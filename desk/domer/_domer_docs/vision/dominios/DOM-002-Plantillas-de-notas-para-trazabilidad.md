---
Estado: Activo
Dominio: Plantillas de notas para trazabilidad
Propósito: Establecer los formatos de los artefactos que requieren una estructura documental común para garantizar su identificación y trazabilidad dentro de DOMER
---
# [DOM-002] Plantillas de notas para trazabilidad

**Propósito:** Establecer los formatos de los artefactos que requieren una estructura documental común para garantizar su identificación y trazabilidad dentro de DOMER.

## Qué es

Las plantillas son los formatos de referencia utilizados para crear notas formales de DOMER.

Definen la estructura documental necesaria para identificar un artefacto, registrar la información que le corresponde y establecer las relaciones que permitan seguir su trazabilidad.

Una plantilla pertenece al tipo de artefacto que representa. No define el contenido conceptual de ese artefacto.

Las plantillas se mantienen como una referencia común para evitar que un mismo tipo de artefacto adopte estructuras incompatibles dentro de un mismo producto.

## Área de trabajo

El área de trabajo de este dominio es la estructura documental de los artefactos formales de DOMER que requieren un formato común para su identificación, registro y trazabilidad.

## Alcance

Este dominio regula las plantillas utilizadas por los artefactos formales que forman parte del sistema de trazabilidad.

Comprende la estructura, los metadatos y las relaciones documentales que permiten reconocer cada tipo de artefacto.

No regula el contenido de las decisiones, requisitos, validaciones ni demás conocimientos que esos artefactos contienen.

Tampoco establece una plantilla rígida para los dominios.

## Método

Cada tipo de artefacto que requiera una estructura documental común utiliza una plantilla definida para ese tipo.

La plantilla establece la forma mínima y común del artefacto.

El contenido se desarrolla dentro de esa estructura de acuerdo con la naturaleza del artefacto y con las definiciones establecidas por la Visión Activa y los dominios correspondientes.

La plantilla no determina qué debe decidirse, qué requisito debe formularse ni qué solución debe adoptarse.

## Plantillas

Las plantillas formales se mantienen en un espacio común:

```text
_docs_[nombre-proyecto]/
└── plantillas/
```

Las plantillas corresponden a los artefactos que requieren formato común, por ejemplo:

```text
plantillas/
├── va.md
├── adr.md
├── req.md
├── test.md
└── sprint.md
```

Cada plantilla corresponde al artefacto que representa:

```text
va.md      → Visión Activa
adr.md     → Decisión de Arquitectura
req.md     → Requisito
test.md    → Validación
sprint.md  → Sprint
```

La plantilla del artefacto debe poder establecer los elementos necesarios para identificarlo y relacionarlo con los demás artefactos de la trazabilidad.

## Dominios

Los dominios no están sujetos a una plantilla de contenido.

Un dominio puede expresarse mediante párrafos, reglas, listas, criterios, relaciones, descripciones funcionales, principios u otras estructuras apropiadas para delimitar su área de trabajo.

Los aspectos que un dominio debe establecer pertenecen a su contenido y no a un formato documental obligatorio.

Un dominio debe poder delimitar, de acuerdo con su naturaleza, aspectos como su propósito, área de trabajo, alcance, método, restricciones, invariantes y relación con la Visión Activa, pero puede hacerlo con la estructura que resulte adecuada para explicar ese dominio.

Por tanto, la plantilla de dominio no establece una secuencia obligatoria de secciones ni convierte esos aspectos en campos formales.

## Trazabilidad

Las plantillas permiten que los artefactos puedan mantener relaciones explícitas entre sí.

La estructura documental debe permitir identificar el artefacto, conocer su tipo y registrar las relaciones que correspondan.

La trazabilidad general de DOMER se expresa mediante las relaciones entre:

```text
Visión
   ↓
Dominio
   ↓
ADR
   ↓
REQ
   ↓
TEST
```

El dominio aporta contexto al área de decisión, pero no constituye obligatoriamente un nivel de la relación entre todos los artefactos.

La plantilla facilita registrar las relaciones. No determina el significado de dichas relaciones.

## Restricciones

Las plantillas son únicas para cada tipo de artefacto dentro del producto.

Un artefacto formal debe utilizar la plantilla correspondiente a su tipo.

Las plantillas no deben contener decisiones particulares del producto.

Las plantillas no deben utilizarse para imponer estructura documental a los dominios.

Una modificación de una plantilla no modifica por sí misma el contenido ni el significado de los artefactos existentes.

Cuando una modificación de plantilla afecte información necesaria para interpretar o relacionar artefactos existentes, el cambio debe conservar la trazabilidad correspondiente.

## Qué no es

Este dominio no define:

- el contenido de los artefactos;
- la metodología de trabajo del producto;
- las decisiones de arquitectura;
- los requisitos;
- las reglas particulares de un dominio;
- la tecnología utilizada para implementar las plantillas.

El dominio define el formato de los artefactos que requieren una estructura común.

## Regla central

La plantilla define cómo se registra un artefacto.

El dominio define qué debe comprenderse y establecerse dentro de un área de trabajo.

El ADR define una decisión concreta.

El requisito define aquello que debe materializarse como consecuencia de una decisión.

Por tanto, la plantilla no debe convertirse en una segunda capa de gobernanza ni utilizarse para imponer una forma única de expresar el conocimiento de los dominios.