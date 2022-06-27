# Arduino Pro Portenta H7 + Visual Shield Lora

## Introducción 



Hoy en dia, el reconocimiento de imagen es un tema muy importante y uno de los principales centros de desarrollo tecnologico. En esta experiecia se implementara un sistema de Edge Computing utilizando las capacidades de la placa Arduino Portenta H7 Pro junto con el Visual Shield de Lora. Se utilizara la camara del Visual Shield y las capacidades de procesamieto de algoritmos de la placa. Finalmente, se conectaran distintas placas mediante LoRa y asi se lograra el intercambio de datos.

## Objetivos

Comprender como funcionan las conexiones entre dispositivos mediante LoRa y enteder como funciona Machine Learning en el Edge Computing.

## Materiales

- [ ] 1 Placas Arduino Portenta H7 + Visual Shield de LoRa.
- [ ] 1 cables USB A -> USB C o USB C -> USB C.
- [ ] Notebook con puerto USB A o puerto USB C con Arduino IDE.
- [ ] Acceso a una antena RAK o un GateWay cercano.

## Marco Teorico 

**1. Arduino Portenta H7 Pro**

Es una placa arduino que permite correr codigo de alto nivel al mismo tiempo que realiza tareas en tiempo real. Junto con la Visual Shield de Lora es posible conectar varias placas para generar una red de Edge donde se procesen tareas en tiempo real.
- Esquema de distribución de sensores:

![](https://i.imgur.com/a3OAQGy.png)

**2. Visual Shield LoRa**

Es un módulo que se conecta al Arduino, este cuenta con una antena LoRa que permite generar la conexión entre los gateways y los end points. Aparte de esto, cuenta con dos micrófonos direccionales, con esto se puede reconocer desde donde provienen los sonidos en el ambiente y combinar los recursos de ambos para tener una mayor claridad de sonido. Y por último, cuenta con una cámara, que si se tiene en consideración que la placa puede correr algoritmos de machine learning, se puede utilizar esta para reconocimiento de imágenes en tiempo real.

**3. The Things Network**

Es un entorno que provee un set de herramientas para construir aplicaciones IoT, permite el registro de End Devices y de Gateways, permitiendo así ver el tráfico entre estos. Todos estos intercambios se hacen mediante la red LoRa, para la cuál se necesita que los dispositivos operen en el mismo espectro de frecuencia


The Things Network provides a set of open tools and a global, open network to build your next IoT application at low cost, featuring maximum security and ready to scale.

## Procedimiento


### 1. Configurar placa Arduino:

- [ ] Abrir software Arduino IDE.
- [ ] Conectar la placa Arduino al notebook.
- [ ] Dentro del IDE, ir a Herramientas/Placa/Gestor de Tarjetas.
- [ ] Buscar '*portenta h7 m7 core*' y hacer click.
- [ ] Si no aparece la placa, ir a Herramientas/Gestor de Librerías e instalar la librería "Arduino Mbed OS Nano Boards".
- [ ] Ir a Archivo/Ejemplos/Ejemplos para Arduino Portenta h7/STM32H747_System/STM32H747_updateBootloader. Con esto se actualizará la placa.
- [ ] Para confirmar que la placa está bien conectada, *poner instrucciones para blink*.

### 2. Instalar OpenMV:

#### Para Linux (de preferencia Ubuntu 18.04 o mayores):

- [ ] Visitar el siguiente [link](https://openmv.io/pages/download).
- [ ] Descargar el archivo correspondiente a la arquitectura de su computador. Se descargará un archivo .run.
- [ ] Abrir una terminal en la carpeta en que se descargó el archivo .run y ejecute los siguientes comandos:
    ```
    chmod +x openmv-ide-linux-*.run
    ./openmv-ide-linux-*.run
    ```
- [ ] Esto abrirá un instalador. Continuar con la instalación como dice el programa y ejecutar este.

#### Para Windows:
- [ ] Visitar el siguiente [link](https://openmv.io/pages/download).
- [ ] Descargar el archivo para Windows según la arquitectura de tu computador.
- [ ] Se descargará el instalador. Ejecutelo una vez descargado y siga con las instrucciones para completar la instalación.

#### Para MacOS:
- [ ] Visitar el siguiente [link](https://openmv.io/pages/download). 
- [ ] Descargar el archivo correspondiente a la arquitectura de su computador (OSX Snow Leopard). Se descargará un archivo .dmg.
- [ ] Ejecutar el archivo y seguir las instrucciones correspondientes. Una vez instalado, mover el archivo .app a la carpeta de Aplicaciones.
- Además, se necesita instalar dfu-util. Para esto se puede utilizar un administrador de paquetes, MacPorts o HomeBrew. 
- [ ] Para MacPorts, ejecutar los siguientes comandos en una terminal:
    ```
    sudo port install libusb py-pip
    sudo pip install pyusb
    ```
- [ ] Para HomeBrew, ejecutar los siguientes comandos:
    ```
    sudo brew install libusb python
    sudo pip install pyusb
    ```
#### Una vez instalado:
- [ ] Abrir la aplicación.
- [ ] Instalar los drivers que sugiere, estos ayudarán a tener la última versión disponible.
- [ ] Una vez listo, enchufar el arduino al computador con el programa abierto y apretar el botón del arduino dos veces seguidas. Se debería prender una luz verde e ir apagándose y prendiéndose lentamente. 
- [ ] En la pantalla aparecerá la instalación para los drivers de la placa. Aceptar y continuar con los pasos indicados.
- [ ] Una vez listo, probar el sketch que aparece por defecto (helloworld). Deberías poder utilizar la cámara de la placa.

 > Entrega una captura de pantalla con la cámara funcionando.

### 3. Crear aplicación en The Things Network:

APP KEY :4283ABDC82B520CC55E31B899DCD0740
https://www.thethingsindustries.com/docs/gateways/adding-gateways/

install CLI y configurar gateway
https://www.thethingsnetwork.org/docs/gateways/rak7243c/configuring-gateway/
https://www.thethingsindustries.com/docs/gateways/troubleshooting/#my-gateway-wont-connect-what-do-i-do
https://www.thethingsindustries.com/docs/getting-started/cli/installing-cli/

use CLI para agregar dispositivo:
https://www.thethingsindustries.com/docs/devices/adding-devices/

### 4. Crear cuenta en Edge Impulse
- [ ] Visitar el siguiente link: [link](https://www.edgeimpulse.com/)
- [ ] Ir a la sección Get Started.
- [ ] Llenar los campos y crear la cuenta.
- [ ] Elegir un nombre arbitrario para el primer proyecto.



## Ejercicios


### **Drive con el source code:** [link](https://drive.google.com/drive/folders/1VsvzGs3wr8_yAU2W0JcLtkOY3au-AOSW?usp=sharing)

### 1. Detección de movimiento con cámara: CameraMotionDetect

- [ ] En Arduino IDE, abir el ejemplo ubicado en "Files/Examples/Ejemplos para Arduino Portenta H7 Camera/CameraMotionDetect".
- [ ] Una vez abierto el script, se debe apretar en upload, el ícono “⇨” de la esquina superior izquierda
- [ ] Una vez cargado, ir a "Tools/SerialMonitor".
- [ ] Mover la camara. Explicar brevemente que realiza el programa.
> Modificar el parametro de la función *cam.setMotionDetectionThreshold()*, y explicar que sucede con el programa.


### 2. Probando micrófono: SerialPlotter

- [ ] En Arduino IDE, abir el ejemplo ubicado en "Files/Examples/Ejemplos para Arduino Portenta H7/PDM/PDM/SerialPlotter.
- [ ] Una vez abierto el script, se debe apretar en upload, el ícono “⇨” de la esquina superior izquierda.
- [ ] Una vez cargado, ir a "Tools/SerialPlotter". Explicar brevemente que realiza el programa.
- [ ] Cambiar los valores en el script de las variables mencionadas a continuación a:

```
static const char channels = 2;

static const int frequency = 32000;

```
> Explicar que cambia en el programa.

### 3. Reconocimiento Facial: face_detection

- [ ] Abir OpenMV, y luego de instalar el arduino, buscar en "Files/Examples/Arduino/Portenta H7/Face Detection" y abrir el script *face_detection.py*.
- [ ] Una vez abierto el script, correrlo con el botón play de la izquierda inferior. 

> Sacar captura reconociendo una cara.

> ¿ Qué sucede si se aumenta el threshold ?

### 4. Tráfico en Movimiento: blob_detection_traffic

- [ ] Copiar el archivo *Traffic.bin* a la carpeta raiz del arduino.
- [ ] Cargar y correr el script *blob_detection_traffic.py* en OpenMV, que se encuentra en la carpeta entregada. 
- [ ] Indicar que es lo que se aprecia en la imagen, y registrar el output de salida del Serial Terminal.

> Explicar brevemente que realiza el programa.

- [ ] Luego de terminar este ejercicio, borrar el archivo *Traffic.bin* de la carpeta raiz del arduino.

### 5. Detector de Frutas usando Edge Impulse

- [ ] Abrir OpenMV, e iniciar sesion en Edge Impulse. 
- [ ] Crear un nuevo proyecto en Edge Impulse, nombrandolo "fruit-detector".
- [ ] Abrir el proyecto, y dirigirse a la sección Data acquisition, donde luego se debe hacer click en "Let's collect some data", eligiendo la opcion "Upload Data".
- [ ] Luego, abrir la carpeta "Source Code/Ejercicio 5/Fruit Recognition/data", donde se encuentran las carpetas con imagenes de cada fruta. 
- [ ] En Edge Impulse, hacer click en Choose Files, eligiendo todas las imagenes de una fruta, y elegir como label el nombre de la fruta. Luego, apretar click upload, y esperar que se suban las imagenes. Repetir para las demas frutas y la carpeta unknown.
- [ ] Luego de subir todas las imagenes, dirigirse a la seccion "Impulse Design/Create Impulse", y en Image data, cambiar las dimensiones de la imagen a 48x48. Clickear en "Add a Processing Block", eligiendo "Image", y clickear en "Add a Learning Block", seleccionando "Transfer Learning". Finalmente, guardar apretando "Save Impulse".
- [ ] Ir a la sección "Impulse Design/Image", y cambiar el color depth a grayscale, guardandolo apretando en "Save Parameters", y luego en "Generate Features". 
- [ ] Dirigirse a "Impulse Design/Transfer Learning", y cambiar el número de training cycles a 30. Luego, apretar en "Start Training" y esperar a que termine.
- [ ] Una vez terminado, el modelo está listo para ser exportado. Dirigirse a la sección "Deployment", y seleccionar "OpenMV Library". Finalmente, clickear en "Build", descargandose un archivo comprimido con todo lo necesario para correr el modelo.
- [ ] Descomprimir el zip, y copiar los archivos *labels.txt* y *trained.tflite* a la carpeta raíz del arduino.
- [ ] Abrir en OpenMV el script *fruits_classification.py* entregado en la ruta "Source Code/Ejercicio 5/Fruit Recognition/" y ejecutarlo.
> Capturar imagen de cada detección de fruta y de objeto desconocido en cámara, junto a lo mostrado en el serial terminal.

**Disclaimer:** La detección de frutas funciona mejor con la fruta física que con imágenes, donde con imágenes muchas veces confunde objetos.

Una vez terminado el ejercicio, borrar de la carpeta raiz del arduino los archivos *labels.txt* y *trained.tflite*.
### 6. Detector de Taza: Mug or No Mug
- [ ] Se crea un nuevo proyecto en Edge Impulse llamado "mug-nomug", siguiendo los mismos pasos del ejercicio anterior para crear un nuevo modelo, donde existen dos carpetas para cada label: "mug", que corresponde al dataset de la taza, y "nomug", que es el dataset de lo que no es una taza.
- [ ] Luego de creado el proyecto y copiado los archivos *labels.txt* y *trained.tflite* en la carpeta raíz del arduino, abrir en OpenMV el script *mug_nomug.py* entregado en la ruta "Source Code/Ejercicio 5/Fruit Recognition/" y ejecutarlo.
> Capturar imagen de detección de taza y de objeto desconocido en cámara, junto a lo mostrado en el serial terminal.

- [ ] Modifique el script con el siguiente codigo:
> Esto se incluye al principio del script
```
import pyb
ledRed = pyb.LED(1)   
ledGreen = pyb.LED(2)
```
> Esto luego de calcular max_idx:
```
if max_idx == 0:    
    ledRed.off()
    ledGreen.on()
else:               
    ledRed.on()
    ledGreen.off()
```

>Explicar que sucede ahora con el programa.

Una vez terminado el ejercicio, borrar de la carpeta raiz del arduino los archivos *labels.txt* y *trained.tflite*.

APP_ID="portenta-1" 
DEVICE_ID="dev1"
FREQUENCY_PLAN="US_902_928"
DEV_EUI="a8610a3335376706"
APP_EUI="800000000000000C"
APP_KEY="752BAEC23EAE7964AF27C325F4C23C9A"