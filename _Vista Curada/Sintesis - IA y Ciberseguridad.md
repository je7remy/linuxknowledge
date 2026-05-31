---
tipo: teoria
tags: [sintesis, ia, ciberseguridad, llm, amenazas]
actualizado: 2026-05-30
---

# Síntesis — IA y Ciberseguridad

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Nota de síntesis cross-dominio** que conecta los cursos de IA
([[_07- Inteligencia-Artificial|07 — IA]]) con el dominio ofensivo y
defensivo de ciberseguridad ([[_02-Ciberseguridad|02 — Ciberseguridad]]).
La IA es a la vez **arma** y **defensa** — esta nota mapea cómo.

## Las dos caras

```
        IA en ciberseguridad
        ┌──────────────────┐
        │                  │
   USO OFENSIVO        USO DEFENSIVO
   (más eficiente)     (más eficiente)
        │                  │
        ↓                  ↓
   amenazas nuevas    detección/respuesta
        │                  │
        └──────────────────┘
             carrera
        atacante ↔ defensor
```

## Capa 1 — Fundamentos de IA (el qué)

Antes de hablar de ciberseguridad con IA, dominar los conceptos:

- [[_1- Programa especializado - Fundamentos de IA de Google|Fundamentos de IA — Google]] —
  Qué es IA, ML, DL, redes neuronales.
- [[_3- Descubra el arte de la instrucción|Arte de la instrucción]] —
  Prompting básico y avanzado.
- [[_Ingenieria de Pront|Ingeniería de prompts]] — Técnicas para LLMs.
- [[_Microsoft Reactor Python + IA|Microsoft Reactor Python + IA]] —
  Embeddings, RAG, Vision, Tool use, Calidad y seguridad.

## Capa 2 — Uso ofensivo (lo que hacen los atacantes)

### 2.1 Phishing potenciado por LLMs

Antes: emails con errores gramaticales delatores.
Ahora: LLMs escriben spear phishing en cualquier idioma con tono creíble.

- Personalización masiva con info de [[OSINT]].
- Voice cloning para vishing (ataques telefónicos).
- Deepfakes para fraude CEO.

### 2.2 Generación de malware

- Polymorphic malware que cambia su firma cada infección.
- LLMs generan payloads, encoders, bypasses de AV.
- Modelos como WormGPT, FraudGPT (versiones jailbroken comerciales).

### 2.3 Reconocimiento automatizado

- LLMs pueden parsear miles de páginas y extraer info estructurada.
- Acelera la fase 2 ([[OSINT]]) de [[MOC - Pentesting end-to-end|pentesting]].

### 2.4 Prompt injection y exfiltración de datos

- Inyectar comandos en chatbots conectados a herramientas (function calling).
- Indirect prompt injection: payload en una web que el LLM lee.
- Extracción de prompts del sistema, datos de training.

[[_4- Utiliza la IA de forma responsable|Curso IA Responsable]] — cubre
ética del uso ofensivo.

### 2.5 Amenazas específicas del dominio

- [[_8- Amenazas de CIberataques Impulsados por IA|Amenazas de ciberataques impulsados por IA]] —
  Sección dedicada (Fortinet CNCS).

## Capa 3 — Uso defensivo (lo que hacen los defensores)

### 3.1 Detección de anomalías

- Modelos ML detectan patrones de tráfico anómalo en SIEMs.
- User and Entity Behavior Analytics (UEBA).
- Detección de spear phishing por análisis lingüístico.

### 3.2 Análisis de logs a escala

- LLMs leen miles de logs y resumen incidentes.
- Generación automática de reglas Sigma / Yara.
- Triage de alertas para reducir _alert fatigue_ en SOC.

### 3.3 Pentesting asistido

- Copilots para pentesters: explican CVEs, sugieren payloads, escriben PoCs.
- Generación de reportes de pentest a partir de findings.

### 3.4 Threat intelligence

- Clasificación automática de IoCs (Indicators of Compromise).
- Resumen de threat reports en feeds.
- Correlación cross-fuente que un humano no podría hacer manualmente.

### 3.5 Verificación de código

- LLMs detectan vulnerabilidades en código durante code review.
- GitHub Copilot warnings de prácticas inseguras.
- Análisis estático automatizado.

## Capa 4 — Riesgos de la propia IA

Implementar IA introduce **nueva superficie de ataque**:

| Riesgo | Descripción |
|---|---|
| **Prompt injection** | Atacante inserta instrucciones en input del LLM. |
| **Data poisoning** | Manipular dataset de training para sesgar predicciones. |
| **Model inversion** | Reconstruir datos privados desde queries al modelo. |
| **Adversarial examples** | Inputs maliciosos que engañan clasificadores. |
| **Supply chain (models)** | Modelos pre-entrenados con backdoors. |
| **Shadow AI** | Empleados usan LLMs externos con data corporativa. |

## OWASP Top 10 for LLM Applications (2023+)

Lista canónica de riesgos en aplicaciones que integran LLMs:

1. **Prompt Injection**.
2. **Insecure Output Handling**.
3. **Training Data Poisoning**.
4. **Model Denial of Service**.
5. **Supply Chain Vulnerabilities**.
6. **Sensitive Information Disclosure**.
7. **Insecure Plugin Design**.
8. **Excessive Agency** (LLM con demasiados permisos en función calling).
9. **Overreliance** (humanos confían sin verificar).
10. **Model Theft**.

## Capa 5 — Mantenerse al día

El campo cambia rápido. Recursos:

- [[_5- Mantente a la vanguardia de la IA|Curso "Mantente a la vanguardia"]] —
  metodología para seguir el campo.
- Newsletters: TLDR AI, Import AI, The Batch.
- Papers: arxiv.org (cs.CR + cs.AI cross), DEFCON / Black Hat AI tracks.
- Comunidades: r/MachineLearning, AI Alignment Forum.

## Cobertura en el vault

| Tema | Notas principales |
|---|---|
| Fundamentos IA | [[_07- Inteligencia-Artificial\|07 — IA]] (5 cursos) |
| Amenazas con IA | [[_8- Amenazas de CIberataques Impulsados por IA\|8- Amenazas IA]] |
| Prompting técnico | [[_Ingenieria de Pront\|Ingeniería de prompts]] |
| Uso responsable | [[_4- Utiliza la IA de forma responsable\|Curso IA Responsable]] |
| Microsoft Reactor | [[_Microsoft Reactor Python + IA\|Taller MS Reactor]] |

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[MOC - Pentesting end-to-end|MOC - Pentesting end-to-end]] — dónde la IA
  ofensiva acelera fases.
- [[OSINT|OSINT (entity page)]] — donde la IA potencia recon.
- [[Pentesting|Pentesting (entity page)]] — el dominio donde la IA es
  arma y herramienta.
