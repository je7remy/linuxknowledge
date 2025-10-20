
### **INFORME FINAL DE INCIDENTE**

#### **Resumen ejecutivo**

La organización experimentó un incidente de seguridad el 28 de diciembre de 2022, a las 7:20 p.m., PT, durante el cual un individuo pudo obtener acceso no autorizado a la información de identificación personal (PII) y la información financiera de los clientes. Aproximadamente 50,000 registros de clientes se vieron afectados. El impacto financiero del incidente se estima en $100,000 en costos directos y pérdida potencial de ingresos. El incidente ya está cerrado y se ha realizado una investigación exhaustiva.

#### **Cronología**

Aproximadamente a las 3:13 p.m., PT, del 22 de diciembre de 2022, un empleado recibió un correo electrónico de una dirección externa. El remitente del correo electrónico afirmó que había robado con éxito los datos de los clientes. A cambio de no divulgar los datos en foros públicos, el remitente solicitó un pago de $25,000 en criptomonedas. El empleado asumió que el correo electrónico era spam y lo eliminó.

El 28 de diciembre de 2022, el mismo empleado recibió otro correo electrónico del mismo remitente. Este correo electrónico incluía una muestra de los datos robados de los clientes y una demanda de pago aumentada de $50,000.

El mismo día, el empleado notificó al equipo de seguridad, que comenzó su investigación sobre el incidente. Entre el 28 y el 31 de diciembre de 2022, el equipo de seguridad se concentró en determinar cómo se robaron los datos y el alcance del robo.

#### **Investigación**

El equipo de seguridad recibió la alerta y se desplazó al lugar para comenzar la investigación.

La **causa raíz** del incidente se identificó como una vulnerabilidad en la aplicación web de comercio electrónico. Esta vulnerabilidad permitió al atacante realizar un **ataque de navegación forzada** y acceder a los datos de transacciones de los clientes modificando el número de pedido incluido en la cadena de la URL de una página de confirmación de compra. Esta vulnerabilidad permitió al atacante acceder a las páginas de confirmación de compra de los clientes, exponiendo los datos de los clientes, que el atacante luego recopiló y exfiltró.

Después de confirmar la vulnerabilidad de la aplicación web, el equipo de seguridad analizó los registros de acceso de la aplicación web. Los registros indicaron que el atacante accedió a la información de miles de páginas de confirmación de compra.

#### **Respuesta y remediación**

La organización colaboró con el departamento de relaciones públicas para revelar la violación de datos a sus clientes. Además, la organización ofreció servicios gratuitos de protección de identidad a los clientes afectados por el incidente.

Después de que el equipo de seguridad revisó los registros del servidor web asociados, la causa del ataque fue muy clara. Había una única fuente de registro que mostraba un volumen excepcionalmente alto de pedidos de clientes listados secuencialmente.

#### **Recomendaciones**

Para prevenir futuras recurrencias, estamos tomando las siguientes acciones:

● Realizar escaneos rutinarios de vulnerabilidad y pruebas de penetración.

● Implementar los siguientes mecanismos de control de acceso:

○ Implementar listas blancas (allowlisting) para permitir el acceso a un conjunto específico de URL y bloquear automáticamente todas las solicitudes fuera de este rango de URL.

○ Asegurar que solo los usuarios autenticados estén autorizados para acceder al contenido.

---

### **Preguntas**

1. Pregunta 1

¿A qué tipo de Incidente de Seguridad se vio afectada la organización?

- **Robo de datos** ✅
    
- Vishing
    
- Phishing
    
- Software malicioso
    

---

2. Pregunta 2

¿Qué sección del Informe incluye una explicación de la causa raíz del Incidente?

- Recomendaciones
    
- Resumen ejecutivo
    
- **Investigación** ✅
    
- Cronología
    

---

3. Pregunta 3

¿Qué utilizó el atacante para explotar la vulnerabilidad de la aplicación web de Comercio electrónico?

- Error del usuario
    
- **Navegación forzada** ✅
    
- Filtración de datos
    
- Registros del servidor web
    

---

4. Pregunta 4

¿Qué recomendaciones implementó la organización para prevenir futuras repeticiones? Seleccione dos respuestas.

- Pagó la solicitud de pago de 50.000 dólares
    
- **Implementación de mecanismos de Control de acceso** ✅
    
- **Implementado escaneos rutinarios de vulnerabilidad** ✅
    
- Prestó servicios de protección de la identidad a los clientes afectados