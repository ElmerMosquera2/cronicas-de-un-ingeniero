---
tipo: gobernanza
id: DOMER-AGNOSTICA
Estado: Borrador
version: 0.3
fecha: 2026-10-01
naturaleza: marco de gobernanza
---
# DOMER Agnóstica

## 1. Definición

DOMER es un marco de gobernanza para productos.

Su propósito es gobernar la evolución de un producto preservando el porqué de las decisiones que determinan su forma, de modo que puedan comprenderse, cuestionarse y modificarse con trazabilidad a medida que cambia el contexto.

DOMER es agnóstico al tipo de producto. Puede aplicarse a software, investigaciones, productos físicos, iniciativas culturales, procesos, servicios u otros productos cuya evolución dependa de decisiones.

El marco no determina qué producto debe construirse ni prescribe una disciplina particular para producirlo. Define una forma de organizar las decisiones que gobiernan su evolución y de conservar la relación entre el propósito, el contexto, las decisiones y aquello que finalmente se materializa.

DOMER puede utilizarse junto con otras metodologías. En un producto de software puede coexistir, por ejemplo, con Scrum, Kanban, XP u otra forma de organizar la producción. La metodología utilizada para producir el producto no constituye por sí misma la gobernanza DOMER.

---

## 2. Área de trabajo

El área de trabajo de DOMER es la gobernanza de las decisiones que condicionan la evolución de un producto.

Esto comprende:

- el propósito y los límites generales expresados por la Visión Activa;
    
- la delimitación de áreas de trabajo mediante dominios;
    
- los métodos adoptados para actuar dentro de esas áreas;
    
- las tecnologías, herramientas, técnicas o medios elegidos para materializar esos métodos;
    
- las decisiones que justifican esas elecciones;
    
- los requisitos derivados de dichas decisiones;
    
- la trazabilidad entre las decisiones y su materialización;
    
- la revisión de las decisiones cuando cambia el contexto.
    

DOMER no pretende gobernar todas las actividades que ocurren durante la producción.

Una actividad puede realizarse sin convertirse en un artefacto de gobernanza. El marco interviene cuando el conocimiento producido por esa actividad es relevante para comprender, mantener o modificar la forma en que el producto evoluciona.

Por esta razón, DOMER distingue entre producir y gobernar.

Producir consiste en transformar una intención, una necesidad o una decisión en un resultado.

Gobernar consiste en conservar y relacionar las razones que permiten decidir cómo debe evolucionar ese resultado.

---

## 3. La estructura conceptual

DOMER organiza la gobernanza mediante cuatro conceptos principales:

```text
                 VISIÓN ACTIVA
                       │
                       ▼
                   DOMINIOS
                       │
                       ▼
                     ADR
                       │
                       ▼
                     REQ
                       │
                       ▼
                MATERIALIZACIÓN
                       │
                       ▼
                   VALIDACIÓN
```

Esta relación representa una dirección de trazabilidad, no necesariamente una estructura física de carpetas ni un flujo de ejecución obligatorio.

### Visión Activa

La Visión Activa establece el marco general dentro del cual se gobierna el producto.

Define qué es el producto desde la perspectiva de gobernanza, cuál es el área que DOMER debe cubrir, qué límites deben respetarse y qué condiciones generales deben orientar las decisiones.

La Visión Activa puede abarcar, restringir o delimitar métodos y formas de trabajo cuando esas condiciones pertenecen a la definición general del producto.

La visión no necesita describir cada decisión. Su función es establecer el contexto dentro del cual esas decisiones tienen sentido.

### Dominio

Un dominio es una delimitación de un área de trabajo dentro de la gobernanza del producto.

Su propósito es separar contextos que pueden ser tratados de manera diferenciada y facilitar la trazabilidad de las decisiones que pertenecen a cada área.

Un dominio no constituye un nivel adicional de jerarquía entre documentos ni representa necesariamente una funcionalidad, un módulo o una parte física del producto.

El contenido de un dominio no está sujeto a una plantilla única. Puede expresarse mediante reglas, restricciones, principios, condiciones, definiciones, descripciones de funcionamiento, comportamientos esperados o una formulación más libre de aquello que debe quedar previsionado en ese ámbito.

Lo importante es que el dominio delimite el área que gobierna.

Como mínimo, un dominio debería permitir comprender:

- qué área se está delimitando;
    
- qué contexto le pertenece;
    
- qué queda dentro y fuera de su alcance;
    
- qué condiciones o comportamientos deben considerarse al tomar decisiones dentro de ella;
    
- qué parte del método queda determinada por esa delimitación.
    

El alcance forma parte del contenido del dominio. No constituye necesariamente un campo independiente ni un formato obligatorio.

Un dominio puede evolucionar cuando cambia la comprensión del área que delimita.

### ADR

Un ADR registra una decisión cuya razón debe preservarse para orientar la evolución posterior del producto.

En DOMER, el ADR reúne el método y la tecnología cuando ambos forman parte de la decisión que debe justificarse.

Por método se entiende la forma, procedimiento, paradigma, estrategia o enfoque mediante el cual se pretende actuar.

Por tecnología se entiende el medio concreto utilizado para materializar ese método, cuando dicha elección constituye parte de la decisión.

La relación puede expresarse así:

```text
método + tecnología + contexto + razón
                         ↓
                        ADR
```

El método debe quedar delimitado preferentemente en el dominio cuando ya constituye una condición del área de trabajo.

Cuando el método continúa siendo una cuestión abierta, depende del contexto o forma parte de aquello que debe ser evaluado, debe quedar registrado dentro del ADR junto con la tecnología adoptada.

Por tanto, el ADR no existe para describir una tecnología de manera aislada. Existe para conservar la decisión que establece una forma concreta de resolver algo y las razones que permiten comprender por qué esa forma fue adoptada.

La decisión puede cambiar.

Lo que DOMER preserva es el conocimiento necesario para comprender el cambio.

### REQ

Un REQ representa una condición que debe ser materializada en el producto como consecuencia de una necesidad o de una decisión gobernada.

El requisito permite conectar el plano de la decisión con el plano de la producción.

No toda observación se convierte inmediatamente en REQ. La formalización depende de que exista una necesidad concreta de producir, modificar o validar algo.

La relación típica es:

```text
ADR → REQ → materialización
```

Un REQ debe poder rastrearse hacia la decisión, contexto o necesidad que le dio origen y hacia el resultado que finalmente lo materializa.

---

## 4. El método y el dominio

DOMER diferencia entre lo que pertenece a la definición del área de trabajo y lo que todavía constituye una decisión sobre cómo actuar dentro de ella.

Cuando el método es una condición establecida por el dominio, el ADR no necesita volver a decidirlo.

Por ejemplo, un dominio puede establecer que determinada clase de información debe procesarse mediante una determinada estrategia. Esa condición forma parte del contexto del dominio.

Cuando, en cambio, existen varias formas posibles de proceder y la selección de una de ellas afecta la evolución del producto, la cuestión pertenece al ADR.

De esta manera:

```text
Dominio:
"En esta área el producto debe operar bajo determinadas condiciones."

ADR:
"Dadas esas condiciones, adoptamos esta forma concreta de resolverlo
con este medio, por estas razones."
```

Esta separación evita convertir cada ADR en una repetición del contexto y permite que varios ADR compartan una misma delimitación metodológica.

---

## 5. Cómo se usa

DOMER se utiliza cuando existe una necesidad de preservar el razonamiento que gobierna la evolución de un producto.

El punto de entrada puede ser una observación, experiencia, necesidad, cambio de contexto, problema, propuesta o cualquier otra información que pueda conducir a una decisión.

Ese material puede pasar por un proceso de análisis y planificación definido por el equipo.

Una implementación concreta puede adoptar un flujo como:

```text
crónica → inbox → planificación → decisión → REQ → implementación → validación
```

pero este flujo no constituye la definición completa de DOMER.

DOMER establece qué relaciones deben conservarse, mientras que la metodología utilizada para procesarlas puede variar.

Si durante el trabajo aparece una decisión relevante sobre el producto, esa decisión puede registrarse mediante un ADR.

Si la decisión produce una obligación concreta que debe materializarse, puede derivarse un REQ.

Si la producción genera evidencia sobre la validez de lo realizado, puede registrarse mediante los mecanismos de validación definidos por la instancia.

La implementación materializa el producto. No sustituye la decisión que la originó.

---

## 6. La trazabilidad

La trazabilidad de DOMER busca preservar el recorrido del razonamiento.

Una decisión debe poder relacionarse con el contexto que la hace comprensible y con aquello que produjo.

La dirección conceptual es:

```text
Visión
  ↓
Dominio
  ↓
Decisión
  ↓
Requisito
  ↓
Materialización
  ↓
Validación
```

La relación no implica que todos los elementos tengan que existir siempre.

Puede existir un dominio sin ADR.

Puede existir una decisión que no genere inmediatamente un REQ.

Puede existir un REQ cuya materialización ocurra mediante varias piezas de trabajo.

La trazabilidad tampoco exige registrar cada paso intermedio. El objetivo es conservar las relaciones que resultan necesarias para comprender el producto y modificarlo posteriormente.

---

## 7. Evolución de la gobernanza

La Visión Activa puede cambiar.

Los dominios pueden cambiar.

Los ADR pueden ser superados por nuevas decisiones.

Los requisitos pueden modificarse cuando cambian las decisiones de las que dependen.

Sin embargo, estos niveles no evolucionan necesariamente mediante el mismo ciclo.

La Visión Activa y los dominios representan la definición del espacio que DOMER gobierna. Cambiarlos constituye una modificación de la gobernanza.

Por ello, un cambio en la visión o en un dominio no debe producirse automáticamente como una consecuencia de:

```text
crónica → inbox → implementación
```

Ese ciclo puede revelar que la visión o el dominio necesitan cambiar, pero el cambio de gobernanza requiere su propia decisión y su propia trazabilidad.

La distinción es importante porque permite que DOMER gobierne su propio desarrollo.

Cuando DOMER está siendo formalizado, algunas decisiones pueden producir cambios en la propia definición del marco. Esto no constituye una contradicción. El marco puede utilizar sus principios para documentar y justificar

## Qué no es DOMER AGNOSTICO?

No es una metodología exclusiva de software.

No es una metodología de desarrollo, una técnica de gestión de proyectos ni un sistema de planificación por sí mismo.

No es una herramienta de documentación.

Git puede utilizarse para versionar y conservar el historial.

Obsidian puede utilizarse para navegar y editar el conocimiento.

Scrum puede utilizarse para organizar ciclos de producción.

No sustituye la implementación del producto.

No determina automáticamente qué decisión debe tomarse.

No exige documentar todas las actividades realizadas.

No considera permanentes las decisiones registradas.

No convierte la documentación en una representación equivalente al producto real.

## DOMER y otras metodologías

DOMER puede coexistir con metodologías de producción y gestión.

Por ejemplo, Scrum puede organizar la planificación y ejecución mediante Product Backlog, Sprint y revisión. DOMER puede encargarse de preservar el contexto y las decisiones que justifican aquello que se incorpora, modifica o descarta dentro de esos ciclos.

La metodología de producción determina cómo se organiza el trabajo.

DOMER determina cómo se conserva el razonamiento de las decisiones que gobiernan ese trabajo.

La misma instancia puede utilizar otra metodología sin cambiar necesariamente su Visión Activa ni sus dominios.