
Has explorado mucho sobre los sistemas operativos. Un aspecto más a tener en cuenta es que los sistemas operativos pueden ejecutarse en máquinas virtuales. En esta lectura, aprenderá sobre las máquinas virtuales y el concepto general de virtualización. Explorará cómo funcionan las máquinas virtuales y las ventajas de usarlas.

## ¿Qué es una máquina virtual?

Una **máquina virtual (VM)** es una versión virtual de un equipo físico. Las máquinas virtuales son un ejemplo de virtualización. La virtualización es el proceso de utilizar software para crear representaciones virtuales de varias máquinas físicas. El término "virtual" se refiere a máquinas que no existen físicamente, pero que funcionan como lo hacen porque su software simula hardware físico. Los sistemas virtuales no usan hardware físico dedicado. En su lugar, utilizan versiones definidas por software del hardware físico. Esto significa que una sola máquina virtual tiene una CPU virtual, almacenamiento virtual y otro hardware virtual. Los sistemas virtuales son solo código.

![A dark gray computer with arrows to light gray computers that have “VM” on the screen and are surrounded by dotted lines.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/C0Cpca6gRquuxTow47dD1A_2a73d66bee5c40b78984e532c09994f1_82635VQFzN8LaD6GAv3bNTQs6oACAmxKjdlZebYCGsO10hvIVpxBElK4gbJ-KJvmRBsxvQd3XHXUfUtgWzNhR4Va6ODC5D42owmm2vyiluDeV86UAaL9d-pyaxXnjzgHARaWckVzCqj12dnrOq1Ca4o?expiry=1752883200000&hmac=hOIbp6JLAjX_LyvPVfD3bQRwdc12ZR_1vrHTvI-ZAqg)

Puede ejecutar varias máquinas virtuales con el hardware físico de un solo equipo. Esto implica dividir los recursos del equipo host para compartirlos entre todos los componentes físicos y virtuales. Por ejemplo, **la memoria de acceso aleatorio (RAM)** es un componente de hardware que se utiliza para la memoria a corto plazo. Si un equipo tiene 16 GB de RAM, puede alojar tres máquinas virtuales para que el equipo físico y las máquinas virtuales tengan 4 GB de RAM cada uno. Además, cada una de estas máquinas virtuales tendría su propio sistema operativo y funcionaría de manera similar a una computadora típica.

## Ventajas de las máquinas virtuales

Los profesionales de la seguridad suelen utilizar la virtualización y las máquinas virtuales. La virtualización puede aumentar la seguridad de muchas tareas y también puede aumentar la eficiencia.

### **Seguridad**

Una ventaja es que la virtualización puede proporcionar un entorno aislado, o un espacio aislado, en la máquina host física. Cuando un equipo tiene varias máquinas virtuales, estas máquinas virtuales son "invitados" del equipo. En concreto, se aíslan del equipo host y de otras máquinas virtuales invitadas. Esto proporciona una capa de seguridad, ya que las máquinas virtuales se pueden mantener separadas de los demás sistemas. Por ejemplo, si una máquina virtual individual se infecta con malware, se puede tratar de manera más segura porque está aislada de las otras máquinas. Un profesional de la seguridad también podría colocar intencionadamente malware en una máquina virtual para examinarla en un entorno más seguro.

**Nota:** Aunque el uso de máquinas virtuales es útil cuando se investigan máquinas potencialmente infectadas o se ejecuta malware en un entorno restringido, todavía existen algunos riesgos. Por ejemplo, un programa malicioso puede escapar de la virtualización y acceder a la máquina host. Esta es la razón por la que nunca debe confiar completamente en los sistemas virtualizados.

### **Eficacia**

El uso de máquinas virtuales también puede ser una forma eficaz y cómoda de realizar tareas de seguridad. Puede abrir varias máquinas virtuales a la vez y cambiar fácilmente entre ellas. Esto le permite optimizar las tareas de seguridad, como las pruebas y la exploración de diversas aplicaciones.

Puede comparar la eficiencia de una máquina virtual con la de un autobús urbano. Un solo autobús urbano tiene mucho espacio y es una forma eficiente de transportar a muchas personas simultáneamente. Si los autobuses urbanos no existieran, entonces todos en el autobús tendrían que conducir sus propios autos. Esto utiliza más gasolina, automóviles y otros recursos que viajar en el autobús urbano.

De forma similar a la cantidad de personas que pueden viajar en un autobús, muchas máquinas virtuales se pueden alojar en la misma máquina física. De este modo, no se necesitan máquinas físicas independientes para realizar determinadas tareas.

## Administración de máquinas virtuales

Las máquinas virtuales se pueden administrar con un software llamado hipervisor. Los hipervisores ayudan a los usuarios a administrar múltiples máquinas virtuales y conectar el hardware virtual y físico. Los hipervisores también ayudan a asignar los recursos compartidos de la máquina host física a una o más máquinas virtuales.

Un hipervisor con el que es útil familiarizarse es la máquina virtual basada en kernel (KVM). KVM es un hipervisor de código abierto compatible con la mayoría de las principales distribuciones de Linux. Está integrado en el kernel de Linux, lo que significa que se puede usar para crear máquinas virtuales en cualquier máquina que ejecute un sistema operativo Linux sin la necesidad de software adicional.

## Otras formas de virtualización

Además de las máquinas virtuales, existen otras formas de virtualización. Algunas de estas tecnologías de virtualización no utilizan sistemas operativos. Por ejemplo, se pueden crear varios servidores virtuales a partir de un único servidor físico. También se pueden crear redes virtuales para usar de forma más eficiente el hardware de una red física.

## Conclusiones clave

Las máquinas virtuales son versiones virtuales de computadoras físicas y son un ejemplo de virtualización. La virtualización es una tecnología clave en el sector de la seguridad, y es importante que los analistas de seguridad comprendan los conceptos básicos. El uso de máquinas virtuales tiene muchas ventajas, como el aislamiento de malware y otros riesgos de seguridad. Sin embargo, es importante recordar que sigue existiendo el riesgo de que el software malicioso escape de sus entornos virtualizados.