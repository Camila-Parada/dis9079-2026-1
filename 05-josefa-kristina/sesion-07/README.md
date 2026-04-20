# sesion-07
vamos  a usar un motor servo 

veremos estrategias para promediar datos

se nos entrega como grupo, motor servo, otra protoboar, un potenciómetro, un LDR (fotorresistor) 

del potenciometro se conecta la patita 1 y la 2 o la 2 y la 3 nunca los dos extremos patita de al medio analog in 

LDR reacciona a la luz 

Motor servo: 3 terminales  permite comportamientos extraños según Aarón



como conectar una protoboard

sección de alimentación es opcional usarla 

positivo cable rojo, lo que sea que conectemos que esté a los dos lados


![proto](./imagenes/protoboard.png)

Protoboard por dentro:

![proto por dentro](./imagenes/protopordentro.jpg)

<https://www.tinkercad.com/>

Ejemplo lectura potenciometro
```
// C++ code
//

// arduino lea potenciometro conectado a la entrada A0

int lectura = 0;

//entrada analog in son controlables
  
void setup()
{
  pinMode(LED_BUILTIN, OUTPUT);
  Serial.begin(9600);
}


void loop()
{
  lectura = analogRead(A0);
  Serial.println(lectura);
}             

```

Ejemplo potenciometro con servomotor

```

// ejemplo lectura potenciometro

// queremos que nuestro Arduino
// sea capaz de leer un potenciometro
// conectado a la entrada A0.


#include <Servo.h>


Servo miServo;

int lectura = 0;
int angulo = 0;


void setup()
{
  pinMode(9, OUTPUT);
  Serial.begin(9600);
  // en que patita esta conectado el servo
  // conectemos a patita 9 digital
  miServo.attach(9);
  
}

void loop()
{
  // leer
  lectura = analogRead(A0);
  
  // imprimir en consola
  Serial.println(lectura);
  
  
  // toma el valor de lectura
  // que va originalmente entre 0 y 1023
  // y mapealo al rango 0 a 180
  angulo = map(lectura, 0, 1023, 0, 180);
    
  // pidele por favor al servo
  // que vaya a ese angulo
  miServo.write(angulo);
  
  // servo descansa un poquito
  // 15 milisegundos
  // la vida es dura
  delay(15);
    
}

```

código primero define cosas

cable naranjo señal


lunes 20 abril 2026
