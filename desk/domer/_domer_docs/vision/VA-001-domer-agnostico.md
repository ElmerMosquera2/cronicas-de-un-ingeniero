---
tipo: vision
id: VA-001
status: Activa
naturaleza: Marco de gobernanza
---
# [VA-001] DOMER como marco de gobernanza de productos

## 1. Qué es

DOMER es un marco de gobernanza para productos. Su propósito es permitir que un producto pueda mantenerse y escalar sin perder la razón por la que fue concebido, las decisiones que determinaron su forma y los criterios que permiten comprender o cuestionar esas decisiones con el paso del tiempo.

DOMER parte de una idea sencilla: un producto cambia porque las personas toman decisiones sobre él. Algunas de esas decisiones pierden importancia con el tiempo, pero otras condicionan su evolución durante meses o años. Cuando el razonamiento que las originó desaparece, quien modifica el producto debe reconstruirlo a partir de sus consecuencias. DOMER busca conservar ese razonamiento y relacionarlo con lo que finalmente se construyó, realizó o produjo.

El marco es agnóstico al tipo de producto. Un producto puede ser software, una investigación, un producto físico, una iniciativa cultural, un proceso, una obra o cualquier otra cosa cuya evolución dependa de decisiones deliberadas. DOMER no define qué debe producirse ni prescribe una disciplina particular para hacerlo. Gobierna el espacio de decisiones que determina cómo un producto puede existir, evolucionar y ser mantenido.

### Área de trabajo

El área de trabajo de DOMER es la gobernanza de las decisiones que condicionan la evolución de un producto.

Esto comprende el propósito y los límites que establece la Visión Activa, los dominios que permiten delimitar áreas de decisión, los métodos y tecnologías adoptados mediante decisiones, los requisitos que materializan esas decisiones y la trazabilidad entre ellas.

DOMER no pretende gobernar cada actividad que ocurre durante la producción. Su objeto es conservar el conocimiento necesario para comprender por qué el producto tiene la forma que tiene y qué tendría que reconsiderarse antes de modificarla.

## 2. Cómo se usa

DOMER comienza estableciendo una Visión Activa. La visión define qué es el producto desde la perspectiva de gobernanza, cuál es su área de trabajo y qué límites deben respetarse al tomar decisiones sobre él.

Cuando una parte de esa visión requiere un tratamiento más preciso, puede delimitarse mediante un dominio. El dominio representa un área conceptual del producto que puede sostener varias decisiones. No constituye por sí mismo una decisión ni agrega otro nivel obligatorio a la jerarquía de trazabilidad. Su función es establecer un contexto común para las decisiones que pertenecen a una misma área.

Cuando debe decidirse una forma concreta de resolver algo, se registra un ADR. En DOMER, una decisión de arquitectura reúne el método y la tecnología cuando ambos forman parte de aquello que debe ser decidido, cuestionado y comprendido posteriormente.

Siempre que sea posible, el método se delimita en el dominio. La Visión Activa puede abarcarlo, restringirlo o establecer las condiciones dentro de las cuales puede utilizarse. Cuando el método todavía constituye una cuestión abierta, depende de un contexto particular o debe justificarse junto con una tecnología concreta, forma parte del ADR. De esta manera, el ADR conserva la explicación necesaria para entender por qué se adoptó determinada forma y permite justificar una futura revisión de la decisión.

De las decisiones aceptadas pueden derivarse requisitos. El requisito representa aquello que debe materializarse en el producto y permite llevar la trazabilidad desde la decisión hasta su implementación o resultado.

La relación fundamental es:

Visión Activa → Dominio → ADR → REQ → implementación

El dominio no es un paso obligatorio entre la visión y el ADR. Es una delimitación que aparece cuando resulta útil para separar áreas de decisión y evitar que un mismo contexto tenga que repetirse en múltiples ADR.

La trazabilidad no pretende registrar cada acción realizada. Pretende que una decisión relevante pueda recorrerse hacia atrás hasta comprender su origen y hacia adelante hasta identificar aquello que produjo.

## 3. Cómo funciona

DOMER separa la gobernanza del producto de su ejecución.

La Visión Activa establece el marco dentro del cual se toman decisiones. Los dominios delimitan partes de ese marco cuando conviene tratarlas de manera independiente. Los ADR registran las decisiones que fijan una forma de resolver algo, junto con el razonamiento que permite comprenderla. Los REQ convierten esas decisiones en unidades trazables de trabajo o de valor.

El ciclo operativo del trabajo puede utilizar mecanismos como Crónica, Inbox e implementación para capturar observaciones, desarrollar ideas y materializar decisiones. Ese ciclo sirve para hacer evolucionar el producto.

La Visión Activa y los dominios pertenecen a otro nivel. Pueden cambiar, pero su modificación no ocurre como consecuencia automática del ciclo Crónica → Inbox → implementación. Cambiar la visión o delimitar nuevamente un dominio constituye una decisión sobre la propia gobernanza del producto. Debe tratarse y versionarse como tal.

Esto permite que una implementación revele la necesidad de cambiar la visión o un dominio sin convertir automáticamente ese hallazgo en una modificación del marco. Primero se identifica la necesidad de cambio en la gobernanza; después se modifica la gobernanza y se ajusta la trazabilidad que dependa de ella.

DOMER puede utilizarse para gobernar su propia evolución. Esto introduce una relación recursiva deliberada: el marco puede documentar y preservar las razones de sus propios cambios. Sin embargo, gobernar DOMER no significa que sus reglas fundamentales deban pasar por el mismo flujo operativo que gobierna el producto. La evolución del marco pertenece a su propia capa de gobernanza.

## 4. Qué conserva la trazabilidad

DOMER prioriza el porqué sobre la descripción exhaustiva del producto.

La documentación debe permitir responder, al menos, estas preguntas:

- Qué se pretende preservar o conseguir.
    
- Dentro de qué límites puede evolucionar el producto.
    
- En qué área de decisión se encuentra un problema.
    
- Qué forma se decidió adoptar.
    
- Por qué esa forma fue aceptable en ese contexto.
    
- Qué requisitos se derivaron de la decisión.
    
- Qué parte del producto materializó esos requisitos.
    
- Qué decisión anterior tendría que revisarse si cambia el contexto.
    

La implementación sigue siendo la fuente del estado real del producto. DOMER no sustituye esa realidad por documentación. La documentación conserva el razonamiento que no puede recuperarse simplemente observando el resultado.

## 5. Qué no es

DOMER no es una metodología exclusiva para desarrollar software.

No es un lenguaje de programación, un patrón arquitectónico, una metodología de gestión de proyectos ni un proceso obligatorio para ejecutar todas las actividades de un equipo.

Tampoco pretende documentarlo todo. Una actividad, una discusión o una modificación no necesita convertirse en un artefacto permanente solo por haber ocurrido. La persistencia se justifica cuando conservar el razonamiento aporta valor para comprender, mantener o modificar el producto posteriormente.

DOMER tampoco determina por sí mismo qué decisión debe tomarse. El marco conserva y relaciona las razones de las decisiones, pero la decisión pertenece a quienes gobiernan el producto.

Finalmente, DOMER no considera inmutables la visión, los dominios ni los ADR. Todos representan conocimiento situado en un contexto. Pueden revisarse cuando cambia aquello que los justificaba. Lo que debe conservarse es la capacidad de comprender cómo y por qué ocurrió ese cambio.

## 6. Visión, dominios y decisiones

La Visión Activa define el espacio de decisión del producto. Establece qué se considera dentro del ámbito gobernado por DOMER y qué condiciones generales deben respetarse.

Un dominio delimita una parte de ese espacio cuando varias decisiones necesitan compartir un mismo contexto. Por ello, un dominio debe responder qué representa dentro del producto y qué queda fuera de él.

Un ADR registra una decisión concreta. Su contenido combina la forma adoptada con la tecnología cuando ambas constituyen parte de la decisión. El método puede estar previamente delimitado por un dominio; en ese caso, el ADR puede apoyarse en ese contexto en lugar de repetirlo. Cuando el método aún es materia de decisión, debe formar parte del razonamiento del ADR.

Esta separación evita confundir tres preguntas distintas:

1. Qué permite o restringe la visión.
    
2. Dentro de qué área conceptual se encuentra una decisión.
    
3. Qué forma concreta se adopta y por qué.
    

## 7. Evolución

La Visión Activa puede cambiar cuando cambia la comprensión del producto, su propósito o los límites dentro de los cuales debe evolucionar.

Los dominios también pueden cambiar cuando cambia la forma en que se entiende un área de decisión. Su modificación no requiere que el dominio siga un ciclo de implementación, porque un dominio no es una funcionalidad del producto.

Los ADR pueden ser superados cuando una decisión deja de ser válida para el contexto actual. La existencia de un nuevo ADR no elimina la necesidad de conservar el anterior: el conocimiento histórico permite comprender por qué el producto llegó a su estado actual y qué cambió para llegar allí.

Por tanto, DOMER distingue entre evolucionar el producto y evolucionar el marco que gobierna el producto. Ambos procesos pueden relacionarse, pero no son el mismo proceso.

## 8. Alternativas

DOMER puede sustituirse o complementarse con otros mecanismos de gestión del conocimiento y de las decisiones.

Un equipo puede utilizar documentación convencional, registros de decisiones independientes, ADR tradicionales, documentos de diseño, sistemas de gestión de requisitos, wikis o herramientas de gestión de proyectos. Cada alternativa puede cubrir una parte del problema.

La particularidad de DOMER está en organizar esas piezas alrededor de una relación de trazabilidad que parte de una visión, permite delimitar dominios, registra decisiones y conecta esas decisiones con aquello que finalmente debe materializarse.

DOMER tampoco obliga a utilizar Obsidian, GitHub o una herramienta concreta. Esas herramientas son medios para implementar el marco. El principio de gobernanza permanece aunque cambie la herramienta.

## 9. Resultado esperado

Un producto gobernado con DOMER debe permitir que una persona que no participó en una decisión pueda reconstruir su razón sin depender exclusivamente de quienes la tomaron.

La finalidad no es producir más documentación. Es reducir la cantidad de conocimiento necesario que queda únicamente en la memoria de las personas y facilitar que las modificaciones futuras puedan partir de decisiones comprendidas, cuestionadas y trazables.