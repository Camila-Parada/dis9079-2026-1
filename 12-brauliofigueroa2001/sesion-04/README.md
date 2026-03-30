# sesion-04

lunes 30 marzo 2026

## primera parte

- tplink es una empresa de routers y modems, todas esas cosas que se conectan a internet

- el router emite una red con el nombre del curso y una clave, crearon una red wifi, pero no tiene internet, solo wifi sin internet

- mateo abrió tplinkwifi.net

- antes se usaba 2.4ghz ahora 5g en general

- existe una lista de clientes "dhcp", de momento aparecen 2 ID, existe un cliente raspidis9079, tiene una dirección mac, un ip asignado y un tiempo de arrendamiento que es cuanto tiempo puedo estar conectado

- todavía no es necesario que usemos muchos computadores con la misma ip, por la complejidad que estamos manejando

- desconectó el router, la red murió, conectó el router y la red vivió

- mateo entró en la terminal y buscó el raspi, se conectó?? no entendí mucho

- tigervnc

- haremos el vlc desde el compu de aarón, esto es para poder revisar en vivo qué ocurre en la raspberry pi sin tocar nada

- se conectaron al escritorio de la raspberry pi, increíble amigos

- cuando mosquitto se prende en el raspberry, aparece como mosquitto.conf, ese era el archivo que estaba en github

- super user do, sudo, significa que todo lo que viene después del super usuario, el computador lo hará

- sudormrf enter, con esto destruyo cualquier computador?? wtf no lo hagan

CÓDIGO EN ARDUINO

- wificlient wificlient; crea una estructura computacional que es capaz de conectarse a wifi

- mqttclient mqfttClient (wifiClient); significa q es una especie de auto que anda sobre este wifi

- const char broker [] = "192.168.0.100"; es la ip de la raspberrypi

- int port = 1883; es el puerto que nos asigna generalmente el computador para comunicaciones mqtt porque los otros puertos del pc hacen otras cosas

- const char topic [], cualquier persona que envía mensajes en mqtt tiene que mandarlo en cierto topic, el que envía y el que recibe deben tener el mismo topic

- mqttClient.setUsernamePassword (mqttID,mqttPass); aquí va la ID y la password

- 
