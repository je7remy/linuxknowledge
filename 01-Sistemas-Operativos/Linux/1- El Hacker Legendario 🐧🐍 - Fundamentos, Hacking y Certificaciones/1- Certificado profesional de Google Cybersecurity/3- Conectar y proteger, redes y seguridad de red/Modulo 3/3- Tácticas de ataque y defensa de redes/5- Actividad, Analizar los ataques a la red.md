---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Actividad, Analizar los ataques a la red
## Resumen de la actividad

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/_3VcKBLLQ0KgcwEu5ZqTlg_d61b7993fcd840b9b5cf282b6e2075f1_image.png?expiry=1751241600000&hmac=_GhnGnm1n8pF_KvTY-mg7Bshv_ozGOcG9PZzoojolto)

En esta actividad, estudiará un escenario en el que un cliente de la empresa para la que trabaja experimenta un problema de seguridad al acceder al sitio web de la empresa. Identificará la causa probable de la interrupción del servicio. A continuación, explicará cómo se produjo el ataque y el impacto negativo que tuvo en el sitio web.

En este curso, ha aprendido sobre varios ataques de red comunes. Ha aprendido sus nombres, cómo se llevan a cabo y las características de cada ataque desde la perspectiva del objetivo. Comprender cómo afectan los ataques a una red le ayudará a solucionar los problemas de la red de su organización. También le ayudará a tomar medidas para mitigar los daños y proteger una red de futuros ataques. Para repasar los ataques, visite [Identificar: Ataques a la red](https://www.coursera.org/learn/networks-and-network-security/ungradedWidget/8hRdi/identify-network-attacks "plugin for Identify: Network Attacks")

Asegúrese de completar esta actividad antes de continuar. El siguiente punto del curso le proporcionará un ejemplo completado para que lo compare con su propio trabajo.

## Escenario

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/KVIvSDP-QXCARpFc_dG0CA_8d5c190ce99a4a60962bcd5dd17a2bf1_image.png?expiry=1751241600000&hmac=YX4lKXbG8sPPYKXVvAoGmBOYrLapJj53qWUYdeb8jKA)

Revise el siguiente escenario. A continuación, complete las instrucciones paso a paso.

Usted trabaja como analista de seguridad para una agencia de viajes que anuncia ventas y promociones en el sitio web de la empresa. Los empleados de la empresa acceden regularmente a la página web de ventas de la empresa para buscar paquetes vacacionales que puedan gustar a sus clientes.

Una tarde, recibe una alerta automática de su sistema de supervisión que le indica un problema con el servidor web. Intenta visitar la página web de la empresa, pero recibe un mensaje de error de tiempo de espera de conexión en su navegador.

Utiliza un rastreador de paquetes para capturar los paquetes de datos en tránsito hacia y desde el servidor web. Observa un gran número de solicitudes TCP SYN procedentes de una dirección IP desconocida. El servidor web parece estar desbordado por el volumen de tráfico entrante y está perdiendo su capacidad para responder al número anormalmente elevado de peticiones SYN. Usted sospecha que el servidor está siendo atacado por un actor malicioso.

Usted desconecta temporalmente el servidor para que la máquina pueda recuperarse y volver a un estado operativo normal. También configura el cortafuegos de la empresa para que bloquee la dirección IP que estaba enviando el número anormal de peticiones SYN. Sabe que su solución de bloqueo de IP no durará mucho, ya que un atacante puede suplantar otras direcciones IP para burlar este bloqueo. Tiene que alertar rápidamente a su jefe sobre este problema y discutir los pasos a seguir para detener a este atacante y evitar que este problema se repita. Tendrá que estar preparado para contarle a su jefe el tipo de ataque que ha descubierto y cómo estaba afectando al servidor web y a los empleados.

## Instrucciones paso a paso

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/AsyTK1VNRLWQhAL-YmOlwg_b04994b50ba64f8fbb10645f0cea9bf1_image.png?expiry=1751241600000&hmac=o8LovHJ2_-56DCwFEs5svBXZqwcSKL1zRWgAVbSNgXk)

Siga las instrucciones y responda a la pregunta para completar la actividad. 

---

## 🛡️ **Informe de Incidente de Ciberseguridad**

---

### **Sección 1: Identificar el tipo de ataque que pudo haber causado esta interrupción en la red**

Una posible explicación para el mensaje de error de **tiempo de espera de la conexión del sitio web** es:



Los registros muestran que:


Este evento podría ser:



---

### **Sección 2: Explicar cómo el ataque está causando el mal funcionamiento del sitio web**

Cuando los visitantes del sitio web intentan establecer una conexión con el servidor web, ocurre un **protocolo de enlace de tres vías (three-way handshake)** usando el protocolo **TCP**. Explica los tres pasos del handshake:



---

### ¿Qué sucede cuando un actor malicioso envía una gran cantidad de paquetes SYN de forma simultánea?


---

### ¿Qué indican los registros y cómo eso afecta al servidor?



---

Los siguientes materiales de apoyo te ayudarán a completar esta actividad. (5.1, 5.2) Manténgalos abiertos mientras continúa con los siguientes pasos.

Reflexione sobre los tipos de ataques de intrusión en la red que ha conocido hasta ahora en este curso. Como analista de seguridad, identificar el tipo de ataque a la red en función del incidente es el primer paso para gestionar el ataque y prevenir ataques similares en el futuro.

He aquí algunas preguntas a tener en cuenta a la hora de determinar qué tipo de ataque se ha producido:

- ¿Qué entiende actualmente sobre los ataques a la red?
    
- ¿Qué tipo de ataque provocaría probablemente los síntomas descritos en el escenario?
    
- ¿Cuál es la diferencia entre una denegación de servicio (DoS) y una denegación de servicio distribuida (DDoS)?
    
- ¿Por qué el sitio web tarda mucho en cargarse e informa de un error de tiempo de espera de conexión?
    

Revise la lectura de Wireshark del paso 2 e intente identificar patrones en el tráfico de red registrado. Analice los patrones para determinar qué tipo de ataque de red se ha producido. Escriba su análisis en la sección uno de la plantilla de informe de incidentes de ciberseguridad proporcionada.


---


Revise la lectura de Wireshark del paso 2 y, a continuación, escriba su análisis en la sección dos de la plantilla de Informe de Incidentes de Ciberseguridad que se proporciona.

Cuando redacte su informe, hable de los dispositivos y actividades de red implicados en la interrupción. Incluya la siguiente Información en su explicación:

- Describa el ataque. ¿Cuáles son los principales síntomas o características de este tipo específico de ataque?
    
- Explique cómo afectó a la red de la organización. ¿Cómo afecta este ataque específico a la red a la página web y a su funcionamiento?
    
- Describa las posibles consecuencias de este ataque y cómo afecta negativamente a la organización.
    
- _Opcional:_ Sugiera posibles formas de asegurar la red para poder evitar este ataque en el futuro.


---

### **Consejo profesional: Guarde la plantilla**

Puede guardar una copia en blanco de la plantilla que ha utilizado para completar esta actividad para seguir practicando o en sus proyectos profesionales. Estas plantillas le ayudarán a elaborar sus procesos de reflexión y a demostrar su experiencia a posibles empleadores.

## Qué incluir en su respuesta

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/NnDknwA9QO2rLUMtGNP84Q_1217aa8688154ff09e2571f556ad2bf1_q8M1mWxjPTiAA5o2LlmvMTu94GBygn-d6Z36Llzorga5oVjdjsj5kXehyvgou2UZujH9IGOF4c5yg1hrqUEEjwWpsKKk9yR3_Hignnq7HQx9_vu4yWX_Ll2wvVnbMe_AaOBTL-5Al6quSzQ9CpvJi55BUJdCsGUtc8F-qsJLYS2sb5zh6t7wDFt5O1BUbooCj9KZKPnOYQQgA3Qf1MI5zidalL0n4JnjsrP_Pg?expiry=1751241600000&hmac=tBKkxvoDRJYqSQXZ6_gRZnZ-ugChgxmqJ6-mrAcgd1s)

Asegúrese de abordar lo siguiente en su actividad completada:

- El nombre del ataque de intrusión en la red
    
- Una descripción de cómo el ataque afecta negativamente al rendimiento de la red

---

## Navegación

- ⬆️ Carpeta: [[_3- Conectar y proteger, redes y seguridad de red|3- Conectar y proteger, redes y seguridad de red]]
- ⬅️ Anterior: [[4- Identificar, Ataques a la red]]
- ➡️ Siguiente: [[5.1- Registro TCP-HTTP-LOG – Wireshark (Tráfico Web Normal y Ataque SYN Flood)]]
