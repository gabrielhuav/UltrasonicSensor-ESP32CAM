# Ultrasonic Sensor ESP32CAM MQTT

## Referencias, software y material:

**Para llevar a cabo esta práctica será necesario contar el siguiente material:**

•	Ubuntu 20.04

•	GitHub Desktop en Ubuntu 20.04

•	IDE de Arduino 1.8 o superior.

•	Biblioteca PubSubClient para Arduino IDE.

•	Biblioteca Ultrasonic para Arduino IDE, (Para esta práctica se utilizará la biblioteca Ultrasonic desarrollada por Erick Simoes en su versión 3.0.0).

•	Broker Mosquitto público o funcionando de forma local en el puerto 1883.

•	NodeRed corriendo de forma local en el puerto 1880.

•	Nodos Dashboard para NodeRed.

•	ESP32CAM AI-Thinker.

•	Sensor ultrasónico HC-SR04

•	Cámara OV2640.

•	Programador FTDI con su cable.

**También será necesario contar el siguiente sotfware:**

•	Ubuntu 20.04

•	Ltd, C., & Ubuntu, F. (2004). Ubuntu (Nº de versión 20.04). x86_64,x86,Microsoft Windows. Europa: Desarrollo de software y hardware libres.
https://ubuntu.com/download/desktop

•	GitHub Desktop en Ubuntu 20.04
https://gist.github.com/berkorbay/6feda478a00b0432d13f1fc0a50467f1

•	IDE de Arduino.

Banzi, M., & Cuartielles, D. (2005). Arduino (Nº de versión 1.8 o superior). Windows/Linux/Mac. Italia: Desarrollo de software y hardware libres.
https://www.arduino.cc/en/software

•	Biblioteca PubSubClient para Arduino IDE.

•	Biblioteca Ultrasonic para Arduino IDE, (Para esta práctica se utilizará la biblioteca Ultrasonic desarrollada por Erick Simoes en su versión 3.0.0).

•	Broker Mosquitto público o funcionando de forma local en el puerto 1883.

•	NodeRed corriendo de forma local en el puerto 1880.

•	O'Leary, N., & Conway-Jones, D. (2013). Node-RED (Nº de versión 2.0). Windows/Linux/Mac/Raspbian. Inglaterra: IBM.

https://nodejs.org/en/
pasos para la instalación en ubuntu: https://edgarjayo.wordpress.com/2020/11/14/instalar-y-ejecutar-node-red-en-ubuntu/

## Circuito a realizar:

Las conexiones para realizar el circuito se muestran en el siguiente diagrama:
<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138552535-07d6113d-be4c-4062-944d-cc014cb116c3.png">
</p>
Una vez realizado el esquema de la figura anterior, el circuito debe tener un aspecto similar a las siguientes figuras:
<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138552560-c3ecc15d-2d48-4c4c-8d73-73d9a6e492b5.png">
 <img src="https://user-images.githubusercontent.com/71236850/138552558-7db667ba-1e0d-4730-9be2-0e6bb9e13869.png">
 <img src="https://user-images.githubusercontent.com/71236850/138552562-9282b9a2-2910-4b33-938c-38cd3725688e.png">
</p>

## Codificación y Explicación del Programa:

Para la codificación del programa que nos permite hacer el envío y recepción de datos del sensor ultrasónico con el ESP32CAM a través del protocolo MQTT se deben realizar los siguientes pasos:

1.- Clonar el repositorio:
-	Con ayuda de GitHub Deskpot, clonar el repositorio proporcionado por Código IoT para el Diplomado Internet de las Cosas de Samsung Innovation Campus, a través del siguiente enlace: https://github.com/codigo-iot/UltrasonicSensor-ESP32CAM-MQTT
- Para corroborar que el repositorio se haya clonado de forma adecuada, verificar que la carpeta del proyecto existe, ingresando al directorio seleccionada, como se muestra en la siguiente figura:
<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138552777-2ab38a91-6600-40d7-bd2c-fe1e88cd6f43.png">
</p>

2.- Abrir el proyecto con el IDE de Arduino:
-	Para abrir el programada, ingresar al directorio donde se clono el repositorio, dar clic derecho en el archivo con terminación. INO (Extensión que utilizan los programas de Arduino por defecto) y seleccionar la opción “Abrir con el IDE de Arduino” (como se muestra en la sigueinte figura). También es posible abrir el IDE de Arduino y buscar el directorio donde se clono el repositorio.

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138552852-c6c698a0-6288-423b-9d00-10587a2f01c7.png">
</p>

2.- Analizar y editar el código:
-	En este paso es importante dedicar un tiempo para analizar la codificación del programa. Una vez que se comprende el funcionamiento del programa inicial es necesario hacer algunas adaptaciones para poder implementar el programa con el circuito que diseñamos en la sección **Circuito a realizar** 
-	Las adecuaciones más importantes que debemos tomar en cuenta son las siguientes:
    1.	Modificar el SSID y password de la red a la que se conectará el programa.
    2.	Modificar la dirección IP del Broker MQTT público o privado al que se conectará el programa. 
    4.	Para un bróker local, utilizar el comando ifconfig para obtener la dirección IP publica de la maquina a utilizar 
    5.	Para un bróker público, ingresar la IP del bróker o alternativamente buscar un servicio que proporcione brokers MQTT, por ejemplo, https://www.hivemq.com/. Con el comando nslookup, que es utilizado para saber si el DNS está resolviendo correctamente los nombres y las IPs, podemos obtener la dirección IP numérica del bróker de hivemq
    
<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138552929-d2b97e16-c91a-42a3-acb5-c79fc95ad357.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553036-6aa124f0-b8d6-40a7-b319-a2490bb930b4.png">
</p>


-	|

    6.	Modificar los temas MQTT donde se publicará la información que el sensor ultrasonico emita.
    7.	Modificar los temas MQTT donde el programa recibe información para evitar recibir información no deseada 

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553173-b79da95e-10e3-465a-b49f-8baa1626f326.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553176-eb49fb13-a9fc-4584-bf06-a4bc2de70700.png">
</p>

## Carga del Programa:

Para cargar el del programa que nos permite hacer el envío y recepción de datos del sensor ultrasónico con el ESP32CAM a través del protocolo MQTT en el circuito que se realizó, se deben realizar los siguientes pasos:

1.- Verificar que nuestro circuito se encuentra conectado al dispositivo con el IDE Arduino instalado a través del cable FTDI:

2.- Antes de iniciar la carga del programa, verificar que el ESP32CAM se encuentra en modo programador, para ello, asegurarse de que el circuito tenga conectado un puenteo como el del cable azul, que se ilustra (como se muestra en la seccion **circuito a realizar**). Posteriormente, apretar el botón de Reset del ESP32CAM para reiniciarlo y asegurarse que el reinicio se haya hecho de forma adecuada utilizando el Monitor Serial.

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553259-2bad3ca0-a827-408c-9149-2eb0a0bf9906.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553238-1f956238-d448-437a-8d97-6482080ec981.png">
</p>

3.- Cargar el programa al circuito realizado.

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553297-5351a355-051d-438f-a8b8-00f52b9a12d5.png">
</p>

4.- El programa comenzará a buscar errores, si todo está bien, se compilará y cargará al ESP32CAM 

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553311-21b635cf-681c-4b2b-8dff-4534b85fa2b5.png">
</p>

5.- Una vez que el programa se haya cargado de forma adecuada, desconectar el puente utilizado en el punto 2 (como se muestra en la siguiente figura), de forma que se obtiene un circuito como el de la seccion **Circuito a realizar**. Presionar nuevamente el botón de reset(como se muestra en la figura 20) y verificar el envío y recepción del sensor con bróker mosquitto desde la Terminal de comandos o utilizando un bróker MQTT y un Flow en NodeRed.

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553350-0d012178-2b96-4cb2-872f-477750d885b3.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553358-7d06a9a5-41fd-4754-b546-aefea0333af3.png">
</p>

## Monitoreo MQTT por consola:

- Para observar el funcionamiento del programa cargado al ESP32CAM, se puedes hacer una serie de suscripciones y publicaciones a los temas seleccionados. Para suscribirse al tema en el que se publican los datos generados por el sensor ultrasónico, se ejecuta un comando de la siguiente forma en la terminal de Ubuntu 20.04 (como se muestra en la siguiente figura):

`mosquitto_sub -h 127.0.0.1 -i NombreUsuarioSubscriptor -t nombre/tema/publicar -q 2`

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553409-f2239c70-bcff-4d8f-a8dc-e2757c659178.png">
</p>

donde:
- 127.0.0.1 es la dirección IP del bróker a utilizar
- NombreUsuarioSubscriptor es el nombre de usuario con el que se realiza la suscripción al bróker MQTT.
- nombre/tema/publicar es el tema a suscribirse para recibir la información.

## Programación de nodos para monitoreo en Node-Red

Para realizar la programación de diferentes nodos para monitorear los datos del sensor ultrasónico, es necesario contar con el Software Node-Red instalado, para posteriormente seguir los pasos que se describen a continuación:

1.- Inicializar Node-Red:

2.- Crear un Flow en Node-Red para visualizar la información.

3.- Configurar el nodo “MQTT in” conforme a la información relevante para que el programa funcione adecuadamente.

4.- Crear un nuevo grupo de tabulaciones para los nodos encargados de mostrar la información.

5.- Configurar los nodos restantes para el despliegue de la información.

6.- Finalmente, desplegar el Flow creado.

<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553518-f6bce1d7-f752-41ac-8f88-c163c1427a99.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553517-1753407e-eb81-4bd4-9699-dd31607c626a.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553514-2a57ea99-8e6c-44a6-ab01-3c038d4e638d.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553511-ebb31b7c-a05e-4b43-8d42-a87cb1b7aab1.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553500-0903be97-1239-448a-9fff-c1a683449107.png">
 <img src="https://user-images.githubusercontent.com/71236850/138553499-b954e019-3393-4b1e-b20f-0c3fad66b2e7.png">  
</p>

## Monitoreo en un Navegador WEB.

- El número que desplegado en el indicador Gauge de nuestro flow representa la distancia medida por el sensor ultrasónico en centímetros (CM), tal y como observa en la siguiente figura:
<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553594-aa2d383e-d6da-4b5a-b3b1-5dcf570adb77.png">
</p>

- Para verificar que el número mostrado en el indicador es el correcto, se muestra la información (en la siguiente figura) desplegada desde el Flow creado, comparando que es idéntica a la del monitor serial del IDE de Arduino y en el monitoreo mostrado en la consola al realizar la suscripción al tema donde se publica la información.
<p align="center">
 <img src="https://user-images.githubusercontent.com/71236850/138553602-75ac153f-007e-489c-8421-f3ba684bfdc1.png">  
</p>
