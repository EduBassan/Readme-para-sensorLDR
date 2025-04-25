# CP01 Edge Computing & Computer Systems  
## Arduino e LDR da Vinheria — Página Web da Vinheria Agnello

A vinheria tinha como diferencial sua interação com o cliente, oferecendo um serviço personalizado para cada pessoa que frequentava a loja. Entretanto, com a chegada da pandemia, o negócio foi prejudicado pela falta de clientes. Após esse período, o senhor Agnello decidiu investir em uma **plataforma de vendas digital**, permitindo que a loja continuasse funcionando.

---

## 📝 Descrição do Projeto

O armazenamento de vinhos é algo complexo, pois envolve várias exigências, como **luminosidade, temperatura e umidade**. Pensando na exigência da luminosidade, desenvolvemos um **sensor de luz** que alerta quando há **alta incidência luminosa sobre os vinhos**, evitando assim danos à bebida.

---

## 🌞 Problemas com o Excesso de Luz

A iluminação deve ser bem suave. Vinhos preferem ambientes com pouca luz, principalmente os **brancos e espumantes**, mais sensíveis à claridade. A exposição à luz, especialmente à **radiação ultravioleta**, pode alterar os compostos orgânicos do vinho, gerando reações químicas que prejudicam seu sabor e qualidade.

---

##  🧪 Testes e Simulações

O projeto foi simulado no Tinkercad e posteriormente testado em um Arduino UNO físico.

---

## 👨‍💻 Integrantes do Grupo
- Eduardo Santiago Bassan — RM: 561474

- Vitor Fernandes dos Santos — RM: 566275

- Henry Andrade Browne — RM: 562622

- João Victor de Souza Abe — RM: 561446

---

## 🧰 Tecnologias Utilizadas

- Tinkercad

- Arduino IDE

---

## 🎥 Link para o PITCH

- https://youtu.be/DvtJpGpJDKg?si=wgisa_kye4-WV1el

---

## 🔧 Materiais Necessários

- 1 Arduino Uno  
- 1 Buzzer  
- 3 LEDs (cores diferentes)  
- 3 Resistores de 220Ω  
- 1 Resistor de 10kΩ  
- 1 Sensor LDR  
- Jumpers  
- 1 Protoboard  

---

## 🛠️ Como Reproduzir o Projeto

1. Conecte uma perna do **LDR** à linha positiva da protoboard (**VCC**).  
2. A outra perna do LDR deve ser conectada ao pino **A0** do Arduino.  
3. Em paralelo, conecte um **resistor de 10kΩ** entre o A0 e o **GND**.  
4. Conecte os **LEDs** com resistores de 220Ω em série:  
    - Cátodo (perna curta) ao **GND**  
    - Ânodo (perna longa) aos seguintes pinos:  
      - Verde → **pino 10**  
      - Amarelo → **pino 9**  
      - Vermelho → **pino 8**  
5. Conecte o pino positivo do **buzzer** ao **pino 11** do Arduino.  
6. O pino negativo do buzzer vai ao **GND**.

---

## 💻 Código Arduino

```cpp
int LED_VERDE = 10;
int LED_AMARELO = 9;
int LED_VERMELHO = 8;
int BUZZER = 11;

void setup() {
  Serial.begin(9600);
  pinMode(LED_VERDE, OUTPUT);
  pinMode(LED_AMARELO, OUTPUT);
  pinMode(LED_VERMELHO, OUTPUT);
  pinMode(BUZZER, OUTPUT);
}

void loop() {
  int LDR = analogRead(A0);
  Serial.println(LDR);
  delay(500);

  if (LDR < 900) {
    digitalWrite(LED_VERDE, HIGH);
    digitalWrite(LED_AMARELO, LOW);
    digitalWrite(LED_VERMELHO, LOW);
    digitalWrite(BUZZER, LOW); 
  }
  else if (LDR >= 900 && LDR <= 950) {
    digitalWrite(LED_VERDE, LOW);
    digitalWrite(LED_AMARELO, HIGH);
    digitalWrite(LED_VERMELHO, LOW);
    digitalWrite(BUZZER, HIGH);
    delay(3000);
    digitalWrite(BUZZER, LOW);
  }
  else if (LDR > 950) {
    digitalWrite(LED_VERDE, LOW);
    digitalWrite(LED_AMARELO, LOW);
    digitalWrite(LED_VERMELHO, HIGH);
    digitalWrite(BUZZER, HIGH);
    delay(3000);
    digitalWrite(BUZZER, LOW);
  }
}
