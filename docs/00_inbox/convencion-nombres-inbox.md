# Inbox — Convención de nombres para entradas de Inbox

Material de entrada para actualizar GOV-DOMER-SOFTWARE.
No es visión, no es dominio, no es ADR, no es REQ.

---

## Hecho observable

El manual vigente (v2.3.1) describe `00_Inbox/` así:

> `00_Inbox/` no requiere estructura; aquí se vuelca cualquier pensamiento.

Y en la sección 1:

> `00_Inbox/` — Captura rápida de ideas, feedback sin procesar y notas de reuniones.

En ninguno de los dos lugares se define:

- si las entradas del inbox llevan nombre;
- si ese nombre sigue alguna convención;
- si llevan frontmatter;
- si existe un prefijo identificador.

La práctica real del vault ya usa un patrón estable para entradas
que apuntan a tipos formales:

    inbox-<descriptivo-corto>.md

Esa práctica no está reconocida por el manual.

---

## Tensión identificada

El manual permite que el inbox no tenga estructura, pero no distingue entre:

1. captura cruda (nota suelta, sin nombre formal, sin destino declarado);
2. entrada de inbox con nombre descriptivo y destino declarado hacia uno
   o varios tipos formales.

Ambas cosas conviven hoy en `00_Inbox/` sin criterio escrito.

Consecuencia: cuando una entrada se promueve (a VA, Dominio, ADR, REQ),
no hay regla sobre:

- si el archivo original se archiva;
- si se renombra;
- si se conserva como trazabilidad del seccionamiento.

---

## Decisión candidata

Reconocer en el manual dos modalidades dentro de `00_Inbox/`:

### Captura cruda (sin cambios respecto a v2.3.1)

- Sin nombre formal obligatorio.
- Sin frontmatter obligatorio.
- Sin destino declarado.
- Vive hasta que se descarta o se promueve.

### Entrada de inbox formalizada

- Nombre: `inbox-<descriptivo-corto>.md`
  Sin prefijo de semana, sin id de tipo formal.
  El nombre debe dar indicios del contenido.
- Sin frontmatter obligatorio.
- Se sugiere declarar el destino al inicio del cuerpo
  (a qué tipo formal apunta: VA, Dominio, ADR, REQ).
- Se sugiere dejar plasmadas las dudas no resueltas.
- Se sugiere cerrar con un checklist de seccionamiento.

La modalidad formalizada es **preferente, no obligatoria**.

---

## Reglas de seccionamiento

Cuando una entrada formalizada se resuelve:

1. Su contenido se promueve a los tipos formales correspondientes,
   con sus propias DoR.
2. El archivo se archiva en `_Archive/` conservando el nombre
   `inbox-<descriptivo-corto>.md`.
3. Las dudas no resueltas permanecen en el inbox; no se promueven
   como pendientes a un tipo formal.

El inbox no es fuente de verdad. Mientras vive en `00_Inbox/`,
nada de lo que dice obliga. Al promover, el documento destino manda;
el inbox queda como rastro histórico.

---

## Cambios que implicaría en el manual

- Sección 2: ampliar la descripción de `00_Inbox/` con las dos modalidades.
- Sección 11 (o nueva): añadir reglas de seccionamiento del inbox.
- Encabezado: bump de versión menor (v2.3.1 → v2.4.0),
  `ultima_revision` actualizada, `reemplaza` actualizado.

---

## Dudas no resueltas

- ¿El prefijo `inbox-` es necesario, dado que la carpeta ya lo indica?
- ¿Una entrada de inbox puede declarar múltiples destinos?
- ¿El destino se declara al inicio del cuerpo, en una sección propia,
  o como línea suelta?
- ¿La modalidad formalizada se documenta como preferente o solo
  como permitida?
- ¿Se permite frontmatter distinto en cada vault, o DOMER fija uno?
- ¿El checklist de seccionamiento es obligatorio en la modalidad
  formalizada?
- ¿Qué pasa cuando una entrada sobrevive mucho tiempo sin resolverse?
  ¿Se marca, se revisa, se descarta?
