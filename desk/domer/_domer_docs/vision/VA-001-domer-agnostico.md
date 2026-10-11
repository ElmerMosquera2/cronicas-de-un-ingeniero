---
tipo: vision
id: VA-001
status: Activa
naturaleza: Marco de gobernanza
descripcion: Marco de gobernanza de productos que estan en desarrollo o requieren evolucion constante.
---
# [VA-001] DOMER como marco de gobernanza de productos

## 1. Qué es

DOMER es un delimitador conceptual de decisiones. Su funcion principal es evolutiva; dado un producto visonado; establecer una forma delimitante que debe mantenerse y escalar sin perder la razón por la que fue concebido, en forma de las decisiones que determinaron su forma y los criterios que permiten comprender o cuestionar esas decisiones con el paso del tiempo.

DOMER parte de una idea sencilla: un producto surge de decisiones y cambia por las decisiones que se toman sobre él. El proceso de desarrollo, manenimiento y actualizacion tiene a ramificarose en versiones conseptualmente distiferente.

El marco es agnóstico al tipo de producto. Un producto puede ser software, una investigación, un producto físico, una iniciativa cultural, un proceso, una obra o cualquier otra cosa cuya evolución ramifica una eleccion entre aternativas.

## 2. Cómo funciona

> Damos por cierto que el producido esta sugeto a un propósito, los _subobjetivos_, las reglas, los metodos y las tecnologías asociadas que le materializan.

La visión define qué es el producto, su alcance, su objetivo general (expresion inspirada en las capas de abstaccion)  y su objetivos especificos.

Los dominios expresan una delimitador que puede abstraerse o agruparse en terminos comprensibles. 

Los adr (nombre inspirado en desiciones de arquitectura) no guardan solo informacion de las tecnologias sino que en su contexto expresan el conjunto de metodos aspciados el CRUD de los componentes del insumo, producto o servicio.

> CRUD de los componentes comprende un producto como un cumulo de funciones producibles, o como sub productos sujetos a los procesos tradicionales en una base de datos.

Separa la gobernanza del producto de su ejecución.

La Visión Activa establece el marco dentro del cual se toman decisiones. Los dominios delimitan partes de ese marco cuando conviene tratarlas de manera independiente. Los ADR registran las decisiones que fijan una forma de resolver algo, junto con el razonamiento que permite comprenderla. Los REQ convierten esas decisiones en unidades trazables de trabajo o de valor.

El ciclo operativo del trabajo puede utilizar mecanismos como Crónica, Inbox e implementación para capturar observaciones, desarrollar ideas y materializar decisiones. Ese ciclo sirve para hacer evolucionar el producto.

La Visión Activa y los dominios pertenecen a otro nivel. Pueden cambiar, pero su modificación no ocurre como consecuencia automática del ciclo Crónica → Inbox → implementación. Cambiar la visión o delimitar nuevamente un dominio constituye una decisión sobre la propia gobernanza del producto. Debe tratarse y versionarse como tal.

Esto permite que una implementación revele la necesidad de cambiar la visión o un dominio sin convertir automáticamente ese hallazgo en una modificación del marco. Primero se identifica la necesidad de cambio en la gobernanza; después se modifica la gobernanza y se ajusta la trazabilidad que dependa de ella.

DOMER puede utilizarse para gobernar su propia evolución. Esto introduce una relación recursiva deliberada: el marco puede documentar y preservar las razones de sus propios cambios. Sin embargo, gobernar DOMER no significa que sus reglas fundamentales deban pasar por el mismo flujo operativo que gobierna el producto. La evolución del marco pertenece a su propia capa de gobernanza.

### 2.1 Conserva la trazabilidad

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

## 3. Qué no es

DOMER no es una metodología exclusiva para desarrollar software.

No es un lenguaje de programación, un patrón arquitectónico, una metodología de gestión de proyectos ni un proceso obligatorio para ejecutar todas las actividades de un equipo.

Tampoco pretende documentarlo todo. Una actividad, una discusión o una modificación no necesita convertirse en un artefacto permanente solo por haber ocurrido. La persistencia se justifica cuando conservar el razonamiento aporta valor para comprender, mantener o modificar el producto posteriormente.

DOMER tampoco determina por sí mismo qué decisión debe tomarse. El marco conserva y relaciona las razones de las decisiones, pero la decisión pertenece a quienes gobiernan el producto.

Finalmente, DOMER no considera inmutables la visión, los dominios ni los ADR. Todos representan conocimiento situado en un contexto. Pueden revisarse cuando cambia aquello que los justificaba. Lo que debe conservarse es la capacidad de comprender cómo y por qué ocurrió ese cambio.

## 4. Alternativas

DOMER puede sustituirse o complementarse con otros mecanismos de gestión del conocimiento y de las decisiones.

Un equipo puede utilizar documentación convencional, registros de decisiones independientes, ADR tradicionales, documentos de diseño, sistemas de gestión de requisitos, wikis o herramientas de gestión de proyectos. Cada alternativa puede cubrir una parte del problema.

La particularidad de DOMER está en organizar esas piezas alrededor de una relación de trazabilidad que parte de una visión, permite delimitar dominios, registra decisiones y conecta esas decisiones con aquello que finalmente debe materializarse.

DOMER tampoco obliga a utilizar Obsidian, GitHub o una herramienta concreta. Esas herramientas son medios para implementar el marco. El principio de gobernanza permanece aunque cambie la herramienta.

## 5. Resultado esperado

Mecanismo de producción y evolución de un producto trazable y delimitado.