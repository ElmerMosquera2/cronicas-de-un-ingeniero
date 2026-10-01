---
tipo: gobernanza
id: DOMER-AGNOSTICA
status: Borrador
version: 0.2
fecha: 2026-09-23
complementos:
  - git
  - obsidian
---

# Gobernanza DOMER Agnóstica

## Preámbulo

DOMER es un marco de gobernanza documental **agnóstico al producto**. No prescribe un tema, una disciplina ni una herramienta; prescribe una **forma de organizar, decidir, producir y validar** el conocimiento dentro de un repositorio.

Este documento define el marco. Su aplicación concreta en cada proyecto se declara en la **Visión Activa** del repositorio gobernado.

DOMER se apoya en dos complementos externos:

- **Git**: preserva la trazabilidad, el versionado y la historia de los cambios.
- **Obsidian**: sirve como interfaz de lectura, navegación y edición del grafo documental.

La identidad no depende de ninguno de los dos; son las herramientas que hace a DOMER operativo.

---

## 1. Principios

| Principio | Significado operativo |
|---|---|
| **Organizada** | Toda nota, elemento o decisión ocupa un lugar explícito en la estructura. No hay documentos huérfanos. |
| **Metódica** | Los métodos, protocolos y enfoques se declaran como Decisiones Metódicas (MDR) antes de aplicarse. |
| **Evolutiva** | El conocimiento se versiona. Lo que cambia se registra; lo que se deprecia se archiva, no se borra. |
| **Rastreable** | Cada pieza documental puede rastrearse hasta su origen (una necesidad, una decisión, una experiencia) y hasta su validación. |

---

## 2. Estructura del Repositorio

Todo repositorio gobernado por DOMER adopta la siguiente estructura base:

```text
_docs_[nombre-proyecto]/
├──inbox/                # Entradas formales a procesamiento, pre-planing
├── vision/
│    ├── dominios/       # Identidad, reglas, sub-productos
│    └──va.md            # Vision activa (¿Que es?, ¿Que no es?, ¿Como se usa?)
├── req/                 # Elementos de Trabajo
├── adr/                 # Decisiones de arquitectura 
├── test/                # Validaciones de producto, integracio y funcionamiento
└── sprints/             # Ciclos de planeación

desk/                    # mesa de trabajo (borradores, experimentos, material)
build/                   # Espacio de producidos formales (parcheables)
cronicas/                # Notas crudas, bitácoras, experiencias sin procesar

README.md                # Estándar Git
CHANGELOG.md             # Estándar Git
```

### 2.1 `_docs_[nombre-proyecto]/`

Núcleo documental del repositorio. Es el **espacio gobernado por DOMER**. Se subdivide en cinco carpetas que corresponden a los cinco tipos documentales del marco:

- `inbox/` —  punto de entrada para planificacion o cambio de enfoque.
- **`vision/`** — Lo que se desea alcanzar (puede incluir imágenes, videos, dibujos y texto).
- **`vision/dominio/`** — Son los aspectos del sistema que estan previsionados.
- **`requisitos/`** — Aplica formalidad de una tarea.
- **`adr/`** — Decisiones metodicas/arquitectura (adr por convencion).
- **`test/`** — Casos de uso, revisiones, experimentos que validan lo producido.
- **`sprints/`** — Ciclos de planeación y cierre.

### 2.2 `productos/`

Espacio de trabajo. Contiene material sobre el que se esta trabajando, borradores, experimentos, prototipos. Lo que está aquí **no se considera estable**.
### 2.3 `build/`

Espacio de **producidos estables o formales**. Lo que llega aquí ha pasado por un ciclo de validación y se considera consolidado. por lo tanto equivale a elementos utilizables certificados segun los aspectos de calidad (ISO 25000) de las validaciones superadas. Es el equivalente a un "release", no implica perfección, sino que su calidad garantizas según términos de los criterios de cumplimiento de su propósito formal es adecuada al requisito.

### 2.4 `cronicas/`

Notas crudas. Bitácoras, experiencias, fragmentos sin procesar. **No están gobernadas por DOMER** en su forma ==FORMATO DE CRONICA ESTANDAR EN EVALUACION==; son materia prima de los procesos internos. Se recomienda que las crónicas locales se mantengan privadas e ignoradas por el sistema de control de versiones o que se aplique flujo de procesamiento en las formales de ci/cd para evitar documentación intrazable.

### 2.5 `README.md` y `CHANGELOG.md`

Por estándar Git. El `README.md` presenta el proyecto. El `CHANGELOG.md` registra los cambios relevantes del repositorio y, cuando aplica, de su gobernanza.

---

## 3. Tipos Documentales DOMER

DOMER reconoce cinco tipos documentales. Cada uno tiene una **función** y una **ubicación** dentro de `_docs_{{nombre espacio de trabajo}}/`.

### 3.1 Visión Activa y sub-dominios (VA)

**Función:** declarar el propósito, el alcance, los principios y los criterios de éxito del proyecto.

**Ubicación:** `vision/`.

**Características:**
- Son elementos **activos**: no documentos fundacionales congelados; evolucionan.
- Se versionan semánticamente.
- Cada revisión sustancial genera una nueva versión.
- Es la referencia última para decidir qué entra y qué no en el repositorio.

va.md

````markdown
```yaml
---
tipo: vision
id: VA-{{nombre-de-producto}}
estado: Borrador          # Borrador | Activa | Superada
naturaleza:               # libre, opcional — p.ej. Comercial, Herramienta, Hipótesis-solución
alternativas_evaluadas: false
---
```

## ¿Que es?

## ¿Que no es?

## ¿Como se usa?

## Alternativas Evaluadas (opcional)

````

\<dominio>.md

`````markdown
```yaml
---
tipo: dominio
dominio: "Mensajería"       # nombre del dominio; funciona como identificador
status: Propuesto           # Propuesto | En Delimitación | Delimitado
vision_origen: VA-XXX
---
```

# [DOMINIO] Nombre del dominio dentro del producto

## ¿Que es ?

## ¿Que no es?

`````


### 3.2 Requisito / Elemento de Trabajo (ET)

**Función:** declarar una unidad de trabajo concreta: qué se va a producir, para qué, con qué criterios de aceptación.

**Ubicación:** `requisitos/`.

**Características:**
- Puede derivar de una crónica, de una decisión o de una necesidad interna.
- Debe declarar su origen (trazabilidad hacia atrás) y su validación esperada (trazabilidad hacia adelante).
- Nombre: "Elemento de Trabajo → **REQ**".

**Formato:** `AND-XXX.md`.

`````markdown
```yaml
---
tipo: REQ
id: REQ-XXX
estado: Pendiente         # Pendiente | En desarrollo | Funcionando
prioridad: Alta           # Crítica | Alta | Media | Baja
dominio: Core             # eje: Pasarela de pago
origen: ADR-XXX           # o DOMINIO-XXX — exactamente UNA decisión
responsable: "@usuario"
sprint: "Sprint-03"
---
```

# [REQ-XXX] Nombre Descriptivo del Requisito

## 🎯 1. El "Por Qué"
*¿Qué problema técnico o de negocio resuelve? ¿Por qué es necesario ahora?*

## 👥 2. Actores y Alcance
*¿Quién interactúa con esta funcionalidad? ¿Qué queda explícitamente fuera?*

## 📋 3. Criterios de Aceptación
- [ ] Dado que [contexto inicial], cuando [acción], entonces [resultado esperado].

## ⚠️ 4. Notas Técnicas Preliminares (Opcional)

## 🔗 5. Trazabilidad
*   **Origen (ADR o MDR):** [[ADR-XXX]] o [[MDR-XXX]]
*   **Decisiones relacionadas:** [[ADR-YYY]] (si informan, no originan)
*   **Features que lo materializan:** [[FEAT-XXX]], [[FEAT-YYY]]
  
`````

**Formato:** `AND-XXX.md`.

`````markdown
```yaml
---
tipo: ET-{{CONVECIONAL}}  # FEATURE | FIX
id: ET-XXX
estado: Pendiente         # Pendiente | Cerrado
prioridad: Alta           # Crítica | Alta | Media | Baja
dominio: Core             # eje: Pasarela de pago
requisitos:               # lista de REQ que materializa
  - REQ-XXX
  - REQ-YYY
responsable: "@usuario"
sprint: "Sprint-03"
---
```

# [{{CONVECIONAL}}] Nombre Descriptivo de la FEATURE | FIX

## 🎯 1. Por Qué
*Qué necesidad de los REQ de origen resuelve esta pieza concreta.*

## 📋 2. Criterios de Cumplimiento
- [ ] Dado que [contexto], cuando [acción], entonces [resultado esperado].

## 🔗 4. Trazabilidad
*   **Requisitos que materializa:** [[REQ-XXX]], [[REQ-YYY]]
*   **Casos de Prueba (si los hay):** [[TC-XXX]]
`````


### 3.3 Decisión Metódica (MDR)

**Función:** declarar y justificar un método, protocolo o enfoque antes de aplicarlo.

**Ubicación:** `adr/`.

**Características:**
- No documenta resultados; documenta **cómo** se va a proceder.
- Puede ser adoptada, adaptada o rechazada explícitamente.
- Sirve como memoria metodológica del repositorio.

**Formato:** `ADR-XXX.md`.

`````markdown
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
rama: "adr/ADR-XXX-descripcion"
requisitos_derivados:
  - REQ-XXX
---
```

# [ADR-XXX] Título de la decisión

## Contexto
   → El método: la forma/paradigma elegido y el porqué.
   → Puede remitirse al documento de Dominio si el contexto ya está delimitado allí.

## Alternativas evaluadas
   → Al menos una alternativa considerada y por qué se descartó.

## Decisión
   → La decisión técnica concreta (tecnología, enfoque).
   

`````

### 3.4 Validación (TC)

**Función:** registrar el proceso mediante el cual un Elemento de Trabajo se considera válido.

**Ubicación:** `validaciones/`.

**Características:**
- Puede ser un caso de uso, una revisión, un experimento o una prueba.
- Conecta con el Elemento de Trabajo que valida.
- Si la validación falla, el ET vuelve a `productos/`.

**Formato:** `TC-XXX.md`.

### 3.5 Ciclo (CIC) **SCRUM**

**Función:** organizar la actividad del repositorio en unidades de planeación y cierre (SCRUM).

**Ubicación:** `ciclos/`.

**Características:**
- Cada ciclo tiene un `plan.md` (qué se abordará) y una `revision.md` (qué se aprendió).
- Los ciclos agrupan Elementos de Trabajo, MDR y Validaciones.
- La Visión Activa puede actualizarse al cierre de un ciclo.

**Formato:** `CIC-XXX/plan.md` y `CIC-XXX/revision.md`.

---

## 4. Flujo de Trabajo

El flujo canónico de DOMER es:

```text
crónica  →  Elemento de Trabajo  →  ADR (si aplica)  →  productos/  →  validación  →  build/
   ↑                                                                              │
   └────────────────────── cierre de ciclo (revision.md) ─────────────────────────┘
```

1. **Origen**: una experiencia, una nota cruda o una reflexión (en `cronicas/`).
2. **Formalización**: se crea un Elemento de Trabajo en `requisitos/`.
3. **Método**: si el requisito requiere un enfoque, se declara una ADR en `adr/`.
4. **Producción**: se trabaja en `productos/`.
5. **Validación**: se documenta en `validaciones/`.
6. **Consolidación**: lo validado se mueve a `build/`.
7. **Cierre**: el ciclo se cierra en `ciclos/CIC-XXX/revision.md`.

>[!IMPORTANT]
>Se introduce el andamio como elemento temporal en ciclos _si el requisito requiere revisión_

---

## 5. Reglas de Gobernanza

1. **Nada se borra; todo se archiva.** Lo deprecado se mueve a `_Archivo/` con una nota de motivo.
2. **Todo cambio relevante se registra en `CHANGELOG.md`.**
3. **Toda decisión metódica se declara antes de aplicarse.**
4. **Toda Visión Activa se versiona semánticamente.**
5. **Todo Elemento de Trabajo tiene un origen y una validación esperada.**
6. **`cronicas/` no está gobernado por DOMER**; es materia prima.
7. **`productos/` no es estable**; lo estable vive en `build/`.
8. **Los complementos Git y Obsidian no son obligatorios**, pero su uso está previsto y documentado.

---

## 6. Versionado

DOMER Agnóstica se versiona así:

| Versión | Significado |
|---|---|
| `0.x` | Borrador. El marco aún no es estable. |
| `1.x` | Marco estable. Aplicable a proyectos reales. |
| `2.x` | Cambios incompatibles con la versión anterior del marco. |

La versión actual es **`0.2` (Borrador)**.

---

## 7. Estado de este Documento

| Versión | Fecha      | Cambio                                                                                                                                            | Estado   |
| ------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| 0.1     | —          | Versión previa (referencia).                                                                                                                      | Obsoleta |
| 0.2     | 2026-09-23 | Adaptación agnóstica con estructura `_docs_/`, `productos/`, `build/`, `cronicas/`. Separación en visión, requisitos, MDR, validaciones y ciclos. | Borrador |

---

## 8. Pendientes

- [x] Redefinir el nombre de "Elemento de Trabajo" (`requisitos/`).
- [x] Definir el formato exacto de YAML para cada tipo documental.
- [ ] Documentar el procedimiento de paso de `productos/` a `build/`.
- [ ] Definir si `cronicas/` se integra a `_docs_/` o permanece separada.
- [ ] Establecer los criterios de cierre de un ciclo.
- [ ] Redactar la Visión Activa `VA-001` aplicada a este repositorio.



