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

**Conexiones del circuito**

**Alimentación de la protoboard**

* El pin 5V de Arduino Uno se conecta al riel positivo (+) de la protoboard.
* El pin GND de Arduino Uno se conecta al riel negativo (−) de la protoboard.

**Sensor ultrasónico**

* VCC: riel positivo (+) de la protoboard.
* GND: riel negativo (−) de la protoboard.
* TRIG: pin digital 10 de Arduino.
* ECHO: pin digital 9 de Arduino.

**LED**

* Pin digital 3 de Arduino: conectado a una pata del LED mediante una resistencia.
* Otra pata del LED: conectada al riel negativo (−) de la protoboard.

La protoboard permite distribuir la alimentación y organizar las conexiones de los componentes del sistema de detección de proximidad.
