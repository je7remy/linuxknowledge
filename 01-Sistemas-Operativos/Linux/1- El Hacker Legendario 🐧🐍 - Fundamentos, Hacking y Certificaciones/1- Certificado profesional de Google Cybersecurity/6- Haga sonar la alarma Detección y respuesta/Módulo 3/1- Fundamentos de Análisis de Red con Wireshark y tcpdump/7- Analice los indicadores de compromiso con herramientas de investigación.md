
Hasta ahora, ha aprendido sobre los diferentes tipos de Métodos de Detección que se pueden utilizar para detectar Incidentes de Seguridad. Esta lectura explora cómo pueden utilizarse las herramientas de investigación durante las investigaciones para analizar los **Indicadores de compromiso (IoC** ) sospechosos y crear un contexto en torno a las alertas. Recuerde que un IoC es una prueba observable que sugiere indicios de un posible incidente de Seguridad.

## Añadir contexto a las investigaciones

Ha aprendido sobre la Pirámide del Dolor, que describe la relación entre los indicadores de compromiso y el nivel de dificultad que experimentan los actores maliciosos cuando los indicadores de compromiso son bloqueados por los Equipos de Seguridad. También ha aprendido sobre los diferentes tipos de IoC, pero como ya sabe, no todos los IoC son iguales. Los actores maliciosos pueden ingeniárselas para eludir la detección y seguir comprometiendo los sistemas a pesar de tener bloqueada o limitada su actividad relacionada con los IoC.

Por ejemplo, identificar y bloquear una única dirección IP asociada a una actividad maliciosa no proporciona una estadística más amplia sobre un ataque, ni impide que un actor malicioso continúe con su actividad. Centrarse en una sola prueba es como fijarse en una sola sección de un cuadro: Se pierde la visión de conjunto.

![Una mujer observa una sola sección de un gran cuadro.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/cii_FTSJTp6T9MiUON3QYw_55d2b729f5dc4eac883a774014823de1_umg_H4AHltqDZ8JXSzqzziTdQQhQQ2nidz2cvkE8wZiIG--TeOBj7WiA5pmKthEgHFrySvUi_inxWJXUVjq6TNB-CntB5QPRzlPylsNHvBlZpcvl_g5sDRygyhAjqwSOnTkfTYowlJs1zbxctSDaHcQ?expiry=1760486400000&hmac=mYzX4iR6SmaeSg7keyImeovECgSuzjNfze2AC4DamDE)

Los analistas de Seguridad necesitan una forma de ampliar el uso de los IoC para que puedan añadir contexto a las alertas. La **Inteligencia** sobre amenazas es información basada en pruebas que proporciona contexto sobre las amenazas existentes o emergentes. Al acceder a información adicional relacionada con los IoC, los analistas de seguridad pueden ampliar su punto de vista para observar el panorama general y construir una narrativa que ayude a informar sus acciones de respuesta.

![Una mujer contempla un gran cuadro de un elefante en su totalidad.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/NJZv0wovQSKtj9HDjsy_vw_a51597ca2f20481289849bf159c222e1_wq21GsJyPvGERPn-NTfkl9XOMS4dtFHHIBl60TkZsaXBdXxsMfARzwbEQ9_S3iut7w-W4fIUikrnjtC2UvMIADqN0yxD8tnz4SNtJLbA_zpo_ZrEvDiCuU6kWJ3cAT1hfHGU526P9qhzGl6X02sjgNY?expiry=1760486400000&hmac=rvygaaa4nwzNgcZdyZ1D1fvE8hG9XQsa-DkoLOCC49w)

Al añadir contexto a un IoC -por ejemplo, identificando otros artefactos relacionados con la dirección IP sospechosa, como comunicaciones de red sospechosas o procesos inusuales- los equipos de seguridad pueden empezar a desarrollar una imagen detallada de un incidente de seguridad. Este contexto puede ayudar a los Equipos de Seguridad a detectar más rápidamente los Incidentes de Seguridad y a adoptar un enfoque más informado en su respuesta.

## El poder del Crowdsourcing

El**Crowdsourcing** es la práctica de recopilar información utilizando las aportaciones y la colaboración del público. Las plataformas de Inteligencia sobre amenazas utilizan el crowdsourcing para recopilar información de la comunidad mundial de ciberseguridad. Tradicionalmente, la respuesta de una organización a los incidentes se realizaba de forma aislada. Un Equipo de Seguridad recibía y analizaba una alerta, y luego trabajaba para remediarla sin estadísticas adicionales sobre cómo abordarla. Sin Crowdsourcing, los atacantes pueden realizar los mismos ataques contra varias organizaciones.

![Un atacante ataca con éxito a cinco organizaciones diferentes.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/hRQbqDNHSkWbZJMfxaNsQw_21e96120d16f4940839edd5b7d5454e1_davTkHHUevx1nYpQaSF7v_WTPPgga12ByDGjdKWVjVBG9OU_lTX-SZnh7EPzFgdBcYskWLQDmVMZOEgyBuXhbrSha86C_Xu_XraeZ4oLHmGOJWhoF4Omr3AbMQf1VwiLgDkohnH-VVSPb48HB46dQp8?expiry=1760486400000&hmac=tuUYnz8WcHUI_oHBzaZXPHMjQxd4s96uW8fH459HmZ4)

Con el crowdsourcing, las organizaciones aprovechan los conocimientos de millones de otros profesionales de la ciberseguridad, incluidos proveedores de productos de ciberseguridad, agencias gubernamentales, proveedores de la nube, etc. El crowdsourcing permite a las personas y organizaciones de la comunidad mundial de ciberseguridad compartir abiertamente y acceder a una colección de datos de inteligencia sobre amenazas, lo que ayuda a mejorar continuamente las tecnologías y metodologías de detección.

Entre los ejemplos de organizaciones que comparten información se incluyen los Centros de Análisis e Intercambio de Información (ISAC), que se centran en recopilar y compartir inteligencia sobre amenazas específica del sector con empresas de sectores concretos como la energía, la sanidad y otros. La **Inteligencia de fuentes abiertas (OSINT** ) es la recopilación y el análisis de información procedente de fuentes de acceso público para generar inteligencia utilizable. La OSINT también puede utilizarse como método para recopilar información relacionada con los actores de las amenazas, las amenazas, las vulnerabilidades y mucho más.

Estos datos de inteligencia sobre amenazas se utilizan para mejorar los métodos y técnicas de detección de los productos de seguridad, como las herramientas de detección o el software antivirus. Por ejemplo, los atacantes suelen realizar los mismos ataques contra varios objetivos con la esperanza de que uno de ellos tenga éxito. Una vez que una organización detecta un ataque, puede publicar inmediatamente los detalles del mismo, como archivos maliciosos, direcciones IP o URL, en herramientas como VirusTotal. Esta Inteligencia sobre amenazas puede entonces ayudar a otras organizaciones a defenderse contra el mismo ataque.

![Se impide que un atacante ataque a las organizaciones gracias a la Inteligencia sobre amenazas crowdsourced.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/4nnwqdjMQzmT291E0-hPWA_09adff26a39c40f9aa26ae06cec198e1_ZeTn34K0Nort9Mm0C7fqubtvfqcK_MniMrjOEZoaNou8UKl9Nc-fp48EETQmm6sJk9SvT1TPcTBN8n53R9EoUbx3LvUPg3SJ1GjXead03Pl1tx1y_bQ7Lfurjsu4FQwCwLcQev81ZUm_YLGQ1v4VAFY?expiry=1760486400000&hmac=h-NK6k_s_8zb3jVAKFvTA2afBfgKvDiO9ScuQR8tK60)

## VirusTotal

[**VirusTotal**](https://www.virustotal.com/gui/home) es un servicio que permite a cualquiera analizar archivos, dominios, URL y direcciones IP sospechosos en busca de contenido malicioso. VirusTotal también ofrece servicios y herramientas adicionales para uso empresarial. Esta lectura se centra en el sitio web de VirusTotal, que está disponible para uso gratuito y no comercial.

Puede utilizarse para analizar archivos sospechosos, direcciones IP, dominios y URL para detectar amenazas de ciberseguridad como software malicioso. Los usuarios pueden enviar y comprobar artefactos, como hashes de archivos o direcciones IP, para obtener informes de VirusTotal, que proporcionan información adicional sobre si un IoC se considera malicioso o no, cómo está conectado o relacionado ese IoC con otros IoC del conjunto de datos, y mucho más.

![Una captura de pantalla de la página de inicio de VirusTotal.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/OGF9XULpS4yRE9XWp0_5Ww_28f373819aa5487080f345ee10ed36e1_2UzPkWUVrcbKDLApq0CPB33OaJOORTO260rs4umcRJK6f09s9wrvwlEyczfwmAjHJp34gLdnvhGcz3WYmdSFzV5BRUscBCjBtePStKAA3S_481ILEM_X1AmmoLNi97lkerAtOcFrOuP2K5PT-QGGJ3Q?expiry=1760486400000&hmac=G33E6NZMWYUZednUKQaq0weYlaxjMlskfHqViSdhKy0)

He aquí un desglose del resumen de los informes:

![Captura de pantalla de un resumen de informes de VirusTotal.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/G6lzkoezTH--0Ly1-t-gyA_bf5046e9968f4a33b881b46561b750f1_CS_R-129_VirusTotal-reports.png?expiry=1760486400000&hmac=xkhKSlo4SuT1U9u8XlABp8xIS709mX-hKSTK6y5xE1k)

1. **Detección**: La pestaña Detección proporciona una Lista de Proveedores de Seguridad de terceros y sus veredictos de detección sobre un IoC. Por ejemplo, los Proveedores pueden listar su veredicto de detección como malicioso, sospechoso, inseguro y más.
    
2. **Detalles**: La pestaña Detalles proporciona información adicional extraída de un análisis estático del IoC. Información como diferentes hashes, tipos de archivo, tamaños de archivo, cabeceras, hora de creación e información sobre el primer y último envío pueden encontrarse en esta pestaña.
    
3. **Relaciones**: La pestaña Relaciones proporciona IoCs relacionados que están de alguna manera conectados a un artefacto, como URLs contactadas, dominios, direcciones IP y archivos descartados si el artefacto es un ejecutable.
    
4. **Comportamiento**: La pestaña Comportamiento contiene información relacionada con la actividad y los comportamientos observados de un artefacto tras ejecutarlo en un entorno controlado o sandboxed. Esta información incluye tácticas y técnicas detectadas, comunicaciones de red, acciones de registro y sistemas de archivos, procesos y mucho más.
    
5. **Comunidad:** La pestaña Comunidad es donde los miembros de la comunidad de VirusTotal, como profesionales de la Seguridad o investigadores, pueden dejar comentarios y estadísticas sobre el IoC.
    
6. **Proporción de Proveedores y** puntuación de la comunidad: La puntuación que aparece en la parte superior del Informe es la proporción de Proveedores. El ratio de proveedores muestra cuántos proveedores de Seguridad han marcado el IoC como malicioso en general. Debajo de esta puntuación, se encuentra también la puntuación de la comunidad, basada en las aportaciones de la comunidad de VirusTotal. Cuantas más detecciones tenga un archivo y mayor sea su puntuación de la comunidad, más probable es que el archivo sea malicioso.
    

**Nota**: Los Datos subidos a VirusTotal serán compartidos públicamente con toda la comunidad de VirusTotal. Tenga cuidado con lo que envía y asegúrese de no subir información personal.

## Otras herramientas

Existen otras herramientas de investigación que pueden utilizarse para analizar IoC. Estas herramientas también pueden compartir los datos que se les cargan con la comunidad de seguridad.

### **Escaneo de software malicioso de Jotti**

El análisis de[software malicioso](https://virusscan.jotti.org/) de Jotti es un servicio gratuito que le permite analizar archivos sospechosos con varios programas antivirus. Existen algunas limitaciones en cuanto al número de archivos que puede enviar.

### **Urlscan.io**

[Urlscan](https://urlscan.io/).io es un servicio gratuito que escanea y analiza las URL y proporciona un informe detallado que resume la información de la URL.

### **MalwareBazaar**

[MalwareBazaar](https://bazaar.abuse.ch/browse/) es un repositorio gratuito de muestras de software malicioso. Las muestras de software malicioso son una gran fuente de Inteligencia sobre amenazas que puede utilizarse con fines de investigación.

## Puntos clave

Como analista de Seguridad, analizará los IoC. Es importante comprender cómo añadir contexto a las investigaciones puede ayudar a mejorar las capacidades de detección y a tomar decisiones informadas y eficaces.