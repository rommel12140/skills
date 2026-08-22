# Attribution

The `copy-review` and `design-review` skills adapt material from the projects below.
Each entry records the licence and what was taken.
Nothing was copied from a source without a published licence.

## MIT

### nutlope/hallmark
<https://github.com/nutlope/hallmark>

Taken: the practice of phrasing a check as a violation question where an affirmative answer fails the gate; the separation of checks that can be read from source from checks that require a rendered page; several accessibility and motion entries (`A1`, `A2`, `A3`, `M1`, `M2`).

Not taken: the theme system, the macrostructure library, the component cookbook, the four verbs.
Those encode a specific design taste that conflicts in places with the rules this skill enforces.

### funboy322/avoid-ai-design
<https://github.com/funboy322/avoid-ai-design>

Taken: the category and ID scheme (`T`, `C`, `L`, `K`, `S`, `M`, `I`, `CP`, `IM`); the P0 to P2 severity model; the practice of pairing each fix to a named stack; several catalog entries (`T1`, `C1`, `C2`, `L1`, `L2`, `K1`, `K3`, `K4`, `I2`, `CP2`, `IM1`).

### leonxlnx/taste-skill
<https://github.com/leonxlnx/taste-skill>

Taken: eleven entries in `design-review`, from section 9 of `skills/taste-skill/SKILL.md` at commit `72e2995` (`C5`, `L5`, `L6`, `K5`, `CP5`, `CP6`, `CP7`, `CP8`, `CP9`, `IM2`, `A4`). Each was rewritten as a gate in this catalog's form, given a severity, a render flag, and a fix for each of the three stacks.

Not taken: the three dials, the brief to design-system map, the package and icon-library prescriptions, and the aesthetic presets.
Those conflict with gate `X1`, which requires the visual language to come from the client's world rather than from a named aesthetic, and they assume an npm stack that most of the work here does not use.

### conorbronsdon/avoid-ai-writing
<https://github.com/conorbronsdon/avoid-ai-writing>

Taken: the pattern category structure; the exemption model that spares code blocks, quoted material, tables, and blockquotes; the published finding that a composite slop score has no reliable predictive value, which is why neither skill reports one.

Not taken: the detector implementation, the corpus, the scoring engine.

### coreyhaines31/marketingskills
<https://github.com/coreyhaines31/marketingskills>

Taken: the architecture only. One `evals/` directory per skill, and one shared project-context file that every skill reads so the skills carry no product opinions of their own.

No content was copied.

## Apache-2.0

### boraoztunc/skills
<https://github.com/boraoztunc/skills>

Taken: positioning and promise structure from the `ogilvy` skill; plain-English substitutions from `copy-editing`; transition guidance from `copywriting`.

Apache-2.0 requires this notice be preserved in redistributions.

## Read but not used

### jalaalrd/anti-ai-slop-writing
<https://github.com/jalaalrd/anti-ai-slop-writing>

No licence file is published in this repository.
It was read for ideas.
No text, list, or structure was copied from it.
