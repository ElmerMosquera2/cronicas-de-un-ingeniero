## 1. Estándar de Metadatos (Propiedades Frontmatter)

### 1.1 Visión Activa (`01_Product/Vision/VA-XXX.md`)

```md
---
tipo: vision
id: VA-XXX
estado: Borrador # Borrador | Activa | Superada
naturaleza: # libre, opcional — p.ej. Comercial, Herramienta, Hipótesis-solución
descripcion:
---

## Que es

## Que no es

## Como funciona

## Reglas generales


```

**Cuerpo mínimo para `estado: Activa`:** qué es y cómo funciona, qué no es, y opcionalmente alternativas cercanas.

### 1.2 Documento de Dominio (`01_Product/Dominios/<dominio>.md`)

```md
---
tipo: dominio
dominio: "<nombre>"
estado: Propuesto    # Propuesto | En Delimitación | Delimitado
vision_origen: VA-001
descripcion: "<qué sostiene, en una línea>"
---

## Qué es
desarrollo del pilar.

## Qué no cubre
— lista.

## Features prerequeridas 
— lista.

Reglas y restricciones
— lista.
```

### 4.3 Decisión de Arquitectura (`03_Architecture/ADR-XXX.md`)

```yaml
---
tipo: adr
id: ADR-XXX
status: Propuesto          # Propuesto | Aceptado | Superado
fecha: YYYY-MM-DD
vision_origen: VA-XXX
dominio: "Nombre del pilar"  # obligatorio; enlaza al documento de Dominio si existe
reemplaza: ADR-000
superado_por:
requisitos_derivados:
  - REQ-XXX
rama: "adr/ADR-XXX-descripcion"
---
```

Cada ADR resuelve **paradigma y tecnología en el mismo documento**: su cuerpo abre con una sección de **Contexto** que argumenta la forma elegida (el método) antes de entrar en la decisión técnica concreta. Cuando ese contexto ya está delimitado en un documento de Dominio compartido, el ADR puede remitirse a él en vez de repetirlo.

### 4.4 Requisito (`02_Requirements/REQ-XXX.md`)

```yaml
---
tipo: requisito
id: REQ-XXX
status: Pendiente          # Pendiente | En Progreso | Aprobado | Deprecado
prioridad: Alta            # Crítica | Alta | Media | Baja
modulo: Core
origen: ADR-XXX
responsable: "@usuario"
sprint: "Sprint-03"
rama: "feature/REQ-XXX-descripcion-vX.Y"
---
```

**Estados:**

- **Pendiente:** refinado, listo para desarrollarse.
- **En Progreso:** hay un Issue/PR activo; pueden existir andamios de apoyo en el sprint.
- **Aprobado:** el PR fue fusionado en `main`, los criterios están verificados.
- **Deprecado:** cancelado o reemplazado; se mueve a `_Archive/` según la política de conservación.

### 4.5 Andamio (`04_Sprints/Sprint-XX/AND-XXX.md`)

```yaml
---
tipo: andamio
id: AND-XXX
requisito: REQ-XXX
decisiones:                 # ADR que informan el enfoque
  - ADR-XXX
---
```

Un andamio es el lienzo donde se deja escrita la deducción concreta que precede a construir una pieza de un REQ: _dado que existe este requisito, con estas decisiones relacionadas, se emplea tal enfoque_. No tiene ciclo de estados ni rama propia — vive y muere dentro del sprint que lo motivó. Una vez construido lo que guiaba, se elimina del vault (queda en el historial de Git, nunca se archiva).

### 4.6 Caso de Prueba (`05_Testing/TC-XXX.md`) (opcional)

```yaml
---
tipo: test-case
id: TC-XXX
status: Diseñado           # Diseñado | Automatizado | Ejecutado | Fallido
requisito: REQ-XXX
modulo: Core
---
```
