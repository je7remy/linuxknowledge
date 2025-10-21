
En esta lectura, examinará algunas de las mejores prácticas relacionadas con la gestión de registros, el almacenamiento y la protección. Comprender las mejores prácticas relacionadas con la recopilación y gestión de registros le ayudará a mejorar las búsquedas de registros y a respaldar mejor sus esfuerzos para identificar y resolver los incidentes de Seguridad.

## Registros

Las fuentes de datos, como los dispositivos, generan datos en forma de eventos. Un **registro** A es un registro de los eventos que se producen en los sistemas de una organización. Los registros contienen entradas de registro y cada una de ellas detalla la información correspondiente a un único evento ocurrido en un dispositivo o sistema. Originalmente, los registros tenían como único propósito la solución de problemas tecnológicos comunes. Por ejemplo, los registros de errores proporcionan información sobre por qué se produjo un error inesperado y ayudan a identificar la causa raíz del error para poder solucionarlo. Hoy en día, prácticamente todos los dispositivos informáticos producen algún tipo de registro que proporciona valiosas estadísticas más allá de la solución de problemas.

Los Equipos de Seguridad acceden a los registros desde receptores de registros como las herramientas SIEM que consolidan los registros para proporcionar un repositorio central de datos de registro. Los profesionales de la Seguridad utilizan los registros para realizar **análisis** de **registros**, que es el proceso de examinar los registros para identificar los eventos de Interés. Los registros ayudan a descubrir los detalles que rodean a las 5 W de la investigación de incidentes: _quién_ provocó el incidente, _qué_ ocurrió, _cuándo_ tuvo lugar el incidente, _dónde_ tuvo lugar el incidente y _por qué_ ocurrió el incidente.

### **Tipos de registros**

Dependiendo de la fuente de Datos, se pueden producir diferentes tipos de registros. He aquí una Lista de algunos tipos de registro comunes que las organizaciones deberían registrar:

- **Red**: Los registros de red son generados por dispositivos de red como firewalls, routers o switches.
    
- **Sistema**: Los registros del sistema son generados por sistemas operativos como ChromeOS™, Windows, Linux o macOS®.
    
- **Aplicación**: Los registros de aplicación son generados por aplicaciones de software y contienen información relativa a los eventos que se producen dentro de la aplicación, como una aplicación de smartphone.
    
- **Seguridad**: Los registros de Seguridad son generados por varios dispositivos o sistemas como software antivirus y sistemas de detección de intrusiones. Los registros de Seguridad contienen información relacionada con la seguridad, como el borrado de archivos.
    
- **Autenticación**: Los registros de autenticación se generan cada vez que se produce una autenticación, como un intento de inicio de sesión con éxito en una computadora.
    

### **Detalles de los registros**

Por lo general, los registros contienen la fecha, la hora, la ubicación, la acción y el autor de la misma. He aquí un ejemplo de registro de autenticación:

Login Event [05:45:15] User1 Authenticated successfully

Los registros contienen información y pueden ajustarse para que contengan aún más información. Verbose registro registra información adicional y detallada más allá del registro por defecto. He aquí un ejemplo del mismo registro anterior pero registrado como verboso.

Login Event [2022/11/16 05:45:15.892673] auth_performer.cc:470 User1 Authenticated successfully from device1 (192.168.1.2)

## Gestión de registros

Dado que todos los dispositivos producen registros, puede resultar abrumador para las organizaciones hacer un seguimiento de todos los registros que se generan. Para obtener el máximo valor de sus registros, debe elegir exactamente qué registrar, cómo acceder a ellos fácilmente y mantenerlos seguros mediante la gestión de registros. La **Gestión de** registros es el proceso de recopilación, almacenamiento, análisis y eliminación de los datos de registro.

### **Qué registrar**

El aspecto más importante de la Gestión de registros es elegir qué registrar. Las organizaciones son diferentes y sus requisitos de registro también pueden variar. Es importante considerar qué fuentes de registro tienen más probabilidades de contener la información más útil en función de su Evento de Interés. Esto podría consistir en configurar las fuentes de registro para reducir la cantidad de datos que registran, por ejemplo excluyendo la verbosidad excesiva. Algunos datos, como los números de teléfono, las direcciones de correo electrónico y los nombres, entre otros, constituyen información de identificación personal (PII), que requiere un tratamiento especial y que en algunas jurisdicciones podría no ser posible registrar.

### **El problema del overlogging**

Desde el punto de vista de la Seguridad, puede resultar tentador registrarlo todo. Este es el error más común que cometen las organizaciones. Sólo porque se pueda registrar, no significa que _sea necesario_ registrarlo. Almacenar cantidades excesivas de registros puede tener muchas desventajas con algunas herramientas SIEM. Por ejemplo, el overlogging puede aumentar los costes de almacenamiento y mantenimiento. Además, el overlogging puede aumentar la carga de los sistemas, lo que puede causar problemas de rendimiento y afectar a la usabilidad, dificultando la búsqueda e identificación de eventos importantes.

### **Retención de registros**

Las organizaciones pueden operar en sectores con requisitos normativos. Por ejemplo, algunas Regulaciones requieren que las organizaciones retengan los registros durante periodos de tiempo determinados y las organizaciones pueden implementar prácticas de retención de registros en su política de gestión de registros.

Las organizaciones que operan en las siguientes industrias podrían necesitar modificar su política de gestión de registros para cumplir con los requisitos normativos:

- Industrias del sector público, como la Ley Federal de Modernización de la Seguridad de la Información (FISMA)
    
- Industrias sanitarias, como la Ley de Transferencia y Responsabilidad de los Seguros Médicos de 1996 (HIPAA)
    
- Industrias de servicios financieros, como el Estándar de seguridad de los datos para la industria de tarjetas de pago (PCI DSS), la Ley Gramm-Leach-Bliley (GLBA) y la Ley Sarbanes-Oxley de 2002 (SOX)
    

### **Protección de registros**

Junto con la gestión y la conservación, la protección de los registros es vital para mantener su integridad. No es raro que los actores maliciosos modifiquen los registros en un intento de engañar a los Equipos de Seguridad e incluso de ocultar su actividad.

Almacenar los registros en un servidor de registros centralizado es una forma de mantener la integridad de los registros. Cuando se generan registros, se envían a un servidor dedicado en lugar de almacenarse en una máquina local. Esto hace que sea más difícil para los atacantes acceder a los registros porque existe una barrera entre el atacante y la ubicación del registro.

## Puntos clave

Es importante comprender cómo recopilar, almacenar y proteger adecuadamente los registros porque forman parte integral de las investigaciones de incidentes. Disponer de un plan detallado para la gestión de registros ayuda a mejorar su utilidad y la eficiencia de los recursos.