---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# PASTA - Proceso de Simulación de Ataques y Análisis de Amenazas

# 🛡️ Framework PASTA (Proceso para la Simulación de Ataques y el Análisis de Amenazas)

PASTA es un **framework de modelado de amenazas** que consta de **siete etapas**. Su objetivo es identificar riesgos, simular ataques y alinear la seguridad con los objetivos del negocio.

---

## 1️⃣ Definir los objetivos empresariales y de seguridad

- Se establecen las metas principales del proyecto.
    
- **Ejemplo:** proteger los datos de los clientes en la aplicación de acondicionamiento físico.
    
- Preguntas clave: ¿cómo se maneja la información personal identificable (PII)? ¿qué impacto tendría un ataque?
    

---

## 2️⃣ Definir el alcance técnico

- Identificación de la **superficie de ataque**.
    
- Incluye todos los componentes de la app y su infraestructura:
    
    - Protocolos de red
        
    - Controles de seguridad
        
    - Almacenamiento y uso de datos
        

---

## 3️⃣ Descomponer la aplicación

- Se realiza un **diagrama de flujo de datos** (DFD).
    
- Muestra cómo viaja la información del usuario hasta la base de datos.
    
- Se identifican controles existentes que protegen los datos.
    

---

## 4️⃣ Análisis de amenazas

- El equipo adopta una **mentalidad de atacante**.
    
- Investigación sobre los ataques más comunes en apps móviles.
    
- Se documentan los vectores de ataque más relevantes (ejemplo: inyección SQL).
    

---

## 5️⃣ Análisis de vulnerabilidades

- Se examinan las **debilidades en el sistema** que podrían ser explotadas.
    
- Se analizan las causas raíz de esas vulnerabilidades.
    

---

## 6️⃣ Modelos de ataque

- Se crean **árboles de ataque**, diagramas que mapean vectores de ataque.
    
- Ejemplo en la app:
    
    - **Objetivo:** datos de clientes (usuarios/contraseñas).
        
    - **Vector:** base de datos vulnerable a inyección SQL.
        
    - **Explotación:** entradas no desinfectadas.
        

---

## 7️⃣ Análisis de riesgo e impacto

- Se recopila toda la información de las fases anteriores.
    
- Se hacen **recomendaciones de gestión de riesgos** alineadas con los objetivos del negocio.
    
- Opciones: evitar, transferir, reducir o aceptar el riesgo.
    

---

✅ Con estas **7 fases de PASTA**, el equipo de seguridad puede **anticipar ataques reales** y proponer defensas efectivas antes del lanzamiento de la aplicación.

### ❓ Pregunta

**Rellene el espacio en blanco:**  
PASTA es un popular framework de _____ que se utiliza en muchos sectores.

- Modelado de amenazas ✅
    
- Clasificación de activos
    
- Árbol de ataque
    
- Gestión de vulnerabilidades
    

---

### ✔️ Respuesta Correcta

**Modelado de amenazas**

👉 **PASTA** (Process for Attack Simulation and Threat Analysis) es un framework de **modelado de amenazas** usado en múltiples industrias.

- Su objetivo es **identificar recursos, vulnerabilidades y cómo están expuestos a amenazas**.
    
- Permite simular ataques y priorizar defensas con un enfoque estructurado.
    

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ⬅️ Anterior: [[6- Chantelle - El valor de la diversidad en la ciberseguridad]]
- ➡️ Siguiente: [[8- Rasgos de un modelo de amenaza eficaz]]
