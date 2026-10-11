---
tipo: dominio
dominios: Estructura del repositorio
estado: En delimitacion
vision_origen: VA-001-domer-agnostico
descripcion: Delimitar los espacios de trabajo
---

# [DOM-001] Estructura del repositorio

## Qué es

La estructura del repositorio establece dónde reside cada tipo de información dentro del producto y qué función cumple cada espacio.

El repositorio se organiza para distinguir entre:

- conocimiento de gobernanza;
    
- entradas pendientes de procesamiento;
    
- decisiones;
    
- elementos de trabajo;
    
- validaciones;
    
- ciclos de planeación;
    
- material de trabajo;
    
- productos formales;
    
- notas y experiencias sin procesar.
    

La estructura busca que la ubicación de un archivo aporte contexto sobre su propósito sin convertir la organización del repositorio en una descripción del contenido interno del producto.

Esta estructura pertenece al dominio de gobernanza porque determina cómo se conserva y relaciona la información necesaria para comprender y modificar el producto.

## 2. Estructura

La estructura base es:

```text
_docs_[nombre-proyecto]/
├── inbox/                # Entradas a procesamiento, pre-planning
├── vision/
│   ├── dominios/         # Dominios de la visión
│   └── va.md             # Visión Activa
├── req/                  # Elementos de trabajo
├── adr/                  # Decisiones de arquitectura
├── test/                 # Validaciones de producto, integración y funcionamiento
└── sprints/              # Ciclos de planeación

desk/                     # Mesa de trabajo
build/                    # Productos formales (espacio de despliege)
cronicas/                 # Notas crudas, bitácoras y experiencias sin procesar

README.md                 # Estándar Git
CHANGELOG.md              # Estándar Git
```

La estructura puede implementarse físicamente de otra manera cuando el contexto del producto lo requiera, pero la separación conceptual entre estos espacios debe conservarse.

## 3. Espacios de gobernanza

### `_docs_[nombre-proyecto]/`

Contiene la documentación formal utilizada para gobernar el producto.

Su contenido representa conocimiento que ha pasado por un proceso de formalización suficiente para participar en la trazabilidad del producto.

No debe utilizarse como área general de trabajo ni como depósito de material provisional.

### `inbox/`

Contiene entradas formales que todavía requieren procesamiento.

Una entrada en `inbox/` puede representar una necesidad, observación, problema, propuesta o información que aún no tiene una clasificación definitiva dentro de DOMER.

`inbox/` funciona como punto de entrada al trabajo de pre-planning. No constituye por sí mismo una decisión ni un requisito.

El procesamiento de una entrada determina si debe convertirse en otro artefacto, descartarse, consolidarse o permanecer como información pendiente.

### `vision/`

Contiene los elementos que establecen el marco conceptual y de gobernanza del producto.

Dentro de este espacio:

```text
vision/
├── dominios/
└── va.md
```

`va.md` contiene la Visión Activa.

`dominios/` contiene las delimitaciones conceptuales que organizan áreas de decisión de la visión.

Los dominios no constituyen un paso obligatorio dentro de la trazabilidad. Su finalidad es proporcionar contexto común a decisiones relacionadas.

### `req/`

Contiene los elementos de trabajo que representan aquello que debe ser materializado, modificado o validado en el producto.

Un REQ debe poder relacionarse con el contexto que justifica su existencia y, cuando corresponda, con la decisión de la que se deriva.

`req/` no debe utilizarse para almacenar decisiones cuyo resultado todavía no se ha convertido en un elemento de trabajo.

### `adr/`

Contiene las decisiones de arquitectura.

Un ADR registra una decisión consciente cuya forma puede necesitar ser comprendida, cuestionada o sustituida en el futuro.

Cuando la decisión involucra conjuntamente un método y una tecnología, ambos forman parte del ADR. El dominio puede establecer o delimitar previamente el método cuando este ya forma parte del contexto aceptado. Cuando el método todavía constituye una decisión abierta, el ADR debe conservar el razonamiento que llevó a adoptarlo.

El ADR conserva el porqué de una forma adoptada, no solamente su descripción.

### `test/`

Contiene las validaciones necesarias para determinar si el producto satisface aquello que debe cumplir.

Su función no es almacenar evidencia arbitraria del trabajo, sino conservar los mecanismos o resultados formales mediante los cuales se verifica el producto.

El contenido de `test/` debe poder relacionarse con los elementos de trabajo que pretende validar cuando esa relación sea relevante para la trazabilidad.

### `sprints/`

Contiene la información asociada a los ciclos de planeación.

Una planificación organiza trabajo existente y no constituye, por sí misma, una nueva decisión de arquitectura.

Por esta razón, `sprints/` no reemplaza `req/` ni `adr/`. Un sprint puede seleccionar y ordenar elementos ya formalizados, pero no debe convertirse en el origen permanente de su significado.

## 4. Espacios de trabajo

Los espacios situados fuera de `_docs_[nombre-proyecto]/` cumplen funciones diferentes.

### `desk/`

Es la mesa de trabajo.

Contiene borradores, experimentos, pruebas temporales, materiales auxiliares y otros elementos utilizados durante la elaboración de trabajo.

Un archivo en `desk/` no adquiere carácter formal por existir allí.

El contenido de `desk/` puede transformarse posteriormente en documentación, requisitos, decisiones, pruebas o productos, pero su estado inicial es de trabajo.

### `build/`

Es el espacio destinado a productos formales producidos a partir de la información gobernada.

Puede contener artefactos generados, compilados, exportados, empaquetados o preparados para distribución.

`build/` representa un resultado. No es la fuente de las decisiones que explican cómo fue producido.

Cuando un producto formal necesita ser corregido o actualizado, el cambio debe realizarse desde sus fuentes correspondientes y posteriormente producir una nueva versión.

### `cronicas/`

Contiene notas crudas, bitácoras, experiencias y observaciones sin procesar.

Una crónica puede servir como fuente de información para una futura decisión, requisito o modificación del producto, pero su existencia no implica que aquello que contiene haya sido adoptado como criterio de gobernanza.

`cronicas/` conserva el registro de la experiencia sin exigir que toda observación se transforme inmediatamente en conocimiento formal.

## 5. Archivos de estándar del repositorio

`README.md` y `CHANGELOG.md` corresponden a convenciones del repositorio y no forman parte de la trazabilidad específica de DOMER.

Pueden describir el proyecto, su forma de uso o la evolución de sus versiones, pero no sustituyen a la Visión Activa, los dominios, los ADR ni los REQ.

## 6. Principio de separación

La estructura distingue cuatro estados de la información:

```text
experiencia
    ↓
cronicas / desk
    ↓
procesamiento
    ↓
inbox
    ↓
formalización
    ├── vision
    ├── adr
    └── req
    ↓
planeación y validación
    ├── sprints
    └── test
    ↓
producto formal
    └── build
```

Este esquema representa una relación funcional, no una obligación de que todo archivo atraviese cada directorio.

Por ejemplo, una experiencia puede no producir ningún artefacto formal. Un REQ puede derivarse directamente de una decisión existente. Un ADR puede surgir de una necesidad detectada durante el trabajo. Un elemento en `build/` puede generarse repetidamente a partir de fuentes ya existentes.

La ubicación expresa el estado y propósito del artefacto, no necesariamente su origen temporal.

## 7. Relación con la Visión Activa

La Visión Activa determina el propósito general de esta estructura y sus límites.

Este dominio concreta ese propósito en una organización física del repositorio.

La VA establece qué debe preservarse de la gobernanza. Este dominio establece dónde se conserva cada clase de información necesaria para hacerlo.

Por ello, un cambio en la estructura del repositorio puede requerir una modificación de este dominio sin que necesariamente implique modificar la Visión Activa.

## 8. Relación con los ADR

La existencia de esta estructura es una decisión de gobernanza del producto, pero sus detalles pueden requerir ADR cuando existan alternativas relevantes o cuando una decisión dependa de tecnología, restricciones concretas o criterios que puedan cambiar.

Por ejemplo, este dominio puede establecer que existe un espacio formal para decisiones. Un ADR podría determinar posteriormente cómo esas decisiones se identifican, versionan, automatizan o integran con una herramienta concreta.

El dominio establece el método organizativo general. El ADR conserva las decisiones particulares sobre cómo implementarlo cuando dichas decisiones son susceptibles de revisión.

## 9. Evolución

La estructura puede evolucionar.

Pueden añadirse, eliminarse, fusionarse o dividirse espacios cuando cambien las necesidades de gobernanza del producto.

Estos cambios no deben producirse como una consecuencia mecánica del ciclo:

```text
crónica → inbox → implementación
```

Cambiar la estructura del repositorio cambia la forma en que el producto conserva y relaciona su conocimiento. Por ello, debe tratarse como una modificación de la gobernanza y quedar justificado por separado.

Cuando la estructura cambie, deben revisarse las referencias afectadas y conservarse la trazabilidad suficiente para comprender qué estructura existía anteriormente y por qué fue modificada.

## 10. Límites

Este dominio no define:

- el contenido específico de una Visión Activa;
    
- el contenido de cada dominio;
    
- la metodología completa de trabajo del producto;
    
- la tecnología utilizada para alojar el repositorio;
    
- el sistema de control de versiones;
    
- las reglas internas de cada artefacto;
    
- el contenido de los productos generados.
    

Este dominio define dónde y con qué propósito se organiza la información.

La tecnología utilizada para materializar esta estructura puede ser objeto de decisiones independientes cuando constituya una elección relevante.

## 11. Criterio de conservación

La estructura debe facilitar que una persona pueda localizar:

1. qué se pretende gobernar;
    
2. qué decisiones se han tomado;
    
3. qué trabajo se deriva de ellas;
    
4. cómo se valida el resultado;
    
5. qué se produjo finalmente;
    
6. qué experiencias dieron origen a cambios o nuevas decisiones.
    

La organización física del repositorio se considera correcta cuando ayuda a conservar estas relaciones sin exigir que cada actividad o documento sea formalizado innecesariamente.