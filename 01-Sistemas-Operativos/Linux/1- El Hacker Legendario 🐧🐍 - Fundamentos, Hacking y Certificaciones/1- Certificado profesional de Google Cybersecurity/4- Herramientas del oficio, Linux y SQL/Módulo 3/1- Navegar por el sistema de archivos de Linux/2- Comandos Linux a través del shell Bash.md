
# 🚀 Introducción práctica al uso del shell en Linux

## 👋 Bienvenida

Antes de sumergirnos en comandos específicos de Linux, vamos a revisar los fundamentos de cómo **comunicarse con el sistema operativo a través del shell**.

---

## 🎯 **¿Por qué es importante para un analista de seguridad?**

Como profesional de ciberseguridad, deberás ser capaz de:

- 📁 Navegar, gestionar y analizar archivos **remotamente y sin GUI**
    
- 👥 Verificar y configurar el acceso de **usuarios y grupos**
    
- 🔐 Autorizar usuarios y establecer **permisos de archivos**
    
- 💻 Usar comandos desde la **línea de comandos (CLI)** como una habilidad esencial
    

---

## 🧱 Fundamentos del Shell

Ya aprendimos que el **shell** es un componente principal de Linux. Existen varios shells, pero en esta sección trabajaremos con:

### 🐚 **Bash (Bourne Again Shell)**

> Es el **shell por defecto** en la mayoría de distribuciones Linux.

> ⚠️ _Aunque hay otros shells, los comandos clave que aprenderás aquí suelen funcionar igual en todos._

---

## 🧑‍💻 Comunicación con el sistema

> _Comunicarse con tu OS es como una conversación: tú escribes un comando y el sistema te responde._

- ✅ Un **comando** es una instrucción que le dice al sistema qué hacer.
    
- 💬 El sistema responde con **una salida**, **un mensaje**, o **un error**.
    

---

## 🧪 Práctica con Bash (Transcripción desde 1:27)

> "Probaremos un comando en Bash. Note un **signo de dólar `$`** antes del cursor.  
> Este es su _prompt_ para introducir un nuevo comando."

- Algunos comandos buscan archivos.
    
- Otros lanzan programas o imprimen texto.
    
- El comando `echo`, por ejemplo, **muestra una cadena de texto**.
    

---

## ✍️ Argumentos en los comandos (Transcripción desde 1:53)

> "Si usamos `echo`, necesitamos decirle **qué** mostrar. Para eso están los **argumentos**."

🔹 **Comando:** `echo`  
🔹 **Argumento:** `"¡Lo estás haciendo genial!"`

```bash
echo "¡Lo estás haciendo genial!"
```

📌 _Los argumentos son datos específicos que el comando necesita para funcionar._

> ⚠️ En Linux, **todo distingue entre mayúsculas y minúsculas**:

- `archivo.txt` ≠ `Archivo.txt`
    
- `Documentos` ≠ `documentos`
    

---

## 🧠 ¿Qué sigue?

> Ahora que dominas la estructura de comandos y argumentos en Bash, ¡estás listo para aprender **comandos específicos** de Linux que usarás como analista de seguridad!

---

## ❓ **Pregunta:**

**¿Qué es un Comando Linux?**

### Opciones:

-  Información que sale del shell
    
- [✅] **Una instrucción que le dice a la computadora que haga algo**
    
-  El shell por defecto en la mayoría de las distribuciones Linux
    
-  Un signo de dólar ($) antes del cursor
    

---

✅ **Respuesta correcta:**  
**Una instrucción que le dice a la computadora que haga algo**

📌 _Un comando en Linux es la forma en que el usuario le indica al sistema operativo qué acción ejecutar, ya sea mostrar información, mover archivos, instalar software, entre otras tareas._

---

