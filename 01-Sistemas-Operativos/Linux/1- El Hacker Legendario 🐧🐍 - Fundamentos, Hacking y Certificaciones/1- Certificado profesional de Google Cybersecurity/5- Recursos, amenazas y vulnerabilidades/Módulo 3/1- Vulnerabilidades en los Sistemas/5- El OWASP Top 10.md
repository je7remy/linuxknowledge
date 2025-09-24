
Para prepararse ante futuros riesgos, los profesionales de la Seguridad deben mantenerse informados. Anteriormente, conoció la **Lista** de vulnerabilidades y exposiciones **comunes (CVE®**), un diccionario de vulnerabilidades y exposiciones comunes de libre acceso. La Lista de CVE® es una importante fuente de información que la comunidad mundial de seguridad utiliza para compartir información entre sí.

En esta lectura, conocerá otro recurso importante al que hacen referencia los profesionales de la seguridad, el Proyecto Abierto de Seguridad en Aplicaciones Web, rebautizado recientemente como Open Worldwide Application Security Proyecto® (OWASP). Conocerá la Función del OWASP en la comunidad mundial de la Seguridad y cómo las empresas utilizan este recurso para centrar sus esfuerzos.

## ¿Qué es OWASP?

OWASP es una fundación sin ánimo de lucro que trabaja para mejorar la Seguridad del software. OWASP es una plataforma abierta que los profesionales de la seguridad de todo el mundo utilizan para compartir información, herramientas y eventos centrados en la seguridad de la Web.

## El OWASP Top 10

Uno de los recursos más valiosos de OWASP es el OWASP Top 10. La organización lleva publicando esta lista desde 2003 como una forma de dar a conocer las vulnerabilidades más específicas de la Web. El Top 10 se aplica principalmente a software nuevo o hecho a medida. Muchas de las organizaciones más grandes del mundo hacen referencia al OWASP Top 10 durante el desarrollo de aplicaciones para ayudar a garantizar que sus programas abordan los errores de Seguridad más comunes.

**Consejo profesional:** El OWASP Top 10 se actualiza cada pocos años a medida que evolucionan las tecnologías. La Clasificación se basa en la frecuencia con la que se descubren las vulnerabilidades y el nivel de Riesgo que presentan.

**Nota:** Los auditores también utilizan el OWASP Top 10 como punto de referencia cuando comprueban el cumplimiento de la normativa.

## Vulnerabilidades comunes

Las empresas suelen tomar decisiones críticas en materia de Seguridad basándose en las vulnerabilidades que figuran en el OWASP Top 10. Este recurso influye en la forma en que las empresas diseñan el nuevo software que estará en su red, a diferencia de la Lista de CVE®, que les ayuda a identificar mejoras en los programas existentes. Estas son las vulnerabilidades que aparecen con más regularidad en su Clasificación para conocerlas:

### **Control de acceso roto**

Controles de acceso limitan lo que los usuarios pueden hacer en una aplicación web. Por ejemplo, un Blog puede permitir a los visitantes enviar comentarios sobre un artículo reciente, pero les restringe la posibilidad de borrar el artículo por completo. Los fallos en estos mecanismos pueden conducir a la divulgación, modificación o destrucción no autorizada de la Información. También pueden dar a alguien acceso no autorizado a otras aplicaciones empresariales.

### **Fallos criptográficos**

La Información es uno de los recursos más importantes que las empresas necesitan proteger. Las leyes sobre privacidad, como el Reglamento General de Protección de Datos (RGPD), exigen que los datos sensibles se protejan mediante métodos de encriptación eficaces. Pueden producirse vulnerabilidades cuando las empresas no encriptan elementos como la información de identificación personal (PII). Por ejemplo, si una aplicación web utiliza un algoritmo de hash débil, como MD5, corre más riesgo de sufrir una violación de datos.

### **Inyección**

La inyección se produce cuando se inserta código malicioso en una aplicación vulnerable. Aunque la aplicación parece funcionar con normalidad, hace cosas que no estaba previsto que hiciera. Los ataques de inyección pueden proporcionar a los agentes de amenaza una puerta trasera al sistema de Información de una organización. Un objetivo común es el formulario de inicio de sesión de un sitio web. Cuando estos formularios son vulnerables a la inyección, los atacantes pueden insertar código malicioso que les da acceso para modificar o robar las credenciales de los usuarios.

### **Diseño inseguro**

Las aplicaciones deben diseñarse de forma que sean resistentes a los ataques. Cuando no lo están, son mucho más vulnerables a amenazas como los ataques de inyección o las infecciones por software malicioso. El diseño inseguro se refiere a una amplia gama de controles de Seguridad ausentes o mal implementados que deberían haberse programado en una aplicación cuando se estaba desarrollando.

### **Desconfiguración de la seguridad**

Los errores de configuración se producen cuando los ajustes de Seguridad no se establecen o mantienen adecuadamente. Las empresas utilizan una gran variedad de sistemas diferentes interconectados. A menudo se producen errores cuando esos sistemas no se configuran o auditan adecuadamente. Un ejemplo común es cuando las empresas implementan equipos, como un servidor de redes, utilizando configuraciones predeterminadas. Esto puede llevar a las empresas a utilizar configuraciones que no tienen en cuenta los objetivos de Seguridad de la organización.

### **Componentes vulnerables y obsoletos**

Los componentes vulnerables y obsoletos es una categoría que se refiere principalmente al desarrollo de aplicaciones. En lugar de codificarlo todo desde cero, la mayoría de los desarrolladores utilizan bibliotecas de código abierto para completar sus proyectos de forma más rápida y sencilla. Este software de acceso público es mantenido por comunidades de programadores de forma voluntaria. Las aplicaciones que utilizan componentes vulnerables que no han sido mantenidos corren un mayor riesgo de ser explotadas por agentes de amenazas.

### **Fallos de identificación y autenticación**

Identificación es la palabra clave en esta categoría de vulnerabilidad. Cuando las aplicaciones fallan a la hora de reconocer quién debe tener acceso y qué está autorizado a hacer, pueden surgir problemas graves. Por ejemplo, un router Wi-Fi doméstico utiliza normalmente un sencillo formulario de inicio de sesión para mantener a los invitados no deseados fuera de la red. Si esta defensa falla, un atacante puede invadir la privacidad del propietario.

### **Fallos de software e integridad de datos**

Los fallos de integridad del software y de los datos son instancias en las que las actualizaciones o los parches no se revisan adecuadamente antes de implementarlos. Los atacantes podrían explotar estos puntos débiles para distribuir software malicioso. Cuando esto ocurre, puede haber graves efectos posteriores. Es probable que terceros resulten infectados si un único sistema se ve comprometido, un suceso conocido como ataque a la cadena de suministro.

Un ejemplo famoso de ataque a la cadena de suministro es el [ciberataque a SolarWinds (2020)](https://www.gao.gov/blog/solarwinds-cyberattack-demands-significant-federal-and-private-sector-response-infographic), en el que los hackers inyectaron código malicioso en las actualizaciones de software que la empresa distribuyó sin saberlo a sus clientes.

### **Fallos en el registro y el monitoreo de la Seguridad**

En Seguridad, es importante poder registrar y rastrear los eventos. Disponer de un registro A de eventos como los intentos de inicio de sesión de los usuarios es fundamental para encontrar y solucionar problemas. Monitorear y responder ante incidentes es igualmente importante.

### **Falsificación de peticiones del lado del servidor**

Las empresas tienen información pública y privada almacenada en servidores web. Cuando usted utiliza un hipervínculo o pulsa un botón en un sitio web, se envía una solicitud a un servidor que debe validar quién es usted, obtener los datos apropiados y devolvérselos.

![Un pirata informático utiliza el ordenador de su víctima para robar datos de un servidor web.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/DT6Hkom1RcugsbS_BFgoLw_7e1de97a7fdc4e00b7c9b14a0ad5fcf1_Pfjezx6XbwJ_TAJbWmCtLMpwLX4YD2xP4Se2IJeQF4uTD6BtqNXlcpObbGHeJuzWlxr5A3WqWQzZ2K6E6kFLsX3JiI0bxbFtWFjNUCxZTgs7ftpEgVEcI87zvBxN2flvGXs37nW_RJF0QVLY7798FCXB9pAH_uUI3zYLbXOiOpGcdhti00aMTwl7xbMFpg?expiry=1758758400000&hmac=4jEitFm9MPfz5kP5XA4bb0bcpeCXvPN9rVf4xDQPF5Q)

Las falsificaciones de peticiones del lado del servidor (SSRF) se producen cuando los atacantes manipulan las operaciones normales de un servidor para leer o actualizar otros recursos en ese servidor. Son posibles cuando una aplicación en el servidor es vulnerable. La aplicación vulnerable puede transportar código malicioso al servidor anfitrión que obtendrá datos no autorizados.

## Puntos clave

Mantenerse informado y estar al tanto de las últimas tendencias en ciberseguridad puede ser una forma útil de defenderse de los ataques y prepararse para los riesgos futuros en su carrera de seguridad. [El OWASP Top 10](https://owasp.org/www-project-top-ten/) es un recurso útil donde puede obtener más información sobre estas vulnerabilidades.
