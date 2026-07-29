---
name: vision-activa
description: Ayuda a pulir una intención cruda de producto (una idea sin refinar) hasta convertirla en el contenido de una Visión Activa (VA), siguiendo el Manual de Gobernanza de Documentación (GOV-001). Organiza el texto del usuario en las secciones "Qué es y cómo se usa", "Lo que no es" y "Alternativas cercanas", y señala cuando el usuario mezcla contenido propio de un MDR o ADR (decisiones de forma o tecnología) dentro de la Visión. Usar esta skill siempre que el usuario comparta una idea, intención o visión de producto en bruto y pida "pulir", "refinar", "delimitar", "estructurar" o "convertir en Visión Activa" esa idea, o mencione VA, "Visión Activa" o el marco de gobernanza GOV-001 — incluso si no lo pide explícitamente con esas palabras y solo describe una idea de producto pidiendo ayuda para aterrizarla.
---

# Pulir Visión Activa (VA)

Esta skill toma una intención cruda de producto y la pule hasta darle la forma de una Visión Activa (VA), según el Manual de Gobernanza `GOV-001` (ver `references/GOV-DOMER-SOFTWARE-001.md` para el manual completo — consúltalo si necesitas repasar las reglas de frontmatter, DoR/DoD o el resto del sistema).

## Alcance: qué SÍ hace y qué NO hace

**Sí hace:**
- Toma el texto crudo del usuario y lo organiza en las tres secciones del cuerpo mínimo de una VA (sección 4.1 / 5.1 del manual): **Qué es y cómo se usa**, **Lo que no es**, **Alternativas cercanas**.
- Pule la redacción de lo que el usuario ya dijo: clarifica, ordena, elimina ambigüedad — sin cambiar el sentido.
- Detecta y señala fragmentos que en realidad son contenido de MDR/ADR (ver "Distinguir VA de MDR/ADR" abajo).
- Detecta secciones débiles o vacías y hace preguntas puntuales para que el usuario mismo las complete.
- **Investiga activamente alternativas reales** (búsqueda web) para la sección "Alternativas cercanas" y propone una diferenciación tentativa a modo de borrador — esta es la única sección donde la skill sí genera contenido propio, porque el encargo explícito es "facilitar la investigación preliminar de alternativas" (ver detalle abajo).

**No hace (por diseño, no lo intentes aunque el usuario insista en que "solo lo hagas"):**
- No crea ningún archivo ni Markdown descargable. El resultado vive en el chat.
- No asigna el `VA-XXX` — el ID lo decide y lo escribe el usuario en su vault.
- No inventa ni completa contenido de **"Qué es y cómo se usa"** ni **"Lo que no es"** que el usuario no ha dado. Si falta algo ahí, se marca y se pregunta — nunca se rellena con una suposición de la skill. (La única excepción a esta regla de no inventar es "Alternativas cercanas" — ver más abajo.)
- No redacta MDR ni ADR. Solo etiqueta el fragmento como perteneciente a ese territorio; mover o desarrollar ese contenido es trabajo de otra skill/flujo.
- No decide ni escribe el frontmatter (`status`, `naturaleza`, `alternativas_evaluadas`) — eso es responsabilidad de quien gestiona el archivo real.

## Alternativas cercanas: la excepción que sí investiga

A diferencia de "Qué es" y "Lo que no es", esta sección **siempre requiere una búsqueda web real** antes de presentarla al usuario — no basta con preguntar "¿conoces alternativas?". Esto aplica tanto si el usuario ya mencionó alguna alternativa como si no dijo nada al respecto.

Proceso para esta sección:
1. A partir de la necesidad ya identificada en "Qué es" (no de la forma de solución, si la distinguiste como MDR), busca en la web herramientas, productos o proyectos existentes que resuelvan algo parecido.
2. Selecciona un puñado de candidatos concretos y reales (nombres propios, no categorías genéricas) — prioriza los más cercanos conceptualmente, no una lista exhaustiva.
3. Para cada candidato, o para el conjunto, **propón una diferenciación tentativa** — un borrador de en qué se parece y en qué podría diferenciarse la idea del usuario, basado en lo que ya sabes de su intención. Dila explícitamente como borrador ("Tentativo, corrígeme:"), nunca como un hecho ya asentado — el usuario es quien decide la diferenciación real.
4. Si algún candidato encontrado es tan cercano que la propia forma de solución (MDR) del usuario parece coincidir con él, dilo sin filtro — es información valiosa aunque incómoda.
5. El usuario corrige, confirma o descarta el borrador; tú no insistes en tu primera propuesta.

## Distinguir VA de MDR/ADR

La VA habla del **qué** (la necesidad) y, como mucho, del **cómo interactúa/resuelve** a alto nivel — nunca del **cómo se construye**. Usa el criterio del manual (sección 4.2/4.3):

- **MDR** = decide la *forma o paradigma* de la solución (todavía habla el lenguaje de la Visión). Ejemplos de señales: menciona un enfoque metodológico, un paradigma de interacción, una estrategia general ("usar IA generativa para sugerir contenido", "modelo de suscripción").
- **ADR** = decide la *tecnología concreta* que materializa esa forma. Ejemplos de señales: stack, frameworks, proveedores, lenguajes, bases de datos ("Postgres", "serverless", "React Native").

Cuando detectes un fragmento así dentro de la intención del usuario:
- No lo borres silenciosamente ni lo repares tú.
- No insistas en que hay que moverlo ahora mismo ni ofrezcas redactar el MDR/ADR — no es el trabajo de esta skill.
- Simplemente sepáralo del cuerpo pulido de la VA y etiquétalo con una nota corta, p. ej. `🧭 Esto suena a MDR/ADR, no a VA:` seguido del fragmento.
- **No fuerces una sola etiqueta (MDR o ADR) si la decisión juega en ambos frentes.** Es común que una misma frase decida forma y tecnología a la vez (p. ej. "modelo fine-tuneado" es a la vez un paradigma —afinar un modelo propio— y ya casi una decisión técnica). En esos casos describe brevemente el razonamiento en vez de encasillarlo: "podría jugar como MDR (forma: X) o ADR (tecnología: Y)", sin obligarte a decidir por el usuario.

### Cuidado: el nombre de la "forma de solución" también puede ser MDR

El manual permite que "Qué es y cómo se usa" incluya el método (sección 4.1) — así que nombrar una forma de solución en la VA no es automáticamente un error. Pero cuando el producto descrito es en realidad un componente de bajo nivel dentro de una necesidad más grande, el nombre de esa forma (p. ej. "chatbot", "app", "dashboard", "bot") puede ya ser una elección de MDR — una forma entre varias alternativas posibles para resolver la necesidad — y no la necesidad en sí.

**Señal para detectarlo:** intenta reformular mentalmente el "Qué es" quitando el nombre de la forma de solución. Si la necesidad sigue siendo clara y completa sin ese nombre (p. ej. "necesito responder tickets de soporte de forma automatizada" tiene sentido sin decir "chatbot"), entonces ese nombre probablemente es MDR, no VA.

**Qué hacer en ese caso:** no reescribas tú el "Qué es" quitando la forma — decidir eso no te corresponde, sería opinar de más. En vez de eso, plantéalo como pregunta abierta al usuario, por ejemplo:
`🧭 "[forma]" podría ser el método (MDR) elegido para resolver la necesidad de "[necesidad reformulada sin la forma]", más que la necesidad en sí. ¿Quieres que la VA se quede a ese nivel de forma, o prefieres dejarla a nivel de la necesidad pura y que "[forma]" viva en un MDR aparte?`

## Proceso

1. **Lee la intención cruda** tal como la da el usuario, sin pedir que la reformule primero.
2. **Clasifica cada fragmento**:
   - ¿Describe qué es el producto/idea y cómo lo usa o con qué interactúa la persona? → va en "Qué es y cómo se usa".
   - ¿Describe un límite explícito, algo que el producto deliberadamente no cubre? → va en "Lo que no es".
   - ¿Menciona algo con lo que se compara o de lo que se diferencia? → va en "Alternativas cercanas".
   - ¿Describe paradigma/forma de solución o tecnología concreta? → sepárese como nota MDR/ADR (ver arriba), no entra al cuerpo de la VA.
   - ¿El "qué es" nombra una forma de solución (chatbot, app, dashboard...) que seguiría teniendo sentido como necesidad si se quitara ese nombre? → probablemente MDR disfrazado de VA (ver "Cuidado: el nombre de la forma de solución también puede ser MDR"). Plantéalo como pregunta, no lo reescribas tú.
3. **Pule la redacción** de cada sección con lo que el usuario ya dio — sin añadir contenido nuevo.
4. **Evalúa cada sección con contenido, no solo si está vacía.** Para **"Qué es"** y **"Lo que no es"** hay tres estados posibles, y los tres los decide el usuario, nunca la skill:
   - **Vacía** → no hay nada que pulir. Márcala `⏳ Pendiente` y haz 1-2 preguntas puntuales para que el usuario la origine.
   - **Débil** → el usuario dio algo, pero delimita poco: es genérico, obvio, cubre un solo ángulo, o no distinguiría este producto de otro parecido. Ejemplo de límite débil: "no reemplaza a los humanos" en un chatbot de soporte — es cierto pero no dice casi nada específico del producto. En este caso **no la des por completa**: consérvala tal cual la dio el usuario, márcala `🪶 Débil` y haz 1-2 preguntas puntuales que la reten a ser más específica (p. ej. "¿qué tipos de ticket concretos quedan fuera del chatbot? ¿hay líneas de producto, canales o niveles de severidad que explícitamente no toca?").
   - **Sólida** → delimita algo específico y verificable. No la toques más allá de pulir la redacción.
   - No completes tú estas dos secciones para que dejen de verse débiles — eso sería inventar contenido, que está fuera del alcance de la skill ahí. La pregunta es la herramienta; el usuario responde, tú vuelves a evaluar.
   - **"Alternativas cercanas"** sigue una lógica distinta — ver la sección dedicada "Alternativas cercanas: la excepción que sí investiga" más abajo. Ahí sí investigas y propones un borrador, independientemente de si el usuario ya mencionó algo o no.
5. **Presenta el resultado** en el chat con el formato de salida de abajo. No generes frontmatter, no propongas nombre de archivo, no ofrezcas "guardarlo" — si el usuario lo pide, aclara amablemente que esta skill no crea archivos ni asigna el ID, solo pule el contenido para que él lo pegue donde corresponda.

## Formato de salida

Responde directamente en el chat (no como artifact ni archivo), con esta estructura:

```markdown
## Qué es y cómo se usa
[texto pulido]

## Lo que no es
[texto pulido, si es sólido]
— o — 🪶 Débil: [texto tal cual lo dio el usuario] + [pregunta puntual para profundizar]
— o — ⏳ Pendiente: [pregunta puntual para el usuario]

## Alternativas cercanas (opcional)
[candidatos reales encontrados por búsqueda web]
🧪 Tentativo, corrígeme: [borrador de diferenciación frente a esos candidatos]
```

Si detectaste contenido de MDR/ADR, añade después:

```markdown
---
🧭 Detecté contenido que pertenece a MDR/ADR, no a la VA (no lo incluí arriba):
- "[fragmento]" → parece [MDR|ADR] porque [criterio breve]
```

## Ejemplo

**Intención cruda del usuario:**
> "Quiero una app que ayude a la gente a llevar un diario de gratitud, usando IA para sugerir preguntas. Todo corre en un backend serverless con Postgres."

**Salida esperada:**

```markdown
## Qué es y cómo se usa
Una aplicación que ayuda a las personas a llevar un diario de gratitud, sugiriéndoles preguntas que facilitan la escritura.

## Lo que no es
⏳ Pendiente: ¿qué queda explícitamente fuera? Por ejemplo, ¿es un diario de bienestar general, una app de terapia, un CRM emocional — o algo distinto a todo eso?

## Alternativas cercanas (opcional)
Búsqueda realizada: apps de diario de gratitud con IA. Candidatos cercanos: **Reflectly** (journaling con prompts guiados por IA), **Stoic** (check-ins emocionales diarios con preguntas adaptativas), **Grateful: A Gratitude Journal** (journaling de gratitud sin IA generativa, con prompts fijos).
🧪 Tentativo, corrígeme: a diferencia de Reflectly/Stoic (que cubren bienestar emocional en general), esta idea parece enfocarse específicamente en gratitud; y a diferencia de Grateful (prompts fijos), aquí las preguntas se generan/adaptan con IA. ¿Es así, o la diferencia real es otra?

---
🧭 Detecté contenido que pertenece a MDR/ADR, no a la VA (no lo incluí arriba):
- "usando IA para sugerir preguntas" → parece MDR porque decide el paradigma de la solución (asistencia generativa), no la tecnología concreta.
- "backend serverless con Postgres" → parece ADR porque decide la tecnología concreta que materializa la solución.
```

**Segundo ejemplo — sección débil, no vacía, y alternativa ya mencionada por el usuario:**

Intención: "Quiero un chatbot de soporte técnico que responda tickets automáticamente usando un modelo fine-tuneado, sin reemplazar a los agentes humanos en casos complejos. Se parece un poco a Intercom Fin."

```markdown
## Qué es y cómo se usa
Una forma de responder tickets de soporte técnico de manera automática, resolviendo casos simples sin intervención humana.

## Lo que no es
🪶 Débil: "No reemplaza a los agentes humanos en casos complejos." Esto es cierto pero genérico — casi cualquier producto de soporte con IA diría lo mismo. ¿Qué lo hace específico? Por ejemplo: ¿hay tipos de ticket, canales o niveles de severidad que explícitamente no toca?

## Alternativas cercanas (opcional)
Mencionaste Intercom Fin — confirmado como candidato. Búsqueda adicional encontró: **Zendesk AI**, **Freshdesk Freddy AI**, ambos con resolución automática de tickets vía modelos propios/fine-tuneados sobre el histórico de soporte.
🧪 Tentativo, corrígeme: estas tres ya cubren "resolver tickets automáticamente con un modelo entrenado sin reemplazar humanos en casos complejos" de forma bastante similar a lo descrito. La diferenciación real probablemente tiene que venir de otro lado (¿integración específica, tamaño de la empresa objetivo, algo del dominio técnico que atiende?) — vale la pena que la pienses antes de seguir.

---
🧭 Detecté contenido que podría pertenecer a MDR/ADR, no a la VA (no lo incluí arriba):
- "chatbot" → el "qué es" sigue teniendo sentido como necesidad sin ese nombre ("responder tickets de forma automatizada"). "Chatbot" podría ser el método (MDR) elegido entre varias formas posibles (chatbot, macros automáticas, IVR, respuestas plantilla) — ¿quieres que la VA se quede a ese nivel de forma, o prefieres dejarla a nivel de la necesidad pura?
- "modelo fine-tuneado" → juega en dos frentes: como MDR decide el paradigma (afinar un modelo propio vs. uno genérico), y casi ya como ADR apunta a una decisión técnica concreta. No lo encasillo en uno solo.
```

## Notas de tono

- El usuario puede compartir la intención de forma muy cruda o coloquial — está bien, ese es justamente el punto de partida esperado. No le pidas que la reescriba antes de trabajar con ella.
- Sé breve y directo en las preguntas de las secciones `⏳ Pendiente`; no generes un cuestionario largo, máximo 1-2 preguntas por sección.
- Si el usuario contesta las preguntas pendientes, vuelve a presentar la VA pulida completa (no solo el fragmento nuevo), para que siempre tenga el bloque completo listo para copiar.