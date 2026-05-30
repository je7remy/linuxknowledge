---
tipo: teoria
tags: [pentesting, black-box, white-box, grey-box, hacking-etico, ingenieria-social]
actualizado: 2026-05-28
---

# Tipos de Pruebas de Penetración

#Ciberseguridad #Pentesting #BlackBox #WhiteBox #GreyBox #HackingÉtico #Vulnerabilidades #SeguridadFinanciera #IngenieríaSocial #SeguridadFísica

---
# **📊 Tipos de Pruebas de Penetración**  
**Clasificación según el conocimiento del evaluador**  

---

### **🔳 1. Pruebas de Caja Negra (Black Box)**  
| **Característica**       | **Detalle**                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Conocimiento previo**  | **Ninguno** (simula un atacante externo).                                  |
| **Enfoque**              | Vulnerabilidades de cara al público.                                       |
| **Ejemplo práctico**     | Institución financiera: certificado SSL obsoleto e inyección SQL en login. |
| **Ventaja**              | Refleja escenarios reales de ataques remotos.                              |

---

### **⬜ 2. Pruebas de Caja Blanca (White Box)**  
| **Característica**       | **Detalle**                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Conocimiento previo**  | **Acceso total** (código fuente, arquitectura, configuraciones).           |
| **Enfoque**              | Errores internos: configuraciones, políticas, parches.                     |
| **Ejemplo práctico**     | Reglas de firewall mal configuradas, contraseñas débiles en sistemas.      |
| **Ventaja**              | Profundidad técnica para identificar vulnerabilidades ocultas.             |

---

### **🔘 3. Pruebas de Caja Gris (Grey Box)**  
| **Característica**       | **Detalle**                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Conocimiento previo**  | **Parcial** (simula un atacante interno o con acceso inicial).             |
| **Enfoque**              | Explotar brechas en redes internas o acceso físico.                        |
| **Ejemplo práctico**     | Red Wi-Fi no segura en sucursal bancaria.                                   |
| **Ventaja**              | Combina perspectivas externas e internas.                                  |

![[2.1- Pruebas Unitarias.jpg]]

---

## **🏦 Caso de Estudio: Institución Financiera**  
### **🔍 Evaluación Integral**  
```diff
+ Plataforma de banca en línea: Vulnerabilidades críticas (SSL, SQLi).  
+ Redes internas: Firewall, contraseñas débiles, software sin parches.  
+ Seguridad física: Tailgating en salas de servidores.  
- Riesgos humanos: Documentos expuestos, credenciales visibles.  
```  
**📌 Resultados clave**:  
- Segmentación de red mejorada.  
- Políticas de seguridad actualizadas.  
- Capacitación en concienciación para empleados.  

---

## **🎯 Perspectivas de Pruebas**  
### **🌐 Pruebas Externas (External Testing)**  
```markdown
**Objetivo**: Evaluar activos públicos (servidores web, DNS, correo).  
**Simulación**: Ataques remotos desde Internet.  
**Ejemplo**: Escaneo de puertos, explotación de servicios expuestos.  
```  

### **🏢 Pruebas Internas (Internal Testing)**  
```markdown
**Objetivo**: Simular amenazas internas o post-violación.  
**Enfoque**: Acceso con credenciales legítimas o comprometidas.  
**Ejemplo**: Movimiento lateral en la red, escalada de privilegios.  
```  

---

## **⚠️ Riesgos No Técnicos Identificados**  
| **Área**                 | **Brechas**                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Ingeniería social**    | Tailgating, phishing exitoso.                                              |
| **Seguridad física**     | Acceso a áreas restringidas sin autorización.                              |
| **Políticas**            | Documentación confidencial expuesta, escritorios desatendidos.             |

---

## **🛠️ Conclusión**  
Las pruebas de penetración deben combinar:  
✅ **Enfoques técnicos** (caja negra/blanca/gris).  
✅ **Evaluación de riesgos humanos** (ingeniería social).  
✅ **Perspectivas internas/externas**.  
**Resultado**: Una postura de seguridad robusta y adaptada a amenazas reales.  

---

**Esquema visual**:  
- Uso de tablas para comparar categorías.  
- Códigos de colores (```diff``` para resaltar hallazgos).  
- Iconos y secciones claramente delimitadas.  
- Ejemplos prácticos integrados.  

---

## Navegación

- ⬆️ Carpeta: [[index|2- Introducción a las pruebas de penetración]]
- ⬅️ Anterior: [[1- Introducción]]
- ➡️ Siguiente: [[3- Áreas y dominios de prueba]] — dónde se aplican estos tipos.

## Relacionadas

- [[1- Introducción]] — las fases del pentesting que enmarcan estos tipos.
- [[4- Beneficios de las pruebas de penetración]] — el caso financiero aparece como ejemplo aquí.
- [[../../../../../../02-Ciberseguridad/3- hacking basico/6- Web/index|02 → Hacking básico → Web]] — SQLi mencionado en el ejemplo Black Box.
