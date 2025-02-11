
----------

#HTTP #WebSecurity #CyberSecurity #Networking #InfoSec #Pentesting #EthicalHacking #Redes #WebDevelopment #URL #DNS #HackTheBox #WebRequests #HTTPFlow #Security #SysAdmin #DevSecOps #WebScraping #NetworkingBasics #HackingÉtico

--------------


Hoy en día, la mayoría de las aplicaciones que utilizamos interactúan constantemente con internet, tanto web como aplicaciones móviles. La mayoría de las comunicaciones por Internet se realizan con solicitudes web a través del protocolo HTTP. [HTTP](https://tools.ietf.org/html/rfc2616) es un protocolo de nivel de aplicación que se utiliza para acceder a los recursos de la World Wide Web. El término significa texto que contiene enlaces a otros recursos y texto que los lectores pueden interpretar fácilmente.`hypertext`

La comunicación HTTP consta de un cliente y un servidor, donde el cliente solicita al servidor un recurso. El servidor procesa las solicitudes y devuelve el recurso solicitado. El puerto predeterminado para la comunicación HTTP es el puerto , aunque se puede cambiar a cualquier otro puerto, dependiendo de la configuración del servidor web. Las mismas solicitudes se utilizan cuando usamos Internet para visitar diferentes sitios web. Introducimos un () como () para llegar al sitio web deseado, como [www.hackthebox.com](http://www.hackthebox.com/).`80``Fully Qualified Domain Name``FQDN``Uniform Resource Locator``URL`

---

## URL

Se accede a los recursos a través de HTTP a través de un , que ofrece muchas más especificaciones que simplemente especificar un sitio web que queremos visitar. Veamos la estructura de una URL: `URL`![url_structure](https://academy.hackthebox.com/storage/modules/35/url_structure.png)

Esto es lo que representa cada componente:

|**Componente**|**Ejemplo**|**Descripción**|
|---|---|---|
|`Scheme`|`http://` `https://`|Se utiliza para identificar el protocolo al que accede el cliente y termina con dos puntos y una barra diagonal doble (`://`)|
|`User Info`|`admin:password@`|Se trata de un componente opcional que contiene las credenciales (separadas por dos puntos) que se utilizan para autenticarse en el host y se separa del host con un signo arroba (`:``@`)|
|`Host`|`inlanefreight.com`|El host indica la ubicación del recurso. Puede ser un nombre de host o una dirección IP|
|`Port`|`:80`|El está separado del por dos puntos (). Si no se especifica ningún puerto, los esquemas se establecen de forma predeterminada en puerto y de forma predeterminada en puerto `Port``Host``:``http``80``https``443`|
|`Path`|`/dashboard.php`|Esto apunta al recurso al que se está accediendo, que puede ser un archivo o una carpeta. Si no se especifica ninguna ruta, el servidor devuelve el índice predeterminado (por ejemplo, ).`index.html`|
|`Query String`|`?login=true`|La cadena de consulta comienza con un signo de interrogación () y consta de un parámetro (por ejemplo, ) y un valor (por ejemplo, ). Se pueden separar varios parámetros con un signo & ().`?``login``true``&`|
|`Fragments`|`#status`|Los fragmentos son procesados por los navegadores del lado del cliente para localizar secciones dentro del recurso principal (por ejemplo, un encabezado o una sección en la página).|

No todos los componentes son necesarios para acceder a un recurso. Los principales campos obligatorios son el esquema y el host, sin los cuales la solicitud no tendría ningún recurso que solicitar.

---

## Flujo HTTP

![HTTP_Flow](https://academy.hackthebox.com/storage/modules/35/HTTP_Flow.png)

El diagrama anterior presenta la anatomía de una solicitud HTTP en un nivel muy alto. La primera vez que un usuario introduce la URL () en el navegador, envía una solicitud a un servidor DNS (Domain Name Resolution) para resolver el dominio y obtener su IP. El servidor DNS busca la dirección IP y la devuelve. Todos los nombres de dominio deben resolverse de esta manera, ya que un servidor no puede comunicarse sin una dirección IP.`inlanefreight.com``inlanefreight.com`

**Nota:** Nuestros navegadores suelen buscar primero los registros en el archivo local, y si el dominio solicitado no existe dentro de él, entonces se pondrían en contacto con otros servidores DNS. Podemos usar el '' para agregar registros manualmente para la resolución de DNS, agregando la IP seguida del nombre de dominio.`/etc/hosts``/etc/hosts`

Una vez que el navegador obtiene la dirección IP vinculada al dominio solicitado, envía una solicitud GET al puerto HTTP predeterminado (por ejemplo, ), solicitando la ruta raíz. A continuación, el servidor web recibe la solicitud y la procesa. De forma predeterminada, los servidores están configurados para devolver un archivo de índice cuando se recibe una solicitud.`80``/``/`

En este caso, el contenido de es leído y devuelto por el servidor web como una respuesta HTTP. La respuesta también contiene el código de estado (por ejemplo, ), que indica que la solicitud se ha procesado correctamente. A continuación, el navegador web procesa el contenido y lo presenta al usuario.`index.html``200 OK``index.html`

**Nota:** Este módulo se centra principalmente en las solicitudes web HTTP. Para obtener más información sobre HTML y aplicaciones web, puede consultar el módulo [Introducción a las aplicaciones web](https://academy.hackthebox.com/module/details/75).



[[Modelo OSI]]
[[Puertos Principales]]
**[[4- Cómo Utilizar CURL con HTTP]]**
**[[5- Cómo Utilizar WGET]]**
**[[3- Securización de Servidores Web Apache – PARTE 1]]**
**[[6- Securización de Servidores Web Apache – Evitar Ataques de Fuzzing Web – PARTE 4]]**

