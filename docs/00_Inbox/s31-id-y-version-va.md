# Identidad y Versionado de la Visión Activa

## Idea

La Visión Activa debería distinguir explícitamente entre su **identidad** y su **grado de madurez**.

Actualmente `VA-001` identifica la visión, pero no permite expresar cómo evoluciona sin crear una nueva VA. Esto lleva a dos extremos poco deseables:

* considerar que cualquier cambio importante obliga a crear una nueva VA; o
* tratar cambios conceptuales relevantes como simples ediciones del documento.

Se propone incorporar un campo `version` independiente del `id`.

## Hipótesis

El identificador (`VA-XXX`) representa la **identidad conceptual** de una visión. Mientras la esencia del producto siga siendo la misma, la identidad no cambia.

La versión representa la **madurez y evolución** de esa identidad.

Esto permitiría distinguir entre:

* una visión todavía en refinamiento;
* una visión oficialmente activa;
* una visión que continúa evolucionando sin perder su identidad.

## Evolución propuesta

La versión comenzaría en la serie `0.x`, correspondiente a una visión en construcción.

Ejemplo:

```yaml
id: VA-001
version: 0.1
status: Borrador
```

Cuando la visión cumple su Definición de Listo y pasa a `Activa`, alcanza su primera versión estable:

```yaml
id: VA-001
version: 1.0
status: Activa
```

A partir de ese momento, nuevas versiones reflejarían cambios conceptuales de la misma visión sin modificar su identidad.

## Preguntas abiertas

* ¿Es suficiente un esquema `X.Y`, o existe algún caso real que justifique un tercer nivel (`X.Y.Z`)?
* ¿Qué criterios deben diferenciar un incremento menor de uno mayor?
* ¿En qué momento deja de ser la evolución de una misma visión y corresponde crear `VA-002`?
* ¿Debe existir alguna relación formal entre la versión de la VA y la revalidación de MDR y ADR existentes?

## Motivación

La intención no es reemplazar el historial de Git, sino dotar a la Visión Activa de un ciclo de vida propio dentro de la gobernanza.

El `id` identifica **qué visión es**.

La `version` expresa **en qué estado de evolución se encuentra esa misma visión**.
