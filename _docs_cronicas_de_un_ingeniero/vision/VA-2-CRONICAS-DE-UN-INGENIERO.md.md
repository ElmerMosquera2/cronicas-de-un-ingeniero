---
tipo: vision_activa
id: VA-2-CRONICAS-DE-UN-INGENIERO
status: Borrador
version: 1
fecha_creacion: 2026-09-23
autores: "@ElmerMosquera2"
dominios:
  - gobernanza documental
  - ingeniería de software
  - narrativa técnica
  - trazabilidad de conocimiento
---

# Visión Activa: Crónicas de un Ingeniero

## 1. Propósito Central

**Crónicas de un Ingeniero** es un repositorio que reúne crónicas sobre el ejercicio de construir software. Cada crónica documenta una experiencia, una decisión, un problema, un aprendizaje o una reflexión nacida de la práctica, preservando el contexto suficiente para comprender no solo el resultado, sino también el camino recorrido.

El propósito de esta Visión Activa es articular, de forma explícita y versionada, el **porqué** de este repositorio, el **qué** se persigue con él y el **cómo** se gobierna su evolución. No es un documento estático: nace en `01_Vision/`, se versiona desde su primer borrador y evoluciona junto con las crónicas que alberga.

## 2. Pregunta de Conocimiento

> **¿Cómo se construye software, no solo como producto, sino como proceso de aprendizaje, decisión y gobernanza?**

Esta pregunta guía la selección, redacción y organización de cada crónica. No se busca documentar únicamente el resultado final (el software funcionando), sino el **camino recorrido**: las decisiones tomadas, los errores cometidos, las alternativas descartadas y las lecciones aprendidas.

## 3. Fenómeno a Comprender

El fenómeno central es el **ejercicio de construir software** como actividad humana, técnica y reflexiva. Este fenómeno se manifiesta en múltiples dimensiones:

- **Dimensión técnica**: arquitectura, código, herramientas, metodologías.
- **Dimensión decisional**: elección de enfoques, trade-offs, deuda técnica.
- **Dimensión narrativa**: cómo se cuenta y se preserva la experiencia.
- **Dimensión de gobernanza**: cómo se organiza, versiona y valida el conocimiento generado.

## 4. Principios Rectores (DOMER)

Este repositorio se rige por el marco de gobernanza **DOMER** (*Documentación Organizada, Metódica, Evolutiva y Rastreable*), adaptado de su versión agnóstica. Esto implica:

| Principio | Aplicación en este repositorio |
|---|---|
| **Organizada** | Estructura de carpetas explícita (`00_Bandeja_Entrada/` a `05_Validacion/`), con metadatos YAML en cada nota. |
| **Metódica** | Uso de **Decisiones Metódicas (MDR)** para documentar enfoques, métodos y protocolos. |
| **Evolutiva** | Ciclos de producción (`04_Ciclos/`) con `plan.md` y `revision.md`. Versionado semántico de la Visión Activa. |
| **Rastreable** | Cada crónica, elemento o decisión conecta con su origen y su validación. Uso de `_Archivo/` para notas deprecadas. |

## 5. Alcance del Repositorio

**Incluye:**
- Crónicas narrativas sobre experiencias concretas de construcción de software.
- Reflexiones sobre decisiones técnicas, metodológicas y de gobernanza.
- Documentación del propio sistema de gobernanza (DOMER) aplicado al repositorio.
- Trazabilidad de la evolución de la Visión Activa y de las crónicas.

**Excluye:**
- Documentación de producto final sin contexto narrativo.
- Código fuente de proyectos ajenos al ejercicio de construir software.
- Contenido no relacionado con la práctica de la ingeniería de software.

## 6. Guía de Actividad

La actividad del repositorio se organiza en **ciclos** (ver `04_Ciclos/`). Cada ciclo:

1. **Planifica** qué crónicas, elementos o decisiones se abordarán (`plan.md`).
2. **Ejecuta** el trabajo en ramas activas (`dominio/`, `metodo/`, `exploracion/`).
3. **Documenta** el cierre del ciclo, incluyendo lecciones aprendidas (`revision.md`).

Las crónicas se formalizan como **Elementos de Trabajo (ET-XXX)** y se validan a través de casos de uso, revisiones o experimentos en `05_Validacion/`.

## 7. Criterios de Éxito

- **Trazabilidad**: cada crónica puede rastrearse hasta su origen (una experiencia, una decisión, un problema).
- **Contexto preservado**: el lector comprende no solo el resultado, sino el camino recorrido.
- **Gobernanza explícita**: la estructura y evolución del repositorio son comprensibles y auditables.
- **Evolución versionada**: la Visión Activa se actualiza con cada revisión sustancial, conservando versiones anteriores.
- **Utilidad narrativa**: las crónicas sirven como material de aprendizaje para otros practicantes.

## 8. Estado de la Visión

| Versión | Fecha | Cambio | Estado |
|---|---|---|---|
| 1.0 | 2026-09-23 | Creación inicial de la Visión Activa. | Borrador |
| — | — | Pendiente: revisión tras primer ciclo de producción. | — |

---

