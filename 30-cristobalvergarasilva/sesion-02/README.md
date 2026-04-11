# sesion-02

lunes 16 marzo 2026

> grupo solemne 1: Josefa, Debora, Cristobal


Esta clase pasamos hartos conceptos clave de la programacion

**C++**
es el lenguaje que utiliza arduino, es muy usado y conocido

**void setup() {** 
Esta función se ejecuta una sola vez al inicio del programa. Se utiliza para realizar la configuración inicial del dispositivo,

**void loop() {** 
Esta función se ejecuta de forma cíclica una vez que se ha completado la función setup, se repite continuamente mientras el dispositivo esté encendido

**protocolo mqtt**
MQTT es un protocolo que se utiliza para la comunicación de un equipo a otro. los dispositivos IoT utilizan MQTT para la transmisión de datos, ya que resulta fácil de implementar y puede comunicar datos de manera eficiente. MQTT admite la mensajería entre dispositivos a la nube y la nube al dispositivo, ademas sus mensajes son livianos.

**Mosquitto**
Es un broker de comunicacion de codigo abierto, proporciona un método para enviar mensajes mediante publicación/suscripción

**Subscribir y publicar**
La pestaña publicar lanza un mensaje con un topic, sin tener claro a donde llega y subcribir publica un mensaje y ve en qué dispositivos reciben qué, según a qué topic están suscritos. 

**Topic**
Direccion a la que se envia el mensaje ..../..../....


**Broker**
servidor que recibe todos los mensajes y los reparte a quien corresponde.

"broker es un intermediario, algo que negocia, entonces mosquitto es algo que sin cables genera un broker de mqtt"

-Para conecciones lejanas se necesita dar indicaciones al router.

**router**
conecta una red con internet y  se encarga de que los dispositivos que estem adentro se puedan comunicar entre sí.

**IP**
donde vive tu computador en el internet, es un lugar asi los datos saben donde llegar.

**primera solemne, conectar un arduino y un raspberrypie**
