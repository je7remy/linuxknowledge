
## ✅ TAREA 1: Buscar mensajes de error

```bash
cd /home/analyst/logs
grep error server_logs.txt
```

🔹 Luego cuenta cuántas líneas devuelve. Esa es la respuesta para la pregunta de "¿Cuántas líneas de error hay?"

---

## ✅ TAREA 2: Encontrar archivos que contengan cadenas específicas

```bash
cd /home/analyst/reports/users
ls | grep Q1
ls | grep access
```

🔹 Cuenta cuántos archivos aparecen en cada comando.  
🔹 Esas cantidades son las respuestas para:

- “¿Cuántos archivos incluyen 'Q1'?”
    
- “¿Cuántos archivos incluyen 'access'?”
    

---

## ✅ TAREA 3: Buscar más contenido en archivos

```bash
grep jhill Q2_deleted_users.txt
grep "Human Resources" Q4_added_users.txt
```

🔹 Si el primer comando te devuelve una línea, selecciona “Sí” como respuesta a la pregunta de jhill.  
🔹 Cuenta cuántas líneas devuelve el segundo comando, y esa será la respuesta para cuántos usuarios se agregaron al departamento de **Human Resources**.

---

## 🚨 IMPORTANTE

- Asegúrate de ejecutar **cada comando exactamente como se indica**.
    
- **Haz clic en “Revisar mi progreso” después de cada sección**.
    
- No combines comandos incorrectamente (como `ls grep`), y asegúrate de que no estés en el directorio equivocado.
    

---

