---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Ejemplar opcional, Filtrado con grep

### **Comandos por tarea**

#### **Tarea 1 – Mensajes de error**

```bash
cd /home/analyst/logs
grep error server_logs.txt
```

- Respuesta: **6 líneas** (selecciona "Seis").
    

---

#### **Tarea 2 – Archivos con cadenas específicas**

```bash
cd /home/analyst/reports/users
ls | grep Q1
ls | grep access
```

- Respuesta Q1: **3 archivos** (selecciona "Tres").
    
- Respuesta access: **4 archivos** (selecciona "Cuatro").
    

---

#### **Tarea 3 – Buscar contenido en archivos**

```bash
ls
grep jhill Q2_deleted_users.txt
grep "Human Resources" Q4_added_users.txt
```

- Respuesta jhill: **Sí**.
    
- Respuesta Human Resources: **2 usuarios** (selecciona "Dos").
    

---

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[3- Actividad, Filtrado con grep]]
- ➡️ Siguiente: [[5- Ejemplar, Filtrado con grep]]
