**El problema:**
El estándar de gobernanza DOMER define que el andamio es el lienzo donde se deja escrita la deducción concreta que precede a construir una pieza de un requisito. Al ser un formato totalmente libre, en los retos académicos he notado que genera parálisis por análisis. A veces los estudiantes no saben cómo empezar a plasmar esa deducción.

**La idea:**
Propongo oficializar una plantilla base sugerida para los andamios.

Esta plantilla respeta los metadatos obligatorios del frontmatter (`tipo`, `id`, `requisito`, `decisiones`) y asegura que se cumpla la Definición de Listo (DoR) del andamio, la cual exige que exista un REQ y al menos un ADR relacionado identificado.

**Plantilla propuesta:**

```markdown
---
tipo: andamio
id: AND-XXX
requisito: REQ-XXX
decisiones:
  - ADR-XXX
---

# [AND-XXX] [Nombre del Componente o Mecanismo]

**Contexto Conexo:**
[Breve conexión con el REQ que satisface y las ADRs que restringen o guían la implementación. Directo al grano].

## Enfoques Propuestos
* [ ] **Abstracción 1 ([Nombre]):** [Descripción cruda de su única responsabilidad].
* [ ] **Abstracción 2 ([Nombre]):** [Descripción cruda de su única responsabilidad].
* [ ] **Abstracción N ([Nombre]):** [Descripción cruda de su única responsabilidad].

---

### Desglose de la Idea
[Narrativa breve y exploratoria. Cómo interactúan estas abstracciones entre sí para resolver el problema. Se plantean las dudas o los mecanismos de integración sin dar por hecho el código final].
```

