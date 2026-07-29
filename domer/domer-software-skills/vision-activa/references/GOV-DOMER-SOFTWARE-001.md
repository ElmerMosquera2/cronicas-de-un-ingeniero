---
tipo: gobernanza
id: GOV-DOMER-SOFTWARE-FOR-VA
version: 2.3.0
ultima_revision: 2026-07-28
reemplaza: GOV-001 v2.2.0
---

# Manual de Gobernanza de la Documentación

Este documento establece el estándar oficial para la captura, organización y evolución de la visión de producto, las decisiones técnicas, los requisitos y las piezas de planificación de bajo nivel dentro de este repositorio, utilizando **Obsidian** y **GitHub** como núcleo del flujo de trabajo.

La metodología prioriza la trazabilidad del *porqué* por encima de la documentación estática, pero mantiene la simplicidad de la versión 2.2.0. Incorpora la **Visión Activa** como semilla del sistema y las **Features** como lienzos de planeación que aterrizan los requisitos en trabajo concreto, sin forzar vínculos a PRs futuros y respetando la filosofía original de conservación mínima.

---

## 1. Segmentación del repositorio

El repositorio se organiza en áreas de responsabilidad clara. Solo se gobiernan los contenidos dentro de `docs/`; el resto sigue las convenciones del proyecto.

```text
repo-root/
├── docs/          # Fuente de verdad de la gobernanza (visión, requisitos, decisiones, features).
├── software/      # Código fuente del producto.
├── build/         # Artefactos generados automáticamente (referencias técnicas, esquemas, etc.).
├── .github/       # Workflows de CI/CD, plantillas de Issues y Pull Requests.
└── README.md
```

**Regla de frontera `docs/` vs `build/`:**
> Si alguien tuvo que decidir conscientemente algo, pertenece a `docs/`. Si se puede derivar o regenerar automáticamente desde el código, pertenece a `build/`.

---

## 2. Estructura del directorio (`docs/`)

```text
docs/
├── 00_Inbox/            # Captura rápida de ideas, feedback sin procesar y notas de reuniones.
├── 01_Product/          # Visión de negocio, roadmaps, alcance, usuarios objetivo.
│   └── Vision/          # VA-XXX.md — la Visión Activa, única nota que no nace en Inbox.
├── 02_Requirements/     # Requisitos de alto nivel (REQ-XXX).
│   └── _Templates/      # Plantillas reutilizables de todas las notas.
├── 03_Architecture/     # Decisiones de Arquitectura (ADR-XXX) y Decisiones Metódicas (MDR-XXX).
├── 04_Features/         # Elementos de planeación de bajo nivel (FEAT-XXX).
├── 05_Sprints/          # Planificación cíclica, minutas y revisiones.
│   ├── Sprint-01/
│   └── Sprint-02/
├── 06_Testing/          # Casos de prueba (TC-XXX), planes de validación (opcional).
├── _Archive/            # Notas obsoletas o deprecadas que se conservan por trazabilidad.
└── SISTEMATIZACION.md   # Este manual.
```

**Reglas de uso:**
- `00_Inbox/` no requiere estructura; aquí se vuelca cualquier pensamiento.
- Toda nota nace en `00_Inbox/`, excepto la Visión Activa (VA). La VA es la semilla del sistema y se crea directamente en `01_Product/Vision/`.
- Las carpetas `02_Requirements/`, `03_Architecture/` y `04_Features/` solo contienen notas con frontmatter válido.
- `03_Architecture/` alberga tanto ADR como MDR, con numeración independiente (`ADR-001`, `MDR-001`).
- `_Archive/` recibe notas con `status: Deprecado` o `Superada` que ya no están activas, según la política de conservación (ver sección 11).

---

## 3. Jerarquía general del sistema

```text
Visión Activa (VA)  ── 1 ──────────► N  MDR / ADR
                                            │
                                          1 ──────► N  REQ
                                                          │
                                                       1 ◄──────► M  FEATURE
```

- **VA → MDR/ADR** es 1:N. Cada MDR/ADR tiene exactamente una `vision_origen`.
- **MDR/ADR → REQ** es 1:N. Cada REQ tiene exactamente un `origen` (ADR o MDR).
- **REQ ↔ FEATURE** es N:M. Una Feature puede materializar varios REQ, y un REQ puede descomponerse en varias Features. Esta es la única relación de composición del sistema.

---

## 4. Estándar de Metadatos (Propiedades Frontmatter)

### 4.1 Visión Activa (`01_Product/Vision/VA-XXX.md`)

```yaml
---
tipo: vision
id: VA-XXX
status: Borrador          # Borrador | Activa | Superada
naturaleza:               # libre, opcional — p.ej. Comercial, Herramienta, Hipótesis-solución
alternativas_evaluadas: false
---
```

**Cuerpo mínimo para `status: Activa`:**
- **Qué es y cómo se usa** — un bloque que puede incluir el método.
- **Lo que no es** — límites explícitos del producto.
- **Alternativas cercanas** — opcional, señal de madurez.

### 4.2 Decisión Metódica (`03_Architecture/MDR-XXX.md`)

```yaml
---
tipo: mdr
id: MDR-XXX
status: Propuesta         # Propuesta | Aceptada | Superada
fecha: YYYY-MM-DD
vision_origen: VA-XXX
dominio:                  # opcional (pilar de la visión)
reemplaza: MDR-000
superada_por:
rama: "mdr/MDR-XXX-descripcion"
---
```

### 4.3 Decisión de Arquitectura (`03_Architecture/ADR-XXX.md`)

```yaml
---
tipo: adr
id: ADR-XXX
status: Propuesto         # Propuesto | Aceptado | Superado
fecha: YYYY-MM-DD
vision_origen: VA-XXX
dominio: "Nombre del pilar"  # obligatorio en ADR
reemplaza: ADR-000
superado_por:
requisitos_derivados:
  - REQ-XXX
---
```

**Criterio MDR vs ADR:**
MDR decide la **forma o paradigma** de la solución (todavía habla el lenguaje de la Visión).
ADR decide la **tecnología concreta** que materializa esa forma.

### 4.4 Requisito (`02_Requirements/REQ-XXX.md`)

```yaml
---
tipo: requisito
id: REQ-XXX
status: Pendiente         # Pendiente | En Planificación | Planificado | Deprecado
prioridad: Alta           # Crítica | Alta | Media | Baja
modulo: Core
origen: ADR-XXX            # o MDR-XXX — exactamente UNA decisión
responsable: "@usuario"
sprint: "Sprint-03"
---
```

### 4.5 Feature (`04_Features/FEAT-XXX.md`)

```yaml
---
tipo: feature
id: FEAT-XXX
status: Pendiente         # Pendiente | En Diseño | Aprobado | Deprecado
requisitos:               # lista de REQ que materializa
  - REQ-XXX
  - REQ-YYY
responsable: "@usuario"
---
```

### 4.6 Caso de Prueba (`06_Testing/TC-XXX.md`) (opcional)

```yaml
---
tipo: test-case
id: TC-XXX
status: Diseñado          # Diseñado | Automatizado | Ejecutado | Fallido
feature: FEAT-XXX
modulo: Core
---
```

---

## 5. Definición de Listo (DoR) y Definición de Hecho (DoD) por tipo

### 5.1 VA — Visión Activa
**DoR para `Activa`:** contiene "qué es", "qué no es" y, opcionalmente, alternativas.
No tiene DoD; se supera cuando otra VA la reemplaza.

(El resto de las secciones de DoR/DoD, anatomía de notas, ciclo de vida, GitFlow, automatización de vistas y política de conservación se omiten aquí por brevedad — no son necesarias para la tarea de esta skill, que se limita a pulir el cuerpo de la VA. Consultar el manual completo del proyecto si se necesita el resto del contexto.)