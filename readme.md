# 📝 **README**  

¡Bienvenido(a) al proyecto! Aquí encontrarás la descripción de cada carpeta y archivo clave.  
Sigue leyendo para conocer la estructura y su propósito.  


## ⚠️ **Consideraciones de Ejecución**  

Tener en cuenta que para la **ejecución** del proyecto 🚀 debes:  
1. **Mover** el archivo `ejecucion/main.py` **fuera** de la carpeta 🔀, ya que es el **archivo principal** de ejecución 📂.  
2. **Cambiar** la ruta del archivo `robot1/main_selenium.py` 🔧 y **ejecutar**.  
3. **Verificar** que en la carpeta `robot1` 🤖 se encuentren las siguientes carpetas:  
   - **bloquear** 🔒 → Se genera un archivo `bloqueo.txt` que indica que se está ejecutando el programa.  
   - **csv** 🗃 → Se guarda en un CSV los datos de los archivos procesados.  
   - **descargas** 📥 → Donde se descarga el PDF a procesar.  
   - **listos** ✅ → Se guarda una copia del DF del día cuando ya terminó de procesar.

---

## 🗃️ **DF**  
En esta carpeta se guardan todos los DataFrames que se quieren procesar **desde el 02-05-2023 hasta la fecha actual**.  
La idea es ir procesando y actualizando cada cierto tiempo estos archivos, guardando el df original y tambien el df aplicando ETL para guardar solamente la ultima aparicon de cada empresa. Por ejemplo:  
- `DF/df_completo_02052013.pkl`  
- `DF/df_completo_02052013_etl.pkl`  

---

## 🚀 **Ejecucion**  
Carpeta que contiene el **archivo de ejecución principal** del proyecto.  
- Aquí es donde suele estar el script o el `.py` que inicia la lógica general (la “puerta de entrada” al proyecto).
- Tener encuenta el enrutamiento del archivo ya que se tiene que encontrar afuera de la carpeta `robot1`.

---

## 🗄️ **get_ruts_BD**  
Contiene el **script para obtener datos** de la BBDD según los parámetros que se necesiten.  
- Ejemplo: `get_ruts_BD/get_rut/data_mongo.csv` o funciones para conectarse a Mongo.

---

## 🤖 **robot1**  
Carpeta con el contenido del **bot actualizado**, principal para el procesamiento de los documentos.  
- Aquí pueden existir scripts de automatización, módulos relacionados con **extracción de datos** y lógica de bot.  

---

## 🐍 **script_python**  
Contiene todos los archivos de ejecución que se encargan de distintos **procesamientos**, como:  
- Ordenar DataFrames,  
- Dividir DataFrames,  
- Realizar iteraciones necesarias,  
- Leer ciertos documentos,  
- Generar nuevos DataFrames con documentos necesarios para el procesamiento.  

---

## 🧪 **test_unitario**  
Carpeta que contiene los scripts para **pruebas unitarias**.  
- Sirve para verificar que, al momento de procesar, la **salida contenga los datos esperados**.  
- Ejemplo: `test_unitario/test_main.py` con funciones de test. Ya se tiene un formato de los `output` esperados.

---

## 🔒 **.gitignore**  
Contiene las carpetas o archivos que se **desean ignorar** por Git por ser muy grandes o innecesarios.  
- Ejemplo de entradas:  
  ```gitignore
  __pycache__/
  .vscode/
  /robot1/__pycache__/
  /robot1/.vscode/
  /robot1/bloquear/
  /robot1/csv/
  /robot1/listos/
  /robot1/descargas/
  env/
  ```  
  Esto evita que esos directorios y archivos se suban al repositorio.

---

## 🗒 **.gitattributes**  
Contiene los atributos de Git para tener en cuenta **archivos grandes** a procesar.  
- Ejemplo de configuraciones (usando [Git LFS](https://git-lfs.github.com/)):  
  ```gitattributes
  DF/IteracionE1d.zip filter=lfs diff=lfs merge=lfs -text
  get_ruts_BD/get_rut/data_mongo.csv filter=lfs diff=lfs merge=lfs -text
  ```  
- **Cómo agregar un archivo nuevo de más de 100MB** a Git:  
  1. Instala y habilita Git LFS (una sola vez en tu equipo):  
     ```bash
     git lfs install
     ```  
  2. Indica a Git LFS que rastree el tipo de archivo o la ruta específica:  
     ```bash
     git lfs track "*.zip"
     ```  
     o  
     ```bash
     git lfs track "DF/archivo_grande_2023.parquet"
     ```  
  3. Asegúrate de que en tu `.gitattributes` aparezca la entrada correspondiente:  
     ```gitattributes
     DF/archivo_grande_2023.parquet filter=lfs diff=lfs merge=lfs -text
     ```  
  4. Confirma los cambios y haz `push`:  
     ```bash
     git add .gitattributes DF/archivo_grande_2023.parquet
     git commit -m "Add large file with LFS"
     git push
     ```  

Esta configuración **optimiza** el manejo de archivos grandes, evitando saturar el repositorio.

---

## ♻️ **upgrade**
Carpeta que almacena los **scripts** de actualización (tanto de la BBDD como del código fuente).

-Aquí se registra la lógica de cada actualización implementada, junto con su historial o logs relevantes.
Ejemplo:
-upgrade/2023_07_update_schema.py: Script que agrega nuevas colecciones o tablas.
-upgrade/2023_08_refactor_code.py: Script que ajusta rutas de archivos y actualiza funciones.
Esta carpeta resulta útil para hacer seguimiento de los cambios importantes en el proyecto y poder revertirlos o revisarlos cuando sea necesario.

---

## 📦 **requirements**  
Contiene todos los **requerimientos** de la aplicación para funcionar de forma adecuada.  
- Por ejemplo, si usas Python, podría ser `requirements.txt` con la lista de dependencias.  
- Permite replicar el entorno de ejecución fácilmente usando:
  ```bash
  pip install -r requirements.txt
  ```

---

## 🌐 **Máquinas de Producción y Desarrollo**

### 🖥️ **Nueva de Producción (más RAM)**  
**Dirección:** `ec2-54-233-14-129.sa-east-1.compute.amazonaws.com`  
**Credenciales:** `WMK*kK=?1VWg*wNFpmrXaHzEV2f&fCuo`  
**IP:** `15.228.205.5`  

---

### 🖥️ **Máquina de Desarrollo Pre-Producción E1D**  
**Dirección:** `ec2-18-231-121-78.sa-east-1.compute.amazonaws.com`  
**Credenciales:** `6Us9Fk1V3H=qb6GFg!z1P!Zb9Ax;QEjr`  

---

### 🖥️ **Máquina Número 3 Getnet**  
**Dirección:** `ec2-15-228-15-207.sa-east-1.compute.amazonaws.com`  
**Credenciales:** `WMK*kK=?1VWg*wNFpmrXaHzEV2f&fCuo`  

---

### ▶️ **Comando de ejecución Uvicorn API**  
```bash
uvicorn main:app --host 127.0.0.1 --port 8000
```

---

## 🔒 **Conexión VPN**

### Pasos para redirigir el tráfico

1. **Descargar PuTTY**  
2. **Crear conexión** a máquina Ubuntu encargada de realizar redireccionamiento.  
   - En el campo **"Host Name (or IP address)"**, ingresa la IP pública de tu instancia Ubuntu EC2.  
     > Ejemplo: `172-31-42-128 (NEW 15.228.59.190)`
3. **Configuración de PuTTY**:  
   - Navega a **Connection > SSH > Tunnels**.  
   - En **"Source port"**, ingresa el puerto a redirigir (p.ej. `8080`).  
     > Caso real → port `1080`  
   - Selecciona **"Dynamic"** y haz clic en **"Add"**.  
   - Regresa a la sección **"Session"** y haz clic en **"Open"** para iniciar la conexión.
4. **Agregar credenciales**:  
   - Adjunta el archivo `.pem` o `.ppk` de la clave privada de la máquina Ubuntu en PuTTY (opción **Connection > SSH > Auth**).

---

### 🛠 **Realizar pruebas de conexión**  

- **Desde PuTTY**:  
  ```bash
  nordvpn status
  ```
  Para cambiar la IP de la máquina Ubuntu:  
  ```bash
  nordvpn connect <country>
  ```
  > Ejemplo de países: `cl`, `br`

- **Desde el CMD de Windows**:  
  ```bash
  curl --socks5 localhost:1080 http://ifconfig.me
  ```
  Esto verifica la IP pública que sale a internet a través del túnel SOCKS5.

---

### ✅ **¡Listo!** 

Con estos pasos tienes la referencia para conectarte a las distintas máquinas de producción, desarrollo y pruebas, así como la configuración de redirección de tráfico vía VPN.
Con estos archivos y carpetas, tendrás una visión clara de dónde se encuentran los distintos elementos del proyecto, sus responsabilidades y cómo manejarlos. Si tienes dudas, ¡no olvides revisar la documentación interna de cada carpeta o ponerte en contacto con el equipo!  

¡Gracias por leer! 🏁✨
