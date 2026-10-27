# alarma-de-movimiento-con-led
# Proyecto: Sistema de Alerta por Proximidad con Arduino

## Integrantes

- Nieto Milagros
- Prinzi Candelaria
- Osler Gonzalo

##  Historia de Usuario

- **Título:** Detección de proximidad y activación de alerta visual.
- **Como:** Usuario del sistema de seguridad.
- **Quiero:** Que el sistema detecte cuando un objeto se acerca mediante un sensor ultrasónico y active un LED.
- **Para:** Recibir una alerta visual cuando un objeto se encuentre demasiado cerca del área monitoreada.

**Criterios de aceptación:**

- El sensor ultrasónico debe medir la distancia entre el sensor y un objeto.
- El Arduino debe procesar la información recibida por el sensor.
- El LED debe encenderse cuando un objeto se encuentre a 35 cm o menos.
- El LED debe apagarse cuando el objeto se aleje a más de 35 cm.
- El sistema debe repetir las mediciones continuamente para detectar nuevos objetos.

---

##  Requerimientos Funcionales

1. **Detección de proximidad:** El sistema debe detectar objetos mediante un sensor ultrasónico conectado a la placa Arduino.
2. **Activación de alerta visual:** El sistema debe encender un LED cuando un objeto se encuentre a 35 cm o menos del sensor.
3. **Desactivación de la alerta:** El LED debe apagarse cuando el objeto se encuentre a más de 35 cm.
4. **Procesamiento de señales:** La placa Arduino debe recibir y procesar las señales enviadas por el sensor ultrasónico para calcular la distancia.
5. **Medición continua:** El sistema debe realizar mediciones repetidas para detectar cambios en la distancia y responder automáticamente.

---

##  Requisitos No Funcionales

1. **Tiempo de respuesta:** El LED debe encenderse rápidamente cuando el sensor detecte un objeto dentro de la distancia establecida.
2. **Estabilidad de conexiones:** Los cables deben estar conectados correctamente para garantizar el funcionamiento del circuito y evitar lecturas incorrectas.
3. **Eficiencia energética:** El circuito debe funcionar con un consumo reducido de energía y alimentarse mediante USB o una fuente compatible de 5 V.
4. **Mantenibilidad del código:** El programa de Arduino debe estar organizado y comentado para facilitar su comprensión y futuras modificaciones.
5. **Confiabilidad:** Los componentes deben funcionar correctamente en condiciones normales de uso y permitir la detección de objetos a diferentes distancias.



##  Código Fuente (Arduino / Wokwi)

```cpp
const int trigPin = 9;
const int echoPin = 10;
const int ledPin = 7;

long duration;
float distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);

  Serial.begin(9600);
}

void loop() {
  // Enviar el pulso ultrasónico
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Medir el tiempo del eco
  duration = pulseIn(echoPin, HIGH, 30000);

  // Calcular la distancia en centímetros
  if (duration == 0) {
    distance = 999;
  } else {
    distance = duration * 0.0343 / 2;
  }

  // Mostrar la distancia en el monitor serie
  Serial.print("Distancia: ");
  Serial.print(distance);
  Serial.println(" cm");

  // Encender el LED a 35 cm o menos
  if (distance <= 35) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }

  delay(100);
}
```

**Conexiones del circuito:**

- Sensor VCC → 5V del Arduino.
- Sensor GND → GND del Arduino.
- Sensor TRIG → pin digital 9.
- Sensor ECHO → pin digital 10.
- LED positivo (+) → pin digital 7, con una resistencia en serie.
- LED negativo (−) → GND del Arduino.
