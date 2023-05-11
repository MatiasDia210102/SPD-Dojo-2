# SPD-Dojo-2
## Integrantes
- Mateo Ciotti
- Matias Díaz
- Franco Beltrán

## Proyecto

<img src="https://github.com/MatiasDia210102/SPD-Dojo-2/blob/4f7aef209f6018eeec7a1bf053fafba6ede3da29/Imagenes/Captura.PNG?raw=true" width="800"/>

## Descrpcion
Una vez tocado el boton, el programa pasara por cada "estacion" encendiendo su respectivo led y haciendo sonar el buzzer

## Funcion principal

~~~/*C++ code
  Matias Diaz DIV J TT
  Dojo 2
*/

#define BUZZER 13
#define B 12
#define A 11
#define F 10
#define G 9
#define E 8
#define D 7
#define C 6
#define LEDROJO 5 
#define LEDNARANJA 4
#define LEDNARANJA2 3
#define LEDNARANJA3 2
#define BOTON A0

void preguntar_estado_boton();
void encenderYApagarLed(int led);
void encenderDigito(int estado0, int estado1, int estado2, int estado3, int estado4, int estado5, int estado6);
void sonarBuzzer(int buzzer);
void prenderLedsNiveles(int led, char* mensaje);
void imprimir_mensaje(char* mensaje);

void setup()
{
  for(int i = 2; i <= 13; i++){
    pinMode(i, OUTPUT);
  }
  
  pinMode(BOTON, INPUT_PULLUP);
  Serial.begin(9600);
}

void loop()
{
  //Serial.println(digitalRead(BOTON));
  int estado_boton = digitalRead(BOTON);
  
  if(estado_boton == LOW){
    
    preguntar_estado_boton();
  }
}

void preguntar_estado_boton(){
  
  encenderDigito(LOW, HIGH, HIGH, LOW, LOW, LOW, LOW);
  prenderLedsNiveles(LEDROJO, "Llego a la estacion: Constitucion.");
  delay(1000);

  encenderDigito(HIGH, HIGH, LOW, HIGH, HIGH, LOW, HIGH);
  prenderLedsNiveles(LEDNARANJA, "Llego a la estacion: San Juan.");
  delay(1000);
  
  encenderDigito(HIGH, HIGH, HIGH, HIGH, LOW, LOW, HIGH);
  prenderLedsNiveles(LEDNARANJA2, "Llego a la estacion: Independencia.");
  delay(1000);
  
  encenderDigito(LOW, HIGH, HIGH, LOW, LOW, HIGH, HIGH);
  prenderLedsNiveles(LEDNARANJA3, "Llego a la estacion: Moreno");
  delay(1000);
  encenderDigito(LOW, LOW, LOW, LOW, LOW, LOW, LOW);
}

void encenderDigito(int estado0, int estado1, int estado2, int estado3, int estado4, int estado5, int estado6){
  digitalWrite(A, estado0);
  digitalWrite(B, estado1);
  digitalWrite(C, estado2);
  digitalWrite(D, estado3);
  digitalWrite(E, estado4);
  digitalWrite(F, estado5);
  digitalWrite(G, estado6);
  delay(500);
}

void encenderYApagarLed(int led){
  
  digitalWrite(led, HIGH);
  delay(1000);
  digitalWrite(led, LOW);
}

void sonarBuzzer(int buzzer){
  tone(buzzer, 1000, 200);
}

void prenderLedsNiveles(int led, char* mensaje){
  sonarBuzzer(BUZZER);
  imprimir_mensaje(mensaje);
  encenderYApagarLed(led);
}

void imprimir_mensaje(char* mensaje){
  Serial.println(mensaje);
}
~~~

## Links
-[ThinkerCad](https://www.tinkercad.com/things/7rjLmqkCjsa-ejercicio-trenes/editel?sharecode=rhnHZ1HSNi45kLiAJaHVGWsPdo9eRsRYTNV-S7J5mjs)
