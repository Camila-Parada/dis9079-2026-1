# sesion-05

lunes 06 abril 2026

Actualización de Arduino R4 y preparación de solemne 1

## Investigación Adafruit IO

Adafruit IO es un servicio en la nube de Adafruit para desarrollar proyectos de Internet de las Cosas (IoT). Permite a los usuarios conectar, monitorizar y controlar dispositivos y sensores IoT en línea sin escribir una sola línea de código.

También ofrece recursos y tutoriales para ayudar a los usuarios a iniciar sus proyectos de IoT. 
Proyectos de IoT: son sistemas que conectan hardware (sensores/actuadores) a internet para monitorear y controlar dispositivos remotamente.

Incluye bibliotecas para lenguajes como CircuitPython, Arduino, Python y otros, lo que facilita la integración de dispositivos. 
https://io.adafruit.com/welcome 


## Investigación: Tutoriales de Adafruit IO

-Qué es Adafruit IO (plataforma IoT para almacenar y compartir datos).

-Cómo crear feeds (canales de datos).

-Cómo conectar hardware (Arduino / ESP) a internet.

-Cómo enviar (publish) y recibir (subscribe) datos.


## Conceptos clave aprendidos

-Feed: espacio donde se guardan datos (ej: contador).

-Publish: enviar datos a la nube.

-Subscribe: recibir datos desde la nube.

-Dashboard: visualización de datos.

-IO_KEY: clave privada de acceso.

-IO_USERNAME: usuario.


## Sirve para:

-Enviar datos de sensores.

-Ej: temperatura, luz, humedad.

-Mandar estados o eventos.

-Ej: “botón presionado”, “LED encendido”.

-Visualizar datos en paneles.

-En Adafruit IO puedes ver gráficos en tiempo real.


## ¿Qué hace el código?

El ejemplo “Publicar” hace:

-Se conecta a tu WiFi.

-Se conecta a Adafruit IO con tu usuario y contraseña. 

-Envía datos a un “feed” (como una variable online).

-Repita el envío cada cierto tiempo.


## Instalación en computador (MacBook Air M4)

Software utilizado:
-Arduino IDE
-Librería Adafruit IO Arduino


## Proceso de instalación
-Abrir Arduino IDE.
-Dirigirse al menú lateral izquierdo, icono de Library Manager (ícono lateral izquierdo).
-Buscar: Adafruit IO Arduino.
-Instalar versión 4.3.4 (abril 2026) o superior.


![Arduino](./imagenes/Libreria arduino.png)

<img width="445" height="386" alt="Libreria arduino" src="https://github.com/user-attachments/assets/d41cf0e5-0742-459a-81c9-512495ffe6f0" />


## Aprendizajes:
-Las librerías no funcionan solas: necesitan dependencias.

-Arduino automatiza la instalación, pero hay que aceptar manualmente.

-La versión de librería puede afectar compatibilidad.


## Creación de cuenta en Adafruit IO

-Ingresar a la pagina: https://io.adafruit.com/welcome

-Crear cuenta gratuita (con correo UDP).

-Iniciar sesión.

-Acceder a credenciales.

Así se ve cuando creas la cuenta y configuraciones:


![cuenta adafruit](./imagenes/iniciosesión.png)


Después de crear la cuenta se ve así el inicio de sesión:

![inicio adafruit](./imagenes/inicioio.png)


## Tener en cuenta por seguridad 

-NO subir claves a GitHub.

-NO compartir públicamente.

-Compartir solo por medios privados.

#define IO_USERNAME "usuario"
#define IO_KEY "clave"

#define WIFI_SSID "wifi"
#define WIFI_PASS "password"

 Este archivo NO debe subirse completo a GitHub.


 ## Configuración del código

El sistema funciona con dos archivos:

-5.1 Archivo principal .ino

## Contiene:

-Conexión a Adafruit IO.

-Envío de datos.

-Lógica del programa.

-5.2 Archivo config.h


## Desarrollo Proyecto solemne 01: En clases

Objetivo: Que los objetos "hablen" entre sí sin cables.

La idea es crear un puente invisible entre un aparato físico (Arduino r4 wifi) y un sitio en internet (Adafruit IO). Esto permite que el aparato mande información a la nube o que, desde un computador, le digas al aparato qué hacer, sin importar qué tan lejos estés.

## ¿Cómo funciona? 

-Arduino (emisor): Es el "cerebro" que está en tu escritorio. Recoge datos y los traduce a un lenguaje que viaja por el aire.

-Wifi (mensajero): Es el túnel invisible que saca la información y la sube a internet.

-Adafruit IO (la central): Es como un panel de control en la web donde llegan todos los datos. Ahí se guardan, se ordenan y se muestran en una pantalla.


Objetivo: al presionar el botón enviara una señal al código para que diera la señal de 0 o 1 y luego visualizar los datos en  Adafruit IO para ver gráficos en tiempo real.

-0= no presionar el botón.

-1=presionar el boton.


## Elementos clave del código: usamos el wifi de la Vale
Credenciales obligatorias:
#define IO_USERNAME "vxlentiinaa"
#define IO_KEY "xxxx"

-Sin esto, Arduino no puede conectarse

## Función importante:
io.run();
-Mantiene la conexión activa
-Permite recibir datos

## Creación de feed:
AdafruitIO_Feed *nombreFeed = io.feed("grupo01");
-Define el canal de comunicación

## Envío de datos:
nombreFeed->save(contador);
-Envía datos a la nube


##Problemas durante el proceso: 

1.Caracteres extraños en monitor serial

-Aparecían signos de interrogación (???)
-Causa: baudios incorrectos

![problema 1](./imagenes/signosdeinterogaciónarduino.png)


## Solución:

-Código: Serial.begin(115200)

-Monitor serial estaba en 9600

-Se corrigió a 115200

![solucion](./imagenes/audiodeaudio.png)


## 2. El "Botón de Reset" accidental

-Al conectar el pulsador al pin A0, se generó un puente eléctrico que replicó la función del botón de reinicio maestro de la placa. Esto permitió que, al presionar el botón en la protoboard, el Arduino se reiniciara por completo, tal como si hubieras presionado el botón rojo integrado en la placa.

-El cableado o el contacto en la protoboard activó el sistema de Reset. Esto corta la corriente por un milisegundo y obliga al programa a empezar desde cero.

![conexión](./imagenes/conexiones.jpge)

![reset](./imagenes/botóndereinicio.gif)



 Datos visualizados en Adafruit IO
 
![grafico](./imagenes/prueba1grupo01.png)


##Código final funcional (Ya validado en clases)

-Envío de datos cada 3 segundos al presionar botón.

-Contador incremental.

-Conexión estable a Adafruit IO.


##Solución: Reasignación de Pines

-Se movió la conexión del pulsador del pin A0 al Pin 1.

-El conflicto eléctrico desapareció, permitiendo que el botón cumpliera su función real: enviar una señal digital que el Arduino procesa y transmite exitosamente a la nube en Adafruit IO.

![solución](./imagenes/botonfunciona.gif)


Adafruit IO para ver gráficos en tiempo real con los datos enviados.


![grafico 1](./imagenes/prueba2grupo01.png)


![grafico 2](./imagenes/prueba3grupo01.png)


## Reflexión del proceso

Aprendizajes técnicos:

-Diferencia entre hardware, software y firmware.

-Importancia de la configuración de red.

-Uso de plataformas IoT.

-Comunicación entre dispositivos remotos


Aprendizajes prácticos:

-Los errores más comunes son simples (baudios, claves).

-La conexión WiFi es el punto más crítico.

-Separar credenciales en config.h es buena práctica.

-En Adafruit IO, te da la llave para colocar en el código en arduino.

-El delay(3000) evita sobrecargar la plataforma (limitación de escritura).


Siempre hay que colocar esa línea, para que el arduino no olvide el adafruit IO

io.run();

Es para ver lo que manda el otro arduino en adafruit

io.feed();


## Código que si funciona + el config.hes donde se guarda la clave de Adafruit IO y la clave de wifi

// Adafruit IO Publish Example
//
// Adafruit invests time and resources providing this open source code.
// Please support Adafruit and open source hardware by purchasing
// products from Adafruit!
//
// Written by Todd Treece for Adafruit Industries
// Copyright (c) 2016 Adafruit Industries
// Licensed under the MIT license.
//
// All text above must be included in any redistribution.

// ejemplo para enviar / publish
// por montoyamoraga
// para disenoUDP
// basado en
// Adafruit IO Publish Example

// incluir archivo config.h
// hacer las modificaciones de este archivo
// NO subir a github
#include "config.h"

// esta variable entera
// sera un contador que aumenta
// durante el funcionamiento del software
int contador = 0;

// definir una variable que se llame nombreFeed
// que tenga un cierto valor
// mantener las doble comillas, cambiar grupoXX segun tu nombre de grupo
AdafruitIO_Feed *nombreFeed = io.feed("grupo01");

void setup()
{

  // prender la conexion serial
  // ojo con la velocidad de 115200 baud
  // cuando abras el monitor serial debes configurarlo
  // a este numero, porque el standard de fabrica es 9600 baud
  Serial.begin(115200);

  // estas lineas pausan el codigo
  // hasta que prendas el monitor serial
  // la lupita arriba a la derecha en Arduino IDE
  while (!Serial)
    ;

  // imprimir en consola
  Serial.print("conectando a Adafruit IO");

  // conectarse a io.adafruit.com
  io.connect();

  // esperar la conexion
  while (io.status() < AIO_CONNECTED)
  {
    // imprimir un punto cada medio segundo
    // mientras se conecta
    Serial.print(".");
    delay(500);
  }

  // demostrar que logramos conexion
  Serial.println();
  Serial.println(io.statusText());
}

void loop()
{

  // esta linea es necesaria
  // al principio de loop()
  // para mantener la conexion
  // y procesar datos que lleguen
  io.run();

  // enviar el contador a Adafruit IO
  // primero mostrar en monitor serial
  Serial.println("enviando -> " + String(contador));
  // despues enviar a la nube
  nombreFeed->save(contador);

  // incrementar el contador en 1
  contador = contador + 1;

  // Adafruit IO tiene una velocidad limitada
  // de escritura / publishing
  // usamos delay para pausar el codigo 3 segundos
  delay(3000);
}
























