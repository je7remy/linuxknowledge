
### **Contexto del Escenario**

Eres un analista de nivel uno del centro de operaciones de seguridad (SOC) en una empresa de servicios financieros. Has recibido una alerta de phishing sobre la descarga de un archivo sospechoso en la computadora de un empleado. Tras investigar el hash del archivo adjunto al correo electrónico, se ha verificado que el archivo es malicioso.

Ahora que dispones de esta información, tu tarea es seguir el libro de jugadas (playbook) de tu organización para completar la investigación, documentar tus hallazgos y resolver la alerta de manera adecuada.

### **Materiales de Apoyo**

Para esta tarea, se te proporcionaron dos documentos clave:

1. **Phishing Playbook**: Una guía paso a paso sobre cómo responder a un incidente de phishing. Define los procedimientos desde la recepción de la alerta hasta su cierre o escalada. 
    
2. **Alert Ticket**: Contiene todos los detalles específicos del incidente que debes investigar. 2
    

Aquí están los detalles cruciales del ticket de alerta que debes analizar:

- **Ticket ID**: A-2703 3
    
- **Severidad**: Media 4
    
- **Remitente**: Def Communications `<76tguyhh6tgftrt7tg.su>` 55
    
- **Destinatario**: `<hr@inergy.com>` 6
    
- **Asunto**: Re: Infrastructure Egnieer role 77
    
- **Cuerpo del correo**: El remitente, "Clyde West", expresa interés en un puesto de ingeniero y adjunta su currículum, protegido con la contraseña `paradise10789`. 8888
    
- **Archivo adjunto**: `filename="bfsvc.exe"` 9
    
- **Hash malicioso conocido**: `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` 10
    

---

### **Enunciado de la Actividad (Instrucciones)**

Debes seguir las instrucciones del libro de jugadas para investigar y resolver el ticket de alerta del incidente.

1. **Evaluar la Alerta (Paso 2 del Playbook)**: Analiza todos los detalles del ticket de alerta. 11Examina la severidad, los detalles del remitente, el cuerpo del mensaje y el archivo adjunto para identificar cualquier inconsistencia que sugiera un intento de phishing. 
    
2. **Determinar Contenido Malicioso (Pasos 3.0 y 3.1)**:
    
    - Confirma si el correo electrónico contiene enlaces o archivos adjuntos. 13En este caso, sí lo contiene. 14
        
    - Determina si el archivo adjunto es malicioso. 15El escenario ya te ha confirmado que el hash del archivo es malicioso. 16
        
3. **Decidir la Acción Final (Pasos 3.2 o 4)**:
    
    - Según el libro de jugadas, si has confirmado que el archivo adjunto es malicioso, debes proceder a escalar el ticket. 17
        
    - Si el archivo no fuera malicioso o no hubiera adjuntos, procederías a cerrar el ticket. 18
        
4. **Actualizar el Ticket de Alerta**: Completa la tarea final actualizando el ticket de alerta con tu decisión.
    
    - Cambia el **Estado del ticket** a "Cerrado" o "Escalado".
        
    - En la sección de **Comentarios del ticket**, redacta un resumen claro de los pasos que tomaste y justifica tu decisión. Debes incluir 2-3 razones específicas por las que crees que la alerta debe ser escalada o cerrada.
        

---

### **Respuesta (Solución a la Actividad)**

A continuación se muestra una actualización del ticket de alerta basada en la investigación del incidente de phishing.

---

#### **Ticket de Alerta Actualizado**

|**Ticket ID**|**Mensaje de Alerta**|**Severidad**|**Detalles**|**Estado del Ticket**|
|---|---|---|---|---|
|A-2703|SERVER-MAIL Posible intento de phishing, descarga de malware|Media|El usuario puede haber abierto un correo electrónico malicioso y haber abierto archivos adjuntos o hecho clic en enlaces.|**Escalado**|

---

#### **Comentarios del Ticket**

Tras la investigación, este ticket ha sido **escalado** a un analista de SOC de nivel dos. A continuación, se presenta un resumen de los hallazgos:

El correo electrónico en cuestión contenía un archivo adjunto malicioso y exhibía múltiples indicadores de un intento de phishing. Siguiendo el libro de jugadas de respuesta a incidentes de phishing, se tomó la decisión de escalar el incidente para una investigación más profunda y una remediación.

Las razones para la escalada son las siguientes:

- **Archivo Adjunto Malicioso Confirmado**: El correo electrónico contenía un archivo adjunto, **"bfsvc.exe"**19. El hash SHA256 de este archivo, `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`, fue verificado como malicioso20. Según el paso 3.2 del libro de jugadas, la confirmación de un archivo adjunto malicioso requiere la escalada del ticket. 21
    
- **Detalles del Remitente Sospechosos**: El correo electrónico del remitente, `<76tguyhh6tgftrt7tg.su>`, es una cadena de caracteres aparentemente aleatoria y no coincide con el nombre del remitente "Def Communications" ni con el nombre de la firma, "Clyde West"22222222. Esto es un fuerte indicador de suplantación de identidad.
    
- **Contenido del Correo Electrónico**: El asunto y el cuerpo del correo electrónico contienen errores gramaticales y de ortografía, como "Infrastructure Egnieer role" y "I am writing for to express"23232323. Los correos electrónicos de phishing a menudo contienen este tipo de errores. La solicitud de usar una contraseña, `paradise10789`, para abrir el archivo adjunto es una táctica de ingeniería social para crear una falsa sensación de seguridad. 24