
## **Resumen de la actividad**

En esta actividad, evaluará los vectores de ataque de una unidad USB. Considerará un escenario de hallazgo de una unidad USB en un aparcamiento tanto desde la perspectiva de un atacante como de un objetivo.

Los USB, o unidades flash, se utilizan habitualmente para almacenar y transportar datos. Sin embargo, algunas características de estos pequeños y cómodos dispositivos también pueden introducir riesgos para la seguridad. Los actores de amenazas utilizan con frecuencia los USB para distribuir software malicioso, dañar otro hardware o incluso hacerse con el control de los dispositivos. El USB baiting es un ataque en el que un actor de amenazas deja estratégicamente una memoria USB con malware para que un empleado la encuentre e instale para infectar una red sin saberlo. Se basa en que los curiosos conecten una memoria USB desconocida que encuentren.

Asegúrese de completar esta actividad antes de continuar. El siguiente punto del curso le proporcionará un ejemplo completado para que lo compare con su propio trabajo.

**Escenario**

Repase el siguiente escenario. A continuación, complete las instrucciones paso a paso.

Usted forma parte del equipo de seguridad del Hospital Retórico y llega al trabajo una mañana. En el suelo del aparcamiento, encuentra una memoria USB con el logotipo del hospital impreso en ella. No hay nadie más cerca que pueda haberlo tirado, así que decide recogerlo por curiosidad.

Lleva la memoria USB a su oficina, donde el equipo tiene instalado un software de virtualización en una estación de trabajo. El software de virtualización se puede utilizar para este mismo propósito porque es una de las únicas formas de investigar con seguridad una memoria USB desconocida. El software funciona ejecutando una instancia simulada del ordenador en la misma estación de trabajo. Esta simulación no está conectada a otros archivos o redes, por lo que la unidad USB no puede afectar a otros sistemas si resulta estar infectada con software malicioso.

**Instrucciones paso a paso**

Siga las instrucciones y responda a la siguiente pregunta para completar la actividad.

**Paso 1: Acceder a la plantilla**  
Para utilizar la plantilla para este elemento del curso, haga clic en el enlace y seleccione Utilizar plantilla.

Enlace a la plantilla:  
Ejercicio USB de aparcamiento

O

Si no dispone de una cuenta de Google, puede descargar la plantilla directamente desde el siguiente archivo adjunto.

Usted crea un entorno virtual y conecta la unidad USB a la estación de trabajo. El contenido del dispositivo parece pertenecer a Jorge Bailey, director de recursos humanos del Hospital Retórico.

Esta captura de pantalla muestra el contenido de esta unidad USB que contiene una mezcla de archivos personales y de trabajo.  
La unidad de Jorge contiene una mezcla de archivos personales y relacionados con el trabajo. Por ejemplo, contiene carpetas que parecen almacenar fotos familiares y de mascotas. También hay una carta de nueva contratación y un horario de turnos de los empleados.

Revise los tipos de información que Jorge tiene almacenados en este dispositivo. A continuación, en la fila Contenido de la plantilla de actividades, escriba de 2 a 3 frases (de 40 a 60 palabras) sobre el tipo de información que hay almacenada en la unidad USB.

**Nota:** Las unidades USB suelen contener una gran variedad de información de identificación personal (IIP). Los atacantes pueden utilizar fácilmente esta información sensible para atacar al propietario de los datos o a otras personas de su entorno.

La unidad flash parece contener una mezcla de archivos personales y relacionados con el trabajo. Considere cómo podría utilizar esta información un atacante si la obtuviera. Además, considere si todo este suceso fue una puesta en escena.

Por ejemplo, un atacante podría haber colocado estos archivos en la unidad USB como distracción. Podrían haber apuntado a Jorge o a alguien que él conoce, esperando que encontraran el dispositivo y lo conectaran a su estación de trabajo. Al hacerlo, el atacante podría establecer una puerta trasera en los sistemas de la empresa mientras el objetivo desprevenido hojeaba los archivos.

En la fila "Mentalidad del atacante " de la plantilla de actividades, escriba de 2 a 3 frases (de 40 a 60 palabras) sobre cómo podría utilizarse esta información contra Jorge o el hospital.

**Consejo profesional:** La Agencia de Ciberseguridad y Seguridad de las Infraestructuras (CISA) ofrece algunos consejos de seguridad sobre cómo actuar con precaución con las unidades USB, como mantener separadas las unidades personales de las de la empresa.

No ha abierto ninguno de los archivos del dispositivo, lo cual es la mejor práctica.

Los atacantes a veces realizan ataques de cebo USB para entregar código malicioso que han elaborado.

Sin embargo, esta unidad USB seguía siendo un riesgo para la seguridad aunque no contuviera código malicioso. Podría haber sido encontrada fácilmente por un atacante que podría haber utilizado su contenido para planear diversos ataques.

Considere algunos de los riesgos asociados a los ataques de cebo USB:

- ¿Qué tipos de software malicioso podrían esconderse en estos dispositivos?
    
- ¿Qué podría haber ocurrido si el dispositivo estuviera infectado y fuera descubierto por otro empleado?
    
- ¿Qué información sensible podría encontrar un actor de amenazas en un dispositivo de este tipo?
    
- ¿Cómo podría utilizarse esa información contra un individuo o una organización?
    

En la fila Análisis de riesgos de la plantilla de actividades, escriba 3 ó 4 frases (de 60 a 80 palabras) que describan los controles técnicos, operativos o de gestión que podrían mitigar los ataques de cebo USB.

---

## **Actividad: Identificar los vectores de ataque de una unidad USB**

|**Sección**|**Respuesta**|
|---|---|
|**Contenido** _Escribe de 2 a 3 frases (40–60 palabras) sobre el tipo de información que hay almacenada en la unidad USB._|La memoria USB contiene una mezcla de archivos personales, como fotos familiares, y archivos laborales, como cartas de contratación y horarios de empleados. Estos documentos incluyen información de identificación personal (PII) y datos sensibles del hospital. Guardar información personal junto con laboral incrementa el riesgo de exposición y facilita el mal uso por parte de terceros.|
|**Mentalidad del atacante** _Escribe de 2 a 3 frases (40–60 palabras) sobre cómo podría utilizarse esta información contra Jorge o el hospital._|Un atacante podría aprovechar los horarios de empleados para planear ataques de phishing o incluso intrusiones físicas en momentos de ausencia. La PII y los datos personales, como fotos o información familiar, podrían usarse para campañas de ingeniería social o extorsión. Esta combinación de datos personales y laborales ofrece múltiples formas de engañar a Jorge o de comprometer al hospital.|
|**Análisis de riesgos** _Escribe de 3 a 4 frases (60–80 palabras) que describan los controles técnicos, operativos o de gestión que podrían mitigar los ataques de cebo USB._|Este tipo de dispositivo podría contener malware como ransomware, troyanos o variantes de BadUSB capaces de comprometer un sistema en segundos. Si otro empleado lo conectara, podría exponer la red o robar información sensible. Los controles de gestión incluyen políticas claras de uso de dispositivos extraíbles y programas de concienciación. Los controles operativos implican escaneos rutinarios y procedimientos seguros en entornos virtuales. Los controles técnicos abarcan desactivar AutoPlay y aplicar soluciones de control de dispositivos para bloquear USB no autorizados.|

---

