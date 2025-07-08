
Anteriormente en este curso, se le presentaron los conceptos del Modelo de responsabilidad compartida y la Gestión de identidad y acceso (IAM). Al igual que las redes locales, las redes en la nube también deben protegerse mediante una combinación de prácticas de refuerzo de la seguridad y criptografía.

Esta lectura abordará las prácticas comunes de endurecimiento de la seguridad de la nube, lo que hay que tener en cuenta a la hora de implementar medidas de seguridad en la nube y los fundamentos de la criptografía. Dado que las infraestructuras en la nube son cada vez más comunes, es importante comprender cómo funcionan las redes en la nube y cómo protegerlas.

## Endurecimiento de seguridad de la nube

Existen varias técnicas y herramientas que pueden utilizarse para proteger la infraestructura y los recursos de las redes en nube. Algunas técnicas comunes de endurecimiento de la Seguridad de la nube incluyen la incorporación de IAM, hipervisores, líneas de base, criptografía y borrado criptográfico.

### Gestión del acceso a la identidad (IAM)

La gestión del acceso a la identidad (**IAM** ) es un conjunto de procesos y tecnologías que ayuda a las organizaciones a gestionar las identidades digitales en su entorno. Este servicio también autoriza la forma en que los usuarios pueden aprovechar los diferentes Recursos de la Nube.

### Hipervisores

Un **hipervisor** abstrae el hardware del host del entorno del software operativo. Existen dos tipos de hipervisores. Los hipervisores de tipo uno se ejecutan en el hardware de la computadora anfitriona. Un ejemplo de hipervisor de tipo uno es ESXi de VMware®. Los hipervisores de tipo dos funcionan en el software de la computadora host. Un ejemplo de hipervisor de tipo dos es VirtualBox. Los proveedores de servicios en la nube (CSP) suelen utilizar hipervisores de tipo uno. Los CSP son responsables de gestionar el hipervisor y otros componentes de virtualización. El CSP se asegura de que los recursos y los entornos de la nube estén disponibles y proporciona parches y actualizaciones con regularidad. Las vulnerabilidades en los hipervisores o los errores de configuración pueden provocar escapes de máquinas virtuales (VM escapes). Un escape de VM es un exploit en el que un actor malicioso obtiene acceso al hipervisor principal, potencialmente a la computadora host y a otras VM. Como cliente de un CSP, rara vez tratará con hipervisores directamente.

### Línea de base

La línea de base para las redes y operaciones en la nube cubre cómo se configura y establece el entorno de la nube. Una línea de base es un punto de referencia fijo. Este punto de referencia puede utilizarse para comparar los cambios realizados en un entorno de nube. Una configuración y puesta a punto adecuadas pueden mejorar en gran medida la seguridad y el rendimiento de un entorno de nube. Algunos ejemplos de establecimiento de una línea de base en un entorno de nube son: restringir el acceso al portal de administración del entorno de nube, habilitar la gestión de contraseñas, habilitar la encriptación de archivos y habilitar los servicios de detección de amenazas para las bases de datos SQL.

## Criptografía en la nube

La criptografía puede aplicarse para asegurar los Datos que se procesan y almacenan en un entorno de nube. La criptografía utiliza sistemas de encriptación y de gestión segura de claves para proporcionar integridad y confidencialidad a los datos. La encriptación criptográfica es una de las formas clave de asegurar los Datos sensibles y la Información en la nube.

La encriptación es el proceso de convertir la información en texto cifrado, que no es legible para nadie sin la clave de encriptación. La encriptación se originó principalmente a partir de la codificación manual de mensajes e Información utilizando un algoritmo para convertir cualquier letra o número dado en un nuevo valor. La encriptación moderna se basa en el secreto de una clave, más que en el secreto de un algoritmo. La criptografía es una herramienta importante que ayuda a proteger las redes en la nube y los Datos en reposo para evitar accesos no autorizados. Aprenderá más sobre criptografía en profundidad en un próximo curso.

## Borrado criptográfico

El borrado criptográfico es un método para borrar la clave de encriptación de los Datos encriptados. Cuando se destruyen Datos en la Nube, los métodos más tradicionales de destrucción de Datos no son tan eficaces. El borrado criptográfico es una técnica más reciente en la que se destruyen las claves criptográficas utilizadas para la desencriptación de los Datos. Esto hace que los Datos sean indescifrables e impide que nadie pueda desencriptarlos. Al cripto-triturar, todas las copias de la clave deben ser destruidas para que nadie tenga la oportunidad de acceder a los Datos en el futuro.

## Gestión de claves

La encriptación moderna se basa en mantener seguras las claves de encriptación. A continuación se indican las medidas que puede tomar para proteger aún más sus Datos cuando utilice aplicaciones en la nube:

- Módulo de plataforma de confianza (TPM). El TPM es un chip de computadora que puede almacenar de forma segura contraseñas, certificados y claves de encriptación.
    
- Módulo de seguridad de hardware de la nube (CloudHSM). El CloudHSM es un dispositivo informático que proporciona almacenamiento seguro para claves criptográficas y procesa operaciones criptográficas, como la encriptación y la desencriptación.
    

Las organizaciones y los clientes no tienen acceso al proveedor de servicios en la nube (CSP) directamente, pero pueden solicitar auditorías e informes de seguridad poniéndose en contacto con el CSP. Los clientes no suelen tener acceso a las claves de encriptación específicas que los CSP utilizan para encriptar los Datos de los clientes. Sin embargo, casi todos los CSP permiten a los clientes proporcionar sus propias claves de encriptación, dependiendo del servicio al que acceda el cliente. A su vez, el cliente es responsable de sus claves de encriptación y de garantizar la confidencialidad de las mismas. El CSP está limitado en cuanto a cómo puede ayudar al cliente si las claves de éste se ven comprometidas o destruidas. Una ventaja clave del Modelo de responsabilidad compartida es que el cliente no es totalmente responsable del mantenimiento de la infraestructura criptográfica. Las organizaciones pueden evaluar y supervisar el riesgo que implica permitir que el CSP gestione la infraestructura revisando la auditoría y los Controles de seguridad de un CSP. Para los contratistas federales, FEDRAMP proporciona una Lista de CSP verificados.

## Puntos clave

Endurecimiento de seguridad de la nube es un componente crítico a considerar al evaluar la seguridad de varios entornos de nube pública y mejorar la seguridad dentro de su organización. La gestión del acceso a la identidad (IAM), la correcta configuración de una línea de base para el entorno de la nube, la seguridad de los hipervisores, la criptografía y el borrado criptográfico son métodos que se pueden utilizar para aumentar la seguridad de la infraestructura de la nube.