# Deteccion-de-objetos-con-TensorFlow
Aplicación realizada para la detección de objetos a través de la web cam con una red previamente entrenada de TensorFlow y el dataset COCO.
## Requerimientos
```
TensorFlow 1.15
lxml 4.6.2
Pillow 8.1.0
Matplotlib 3.3.3
Jupyter 1.0.0
Cython 0.29.21
tf_slim 1.1.0
Anaconda
Python 3.7 32 bits
```
## Instalación y ejecución
Todo el proceso se realiza en el sistema operativo windows 10.
* Clonamos el repositorio oficial de Tensorflow en el directorio que queramos
```
git clone https://github.com/tensorflow/models.git
```
* Descargamos e instalamos conda desde la [Pagina oficial](https://docs.anaconda.com/anaconda/install/windows/) 
* Creamos un ambiente con el nombre que queramos con el comando:
```
conda create -n [nombre_de_ambiente] python=3.7
```
* Activamos el ambiente de conda
```
conda activate [nombre_del_ambiente]
```
* Instalamos las librerias necesarias
```
pip install TensorFlow==1.15 lxml pillow matplotlib jupyter contextlib2 cython tf_slim
```
* Nos movemos a al directorio donde clonamos el repositorio de TensorFlow y nos ubicamos en la ruta _../models/research/_
* Descargamos la versión protoc-3.14.0-win32 del [directorio de versiones](https://github.com/protocolbuffers/protobuf/releases) en github.
Extraemos y movemos el ejecutable ubicado en _../protoc-3.14.0-win32/bin/_ al directorio _../models/research/_
* Compilamos el protoc en la consola de conda con el siguiente comando 
```
protoc object_detection/protos/*.proto --python_out=.
```
* Vamos a construir e instalar el archivo setup.py con los siguientes comandos
```
python setup.py build
python setup.py build
```
* Instalamos pycocotools
```
pip install pycocotools
```
*Instalamos la versión de opencv que sea compatible con nuestra versión de python, en este proyecto se utilizó el binario _opencv_python-4.4.0-cp37-cp37m-win_amd64.whl_ .
Nos ubicamos en la carpeta donde se haya descargado y lo instalamos con el siguiente comando:
```
pip install opencv_python-4.4.0-cp37-cp37m-win_amd64.whl
```
* Regresamos a la ruta _../models/research/object_detection/_
* Ejecutamos jupyter notebook
```
jupyter notebook 
```
* Descargamos el archivo obj_detection_web_cam.ipynb y lo ubicamos en la ruta _../models/research/object_detection/_
* Abrimos el archivo anterior desde el gestor de archivos de jupyter y lo ejecutamos, ya sea celda por celda o con la acción _Cell -> Run All_
## Troubleshooting
Se pueden presentar los siguientes problemas: 
### Error Python 3 Microsoft Visual C++ 14.0 is required
Debemos descargar la [herramienta de compilacion de visual studio](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16). Instalamos y nos vamos a "Herramientas de trabajo", seleccionamos "Herramientas de compilación de c++" y a la derecha seleccionamos únicamente las opciones:
* Windos 10 SDK (version que se tenga del sistema, puede consultarse en el regedit)
* MSVC v141 - VS 2017 C++ Build Tools para x64/x86
* MSVC v140 - VS 2015 C++ Build Tools (v14.00)
Se instalarán algunos gb de actualización, esperamos a que esto suceda y volvemos a intentar ejecutar el comando donde nos hayamos quedado, puede que este paso no sea suficiente por lo cual seguimos la explicación del siguiente problema. 
### LNK1158 cannot run 'rc.exe'
* Copiamos los archivos
```
rc.exe
rcdll.dll
```
* De
```
C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86
```
* A
```
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin
```
### Problema de OpenCv
Es importante recordar que si ejecutamos el ejemplo por default de tensorflow nos actualizará la libreria a la versión 2 y estó dará errores para evitarlos se debe
desinstalar la version actual con pip e instalar nuevamente la versión 1.5. 
---
