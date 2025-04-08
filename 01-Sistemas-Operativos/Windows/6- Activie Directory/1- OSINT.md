
------------

#osint #activeDirectory  

----------
## ¿Hacia dónde miramos?

Nuestra lista de puntos de datos anterior se puede recopilar de muchas maneras diferentes. Hay muchos sitios web y herramientas diferentes que pueden proporcionarnos parte o toda la información anterior que podríamos usar para obtener información vital para nuestra evaluación. En la siguiente tabla se enumeran algunos recursos y ejemplos potenciales que se pueden utilizar.

|**Recurso**|**Ejemplos**|
|---|---|
|`ASN / IP registrars`|[IANA,](https://www.iana.org/) [arin](https://www.arin.net/) para buscar en América, [RIPE](https://www.ripe.net/) para buscar en Europa, [BGP Toolkit](https://bgp.he.net/)|
|`Domain Registrars & DNS`|[Domaintools](https://www.domaintools.com/), [PTRArchive](http://ptrarchive.com/), [ICANN,](https://lookup.icann.org/lookup) solicitudes manuales de registros DNS contra el dominio en cuestión o contra servidores DNS conocidos, como .`8.8.8.8`|
|`Social Media`|Busca en Linkedin, Twitter, Facebook, los principales sitios de redes sociales de tu región, artículos de noticias y cualquier información relevante que puedas encontrar sobre la organización.|
|`Public-Facing Company Websites`|A menudo, el sitio web público de una corporación tendrá información relevante incrustada. Los artículos de noticias, los documentos incrustados y las páginas "Acerca de nosotros" y "Contáctenos" también pueden ser minas de oro.|
|`Cloud & Dev Storage Spaces`|[GitHub](https://github.com/), [buckets de AWS S3 y contenedores de almacenamiento de Azure Blog](https://grayhatwarfare.com/), [búsquedas de Google usando "Dorks"](https://www.exploit-db.com/google-hacking-database)|
|`Breach Data Sources`|[HaveIBeenPwned](https://haveibeenpwned.com/) para determinar si alguna cuenta de correo electrónico corporativo aparece en los datos públicos de filtración, [Dehashed](https://www.dehashed.com/) para buscar correos electrónicos corporativos con contraseñas de texto sin cifrar o hashes que podemos intentar descifrar sin conexión. A continuación, podemos probar estas contraseñas en cualquier portal de inicio de sesión expuesto (Citrix, RDS, OWA, 0365, VPN, VMware Horizon, aplicaciones personalizadas, etc.) que pueda utilizar la autenticación AD.|

**[[2- Tools]]**
**[[5- nmap scripts]]** 
**[[Extraer Metadatos]]**