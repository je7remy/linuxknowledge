
# 📬 Clase 3: Envío de Correos Automáticos con N8N (Gmail)

---

## 🎯 Objetivo

Aprenderás a:

- Conectar Gmail con N8N
    
- Enviar un correo automático con datos generados por un flujo anterior
    
- Usar expresiones dinámicas (como variables)
    
- Automatizar envíos con un _trigger_ programado por tiempo
    

---

## 🧩 Requisitos previos

- Haber completado la **Clase 2**: obtención del número total de máquinas desde Dockerlabs mediante petición HTTP y tratamiento con JavaScript.
    

---

## 🔗 Paso 1: Conectar Gmail con N8N

1. En tu workflow, haz clic en **"+"** y busca el nodo **Gmail**.
    
2. Selecciona la opción **"Send Email"**.
    
3. En **"Credentials"**, haz clic en **"Create new"** y luego en **"Sign in with Google"**.
    
4. Selecciona tu cuenta de Gmail y acepta los permisos.
    
5. Una vez conectado, cierra la ventana. Verás la conexión marcada como _Exitosa_ ✅.
    

---

## 📝 Paso 2: Configurar el correo

Completa los campos del nodo Gmail:

- **To**: tu dirección de destino (`ejemplo@gmail.com`)
    
- **Subject**: `Recuento de máquinas en Dockerlabs`
    
- **Email Type**: `Text` o `HTML`
    
- **Message** (clic en `Expression` para usar variables y saltos de línea):
    

```text
El recuento de máquinas en Dockerlabs es de:

{{$json["total_maquinas"]}}
```

> 🔍 Este valor viene del nodo anterior de tipo `Code`, que contenía la variable `total_maquinas`.

---

## 📤 Paso 3: Probar el envío

1. Ejecuta el workflow.
    
2. Verifica tu bandeja de entrada: deberías recibir un mensaje como este:
    

```
Asunto: Recuento de máquinas en Dockerlabs

El recuento de máquinas en Dockerlabs es de:

162
```

---

## ⏱️ Paso 4: Automatización por tiempo (Trigger programado)

1. Elimina el **Manual Trigger**
    
2. Añade un nodo **Schedule Trigger**
    
3. Configura el intervalo:
    
    - **Every**: `10`
        
    - **Unit**: `Seconds` (o minutos, horas, etc.)
        
4. Conecta este trigger al flujo de nodos.
    
5. Activa el flujo con el botón **“Activate”** en la parte superior.
    

> 📬 ¡Listo! Ahora recibirás un correo **cada 10 segundos** (o en el intervalo que configures).

---

## 🧠 Consejo Extra

Puedes configurar el trigger para que se ejecute:

- Cada hora
    
- Cada día a una hora exacta
    
- Una vez al mes
    
- En días específicos (cron jobs)
    

También puedes usar **otros triggers**:

- Cuando llegue un correo nuevo
    
- Cuando alguien interactúe con un bot de Telegram
    
- Cuando se modifique una hoja de cálculo de Google Sheets
    

---

## 🧭 Organización y buenas prácticas

- Cambia el nombre del flujo: haz clic en “Overview” → Renómbralo a “Dockerlabs Count”
    
- Guarda tus cambios siempre
    
- Recuerda: en la nube, tu cuenta tiene **1000 ejecuciones disponibles**
    
- Si quieres usar N8N sin límites, **instálalo localmente** (lo veremos pronto)
    

---

## ✅ Recapitulación

✔️ Conectaste Gmail a N8N  
✔️ Enviamos un correo automático con datos dinámicos  
✔️ Automatizaste el proceso con un trigger programado  
✔️ Personalizaste el cuerpo del mensaje con expresiones

---

