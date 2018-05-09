# cny-70
contador de revoluciones


boolean estado = false;
int ledPin1 = 3; // pin de un LED
int ledPin2 = 0; // pin de otro LED
int infraPin = 2; // pin del infrarrojos utilizado como entrada digital
int valorInfra = 0; // Valor inicial de la lectura digital del infrarrojos.
int counter = 0;

int temp = 0;
int tiempo = 0;
int dif = 0;
int rpm = 0;
void setup() {
Serial.begin(9600);
pinMode(ledPin1, OUTPUT); // Inicializa el pin del LED1 como salida digital
pinMode(ledPin2, OUTPUT); // Inicializa el pin del LED2 como salida digital
pinMode(infraPin, INPUT); // Inicializa el pin 4 como entrada digital
}

void loop() {

if(digitalRead(infraPin))
{

if(digitalRead(2) == 1)
{
// valorInfra = true;
valorInfra = digitalRead(infraPin); // Lee el valor de la entrada 4, esto es, el valor que lee el infrarrojo
digitalWrite(ledPin1, valorInfra); // Escribe en el pin 8 el valor que lee la entrada 4, esto es, el mismo valor que lee el infrarrojo
//Si el infrarrojo lee 0, entonces, el LED estará apagado
//Si el infrarrojo lee 1, entonces, el LED estará encendido */
counter++;
delay(500);

Serial.println(counter);

}

}
else
{
estado = false;
valorInfra = digitalRead(infraPin); // Lee el valor de la entrada 4, esto es, el valor que lee el infrarrojo
digitalWrite(ledPin1, valorInfra); // Escribe en el pin 8 el valor que lee la entrada 4, esto es, el mismo valor que lee el infrarrojo
//Si el infrarrojo lee 0, entonces, el LED estará apagado
//Si el infrarrojo lee 1, entonces, el LED estará encendido */
}
if (counter == 1){
temp = millis();
}
tiempo=millis();
dif = (tiempo - temp);
if (dif > 15000)
{
rpm = 4*counter;

Serial.print("la velocidad en rpm es ");
Serial.println(counter);
tiempo = 0;
temp = 0;
dif = 0;
rpm = 0;
counter = 0;
}

}
