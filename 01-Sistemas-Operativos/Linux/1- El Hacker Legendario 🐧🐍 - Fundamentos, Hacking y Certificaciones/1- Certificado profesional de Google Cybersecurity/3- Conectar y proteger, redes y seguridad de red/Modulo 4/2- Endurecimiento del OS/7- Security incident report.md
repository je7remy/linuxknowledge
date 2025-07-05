
**Sección 1: Identificar el protocolo de red involucrado en el incidente**  
El protocolo implicado en el incidente es el **Protocolo de Transferencia de Hipertexto (HTTP)**.  
Como el problema se presentó al acceder al servidor web de yummyrecipesforme.com, sabemos que las peticiones a servidores web usan tráfico HTTP. Además, al ejecutar tcpdump y visitar yummyrecipesforme.com, el registro mostró explícitamente el uso de HTTP en la capa de aplicación para transportar el archivo malicioso a los equipos de los usuarios.

---

**Sección 2: Documentar el incidente**

1. **Reporte de usuarios:** varios clientes informaron al helpdesk que al visitar el sitio se les pedía descargar y ejecutar un archivo con “nuevas recetas”. Desde entonces, sus equipos operan muy lentos.
    
2. **Bloqueo del administrador:** el propietario del sitio intentó ingresar al servidor web y descubrió que su cuenta de administrador estaba bloqueada.
    
3. **Reproducción en sandbox:** el analista de ciberseguridad abrió el sitio en un entorno aislado y capturó el tráfico con tcpdump. Aceptó la descarga del archivo malicioso, lo ejecutó y fue redirigido a greatrecipesforme.com, un dominio falso.
    
4. **Análisis de tcpdump:** los logs mostraron primero la resolución DNS de yummyrecipesforme.com y luego el handshake y GET sobre HTTP. Tras ejecutar el archivo, se vio una nueva consulta DNS para greatrecipesforme.com y el tráfico se redirigió a su IP, confirmando el redireccionamiento malicioso.
    
5. **Investigación forense:** un profesional sénior revisó el código fuente y el ejecutable; halló que un atacante había inyectado un script para forzar la descarga de un “actualizador de navegador” malicioso. Al mismo tiempo, aprovechó un ataque de fuerza bruta contra la cuenta admin para cambiar la contraseña y bloquear al verdadero propietario. La ejecución del payload comprometió los equipos finales.
    

---

**Sección 3: Recomendaciones de remediación para ataques de fuerza bruta**

- **Impedir contraseñas anteriores:** configurar la política de contraseñas para que no se puedan reutilizar valores antiguos ni la contraseña por defecto.
    
- **Expiración frecuente:** forzar la actualización de contraseñas cada cierto período (por ejemplo, cada 60–90 días) para limitar la ventana de exposición si una credencial se ve comprometida.
    
- **Autenticación de dos factores (2FA):** exigir, además de la contraseña, la confirmación con un código de un solo uso (OTP) enviado por SMS o correo electrónico, para bloquear eficazmente los intentos de fuerza bruta.