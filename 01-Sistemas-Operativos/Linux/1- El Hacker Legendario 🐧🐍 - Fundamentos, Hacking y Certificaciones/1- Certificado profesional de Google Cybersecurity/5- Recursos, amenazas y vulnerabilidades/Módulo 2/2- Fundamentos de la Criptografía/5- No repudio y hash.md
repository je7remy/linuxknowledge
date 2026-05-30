---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# No repudio y hash

# 🔐 Funciones Hash en Seguridad

## 🚨 Vulnerabilidades de las claves

- Los algoritmos de cifrado (asimétricos y simétricos) producen **claves** que deben compartirse para comunicar información.
    
- Estas claves son vulnerables a **pérdida** o **robo**, lo que puede comprometer datos confidenciales.
    
- Para abordar esta debilidad, se utiliza otro control: **las funciones hash**.
    

---

## 🧩 ¿Qué es una función hash?

- Una **función hash** es un algoritmo que produce un código **no reversible**.
    
- A diferencia del cifrado:
    
    - No hay claves de desencriptación.
        
    - Genera un **valor hash** o **resumen único**.
        
- Es un proceso **unidireccional** diseñado para verificar integridad, no para recuperar datos.
    

---

## 📝 Ejemplo práctico

1. Una empresa tiene una aplicación interna almacenada en una unidad compartida.
    
2. La aplicación pasa por una función hash (ejemplo: **MD5** o **SHA-256**) → genera un valor hash único.
    
3. Si un atacante modifica el programa:
    
    - Aunque funcione igual, una sola línea distinta cambia el hash.
        
    - Comparando los valores hash se detecta la alteración.
        

👉 Los hashes ayudan a **identificar versiones alteradas de programas o archivos**.

---

## 🔎 Usos en Seguridad

- Verificar **integridad de archivos y aplicaciones**.
    
- Prevenir el **repudio**, ya que no se puede negar la autenticidad de un archivo validado por hash.
    
- Comparar el valor hash de un archivo con los de **malware conocido**.
    

### Ejemplo en Linux

Para calcular el hash **SHA-256** de un archivo:

```bash
sha256sum newfile.txt
```

**Salida esperada (ejemplo):**

```
d2a537...c9f1b2  newfile.txt
```

---

## 🌐 Herramientas útiles

- **VirusTotal**: base de datos pública donde se comparan hashes de archivos sospechosos contra hashes de malware conocidos.
    
- Muy usada por analistas de seguridad para analizar:
    
    - Archivos
        
    - Dominios
        
    - Direcciones IP
        
    - URLs
        

---

## ✅ Conclusión

- Los **hashes** cambian drásticamente con mínimas variaciones en los datos.
    
- Proveen una forma rápida y confiable de:
    
    - Validar integridad.
        
    - Detectar alteraciones.
        
    - Garantizar **no repudio**.
        

👉 Son un **control esencial** en la seguridad informática.

---
### ❓ Pregunta

**Rellene el espacio en blanco:**  
Los valores hash se utilizan principalmente para determinar el **_____** de archivos y aplicaciones.

Opciones:

-  resumen
    
-  una función nueva
    
-  integridad 👍
    
-  disponibilidad
    

---

### ✅ Respuesta correcta:

**integridad**

**Justificación:**  
Los valores hash se utilizan principalmente para **verificar la integridad** de archivos y aplicaciones, es decir, comprobar que no han sido alterados.  
Además, los hashes ayudan a mantener la **confidencialidad**, ya que son procesos unidireccionales y no pueden desencriptarse para revelar la información original.

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ⬅️ Anterior: [[4- Actividad - Desencriptación de un mensaje encriptado]]
- ➡️ Siguiente: [[6- La evolución de las funciones hash]]
