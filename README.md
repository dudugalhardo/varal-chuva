#include <Servo.h>

Servo servoEsquerdo;
Servo servoDireito;

int posicaoInicial = 0;
int posicaoFinal = 90;

void setup() {
  servoEsquerdo.attach(9);   // Pino digital 9
  servoDireito.attach(10);   // Pino digital 10

  // Inicializa os servos na posição recolhida
  servoEsquerdo.write(posicaoInicial);
  servoDireito.write(posicaoInicial);
  delay(1000);
}

void loop() {
  // Estende o varal
  for (int pos = posicaoInicial; pos <= posicaoFinal; pos++) {
    servoEsquerdo.write(pos);
    servoDireito.write(pos);
    delay(15);
  }

  delay(5000); // Mantém estendido por 5 segundos

  // Recolhe o varal
  for (int pos = posicaoFinal; pos >= posicaoInicial; pos--) {
    servoEsquerdo.write(pos);
    servoDireito.write(pos);
    delay(15);
  }

  delay(5000); // Mantém recolhido por 5 segundos
}
