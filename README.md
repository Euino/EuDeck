# NotebookLM Presentation Process Status

Date: 2026-05-20

## Objective

This workspace is for building a repeatable system to generate high-quality presentations in `NotebookLM`, with a specific immediate use case around the `GLT` mandate groups deck.

There are two parallel goals:

1. Produce a good presentation now.
2. Build a system where source documents + a high-level brief can reliably generate strong presentations in future.

## Core constraints confirmed

### 1. NotebookLM outputs are often effectively final

The generated `.pptx` decks reviewed in this process were flattened slide-image exports rather than normal editable slide decks.

Reviewed files:

- `GLT_Mandate_Blueprint.pptx`
- `GLT_v3.pptx`
- `GLT_v4.pptx`
- `GLT_SemiFinal.pptx`

Observed behavior:

- each slide was exported as a PNG image
- there were no real editable text objects on slides
- PowerPoint font/theme settings were therefore mostly irrelevant after export

Implication:

- style consistency cannot be fixed properly after generation
- prompt quality matters more than downstream editing instructions

### 2. NotebookLM follows structure better than visual styling

NotebookLM obeyed:

- slide order
- narrative logic
- major content framing
- some visual hierarchy cues

NotebookLM did not reliably obey:

- font family instructions
- exact brand-style instructions
- exact visual discipline
- anti-genericity instructions

Implication:

- the system must focus on what NotebookLM responds to reliably:
  - slide intent
  - hierarchy
  - compositional logic
  - density control
  - explicit non-invention rules

### 3. Exact font control is a false target in NotebookLM

Because the output is usually flattened into images, the real problem is not “wrong font file applied in PowerPoint.”

The real problem is:

- NotebookLM makes visual typography decisions slide by slide
- those decisions are then baked into raster images

Implication:

- prompt budget should not be spent on exact font names
- prompt budget should be spent on visible rendering behavior and layout logic

## What happened across versions

### Original baseline: `GLT_Mandate_Blueprint.pptx`

Strengths:

- stronger content credibility
- better preservation of real material
- closer to a real leadership working deck

Weaknesses:

- generic visual language
- weak ActionAid flavour
- average graphic quality

### `v3` prompt direction

Files:

- `BASE_PROMPT_NOTEBOOKLM_ACTIONAID_V3.txt`
- `NOTEBOOKLM_PROMPT_GLT_MANDATE_GROUPS_V3.txt`

What changed:

- reduced dependence on font instructions
- tighter visual grammar
- stricter archetypes
- more minimal composition

Result:

- too compressed
- lost important decision-grade content
- cleaner, but intellectually thinner
- felt generic in a minimalist-strategy way

Conclusion:

- visual discipline improved somewhat
- content integrity degraded too much

### `v4` prompt direction

Files:

- `BASE_PROMPT_NOTEBOOKLM_ACTIONAID_V4.txt`
- `NOTEBOOKLM_PROMPT_GLT_MANDATE_GROUPS_V4.txt`

What changed:

- stronger black/red contrast
- more explicit ActionAid flavour
- more activist-editorial tone

Result:

- more brand energy
- but still introduced invented content
- sometimes drifted into slogan/poster logic
- still weaker than the original blueprint on trustworthiness

Conclusion:

- stronger flavour alone is not enough
- content integrity is the harder constraint

## Critical scope correction from the user

The most important clarification in the whole process was that the deck is not just “about mandate groups.”

The real narrative is:

1. ActionAid identity evolution toward rooted `people power`
2. why mandate groups exist
3. the bridge from now to `July 2028`
4. the four groups
5. how groups interact and deliver
6. one vertical slide per group
7. governance / operating flow
8. what is needed from `CD Forum / ILT`

This led to the final `11-slide` architecture.

## Current best NotebookLM system artifacts

### Reusable system

Primary reusable system file:

- `NOTEBOOKLM_PRESENTATION_SYSTEM_11SLIDE.md`

Purpose:

- defines the repeatable workflow
- source docs + high-level brief + hard facts + slide intent -> final prompt

Main logic:

- do not let NotebookLM infer the deck logic by itself
- define slide jobs explicitly
- define facts that must not be invented or changed

### Current GLT-specific prompt

Primary GLT prompt:

- `GLT/outputs/mandate_groups_analysis/NOTEBOOKLM_PROMPT_GLT_11SLIDES_FINAL.txt`

This is the strongest prompt produced in this process for the GLT deck because it:

- follows the corrected `11-slide` structure
- protects verified content better than `v3/v4`
- hard-blocks invention of names, dates, and governance routes
- centers the people-power identity shift correctly

## Verified content anchors used

Most important sources:

- `GLT/outputs/mandate_groups_analysis/extracted/27 28 April 2026 GLT communique.txt`
- `GLT/outputs/mandate_groups_analysis/extracted/GLT 27 28.04.2026 detailed notes.txt`
- `GLT/outputs/mandate_groups_analysis/extracted/GLT Priorities and key dates 2026 April 2026.txt`
- `GLT/outputs/mandate_groups_analysis/extracted/Paper 0 - Agenda Directors Forum June 2026 DRAFT.txt`

Most important confirmed content used in prompts:

- people power remains central to ActionAid’s identity
- people power must not remain abstract
- the distinction is not whether ActionAid delivers, but how it delivers
- people power is the foundation; tangible solutions are the expression
- mandate groups are the bridge to the next strategy, not side process
- first evidence by end-2026
- first strategy draft by mid-2027
- strategy live in July 2028
- Group D governance route:
  - Arthur drafts
  - GLT input and endorsement
  - International Board / General Assembly

## What was tried outside NotebookLM

### Editable PowerPoint rebuilds

Files produced:

- `ActionAid_Strategic_Evolution.pptx`
- `ActionAid_Strategic_Evolution_v2.pptx`
- `ActionAid_Strategic_Evolution_Original.pptx`

Scripts:

- `GLT/outputs/mandate_groups_deck/build_actionaid_strategic_evolution.mjs`
- `GLT/outputs/mandate_groups_deck/build_actionaid_strategic_evolution_original.mjs`

Outcome:

- structurally valid editable decks were produced
- typography became controllable
- but visual quality still underperformed relative to user expectations
- result felt too schematic / too engineered / not artistic enough

Conclusion:

- local scripted PowerPoint is useful for technical editability
- it is not currently the preferred path for this presentation standard

### Canva route

Attempted:

- checked Canva connector
- no usable brand kit was available
- outline-review workflow was triggered, but the user did not see a usable review widget

Conclusion:

- Canva was not operationally usable in this session

## Current practical conclusion

The preferred working path remains `NotebookLM`, despite its flaws.

Reason:

- it still produces better visual presentation quality than the alternatives tested here
- the pain is in refinement and editability, not in first-pass visual potential

## Current recommendation for future use

### Use NotebookLM for generation

Use:

- `NOTEBOOKLM_PRESENTATION_SYSTEM_11SLIDE.md`
- deck-specific prompts derived from that system

For GLT specifically, use:

- `GLT/outputs/mandate_groups_analysis/NOTEBOOKLM_PROMPT_GLT_11SLIDES_FINAL.txt`

### Treat prompt construction as the real design stage

Because output slides are often flattened and hard to edit, most quality control must happen before generation:

- slide-by-slide intent
- mandatory facts
- anti-invention rules
- hierarchy and density instructions
- explicit framing of strategy logic

### Stop spending effort on these weak control surfaces

Avoid over-investing in:

- exact font family instructions
- exact theme metadata instructions
- instructions that assume editable PowerPoint text layers

### Focus instead on these high-leverage control surfaces

- narrative spine
- slide purpose
- visible compositional guidance
- which slides are evidence-heavy vs signal-heavy
- which facts must appear exactly
- what NotebookLM must not simplify away

## Suggested process going forward

### For any new deck

1. Gather source documents.
2. Extract non-negotiable facts:
   - names
   - dates
   - milestones
   - governance routes
   - strategic tensions
3. Define the exact slide architecture before writing the final NotebookLM prompt.
4. Mark each slide as one of:
   - framing / signal slide
   - evidence / detail slide
5. Write the NotebookLM prompt so each slide has:
   - title
   - purpose
   - must-include content
   - forbidden drift
6. Generate in NotebookLM.
7. Refine only where necessary.

### For GLT deck specifically

Stable architecture:

1. rooted identity / people power
2. why mandate groups
3. timeline to July 2028
4. four groups overview
5. interaction and delivery logic
6. Group A
7. Group B
8. Group C
9. Group D
10. governance / operating model
11. ask to CD Forum / ILT

## Final status

Current status of the process:

- the design problem is understood much better than at the start
- the correct GLT deck architecture is defined
- the best current reusable NotebookLM system is documented
- the best current GLT-specific prompt is available
- editable PowerPoint fallback exists, but is not preferred
- NotebookLM remains the primary tool

Most important takeaway:

The system should be optimized for `NotebookLM`'s actual behavior, not for ideal PowerPoint behavior.
