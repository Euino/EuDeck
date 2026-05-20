# Slide Creation System Status

Date: 2026-05-20

## Purpose

This document defines the current direction for a repeatable slide-creation system.

The target is not a one-off deck.

The target is a system that:

1. takes source documents plus a high-level brief
2. generates a strong presentation in `NotebookLM`
3. stays consistent with your taste
4. carries visible `ActionAid` character
5. minimizes post-generation cleanup

## Current conclusion

`NotebookLM` remains the primary generation tool.

Not because it is controllable.
Because, in practice, it still produces better presentation aesthetics than the alternatives tested here.

The system therefore has to be designed around `NotebookLM`'s real behavior, not ideal presentation-software behavior.

## What NotebookLM is good at

It is relatively good at:

- following a clear narrative spine
- respecting slide order
- carrying forward major content framing
- producing visually polished first-pass slides
- translating a strong brief into a presentation-like output

## What NotebookLM is bad at

It is unreliable at:

- exact font control
- exact brand-style obedience
- exact layout repetition
- preserving every detail unless protected explicitly
- avoiding invented specifics unless constrained hard
- giving clean editable output

## Structural constraint that matters most

The exported `.pptx` output is often effectively flattened.

Observed behavior in generated decks reviewed during this process:

- slides exported as PNG-based slide images
- little or no real editable text layer
- PowerPoint font settings not meaningfully reusable afterward

Implication:

- prompt quality is the real design stage
- refinements after generation are expensive and frustrating
- exact font instructions are weak leverage

## System objective

The system should not aim for:

- perfect brand compliance at microscopic level
- exact font-family fidelity
- exact template behavior

The system should aim for:

- consistent narrative quality
- consistent hierarchy
- consistent taste
- visible ActionAid flavor
- strong first-pass slide composition
- high trustworthiness of content

## The design problem

There are two simultaneous consistency targets:

1. consistency with your taste
2. consistency with ActionAid

These are related but not identical.

### Consistency with your taste means

- sharp editorial hierarchy
- fewer generic corporate layouts
- less safe consulting-template logic
- stronger visual intent
- slides that feel authored, not assembled
- slides that are not over-clean at the expense of tension

### Consistency with ActionAid means

- people, power, justice, movement, and practical change remain visible
- the tone is serious, political, and grounded
- not a glossy corporate deck
- not NGO-generic softness
- not campaign-poster slogans replacing real analysis
- black/red editorial force, but with institutional credibility

## Current system principles

### 1. Start from slide jobs, not from style prompts

Do not ask NotebookLM to “make a beautiful deck.”

Instead define:

- what each slide must do
- what must appear
- what must never be lost
- what the viewer should understand after seeing it

### 2. Protect facts explicitly

Any deck needs a protected fact layer:

- names
- dates
- milestones
- governance routes
- numbers
- strategic tensions

If these are not listed explicitly, NotebookLM may compress, paraphrase, or invent.

### 3. Separate signal slides from evidence slides

This is one of the most important working rules.

Signal slides:

- framing
- thesis
- transition
- decision logic
- asks

Evidence slides:

- scope
- workstreams
- operating detail
- milestones
- comparative logic
- governance flow

If this distinction is not made, NotebookLM tends to do one of two bad things:

- over-simplify evidence slides
- over-fill signal slides

### 4. Use visible behavioral instructions, not abstract style language

Weak prompt language:

- “use our brand”
- “be elegant”
- “use ActionAid style”
- “use these fonts”

Stronger prompt language:

- oversized black titles
- high contrast red only for pressure, urgency, or decision signals
- flat backgrounds
- one dominant visual move per slide
- no decorative gradients
- no generic icon grids
- no equal visual weight across all boxes

### 5. Constrain invention aggressively

Every prompt should contain an explicit no-invention rule:

- do not invent names
- do not invent milestones
- do not invent governance routes
- do not invent examples unless clearly marked as illustrative

### 6. Do not over-normalize the deck

A bad system makes every deck feel mechanically tidy.

The better target is:

- one coherent visual language
- but varied slide compositions
- each slide shaped by its job

## Current prompt architecture

The working prompt should be built in layers.

### Layer 1. System role

What NotebookLM is being asked to do:

- produce a presentation
- not a document
- not a summary
- not a visual report

### Layer 2. Design behavior

Visible rules:

- contrast
- hierarchy
- density
- composition discipline
- where to use red
- what generic habits to avoid

### Layer 3. Content protection

Protected facts list:

- names
- dates
- required phrases
- structural logic

### Layer 4. Slide architecture

For each slide:

- title
- role
- must-include points
- what to emphasize
- what not to reduce or simplify

### Layer 5. Final quality controls

Checklist for the generated deck:

- does it preserve core facts
- does it feel like one deck
- is it generic
- is it too corporate
- is it too slogan-heavy
- is it too thin

## What the reusable workflow should be

### Step 1. Gather inputs

Inputs should be separated before prompt writing:

1. source documents
2. high-level brief
3. hard facts list
4. desired slide count
5. audience
6. deck purpose

### Step 2. Build the fact lock

Before any style work, extract:

- fixed names
- fixed dates
- fixed numbers
- decisions already made
- decisions still open
- relationships and process steps that must remain exact

### Step 3. Define the deck spine

Before writing the final prompt, define:

- opening logic
- middle logic
- closing logic
- where signal slides sit
- where evidence slides sit

### Step 4. Define slide-by-slide jobs

Each slide should have:

- title
- purpose
- 3 to 6 must-include elements
- dominant message
- dominant visual move

### Step 5. Write the generation prompt

The prompt should be written as an operating brief, not a style poem.

### Step 6. Generate once

Judge the first generation on system quality, not on perfection.

Questions:

- did the prompt architecture work
- where did NotebookLM drift
- what category of failure occurred

### Step 7. Refine surgically

Do not rewrite everything after every generation.

Instead identify failure type:

- too generic
- too thin
- too slogan-heavy
- too dense
- invented detail
- weak ActionAid feel
- weak hierarchy

Then fix the system at that layer.

## Current style direction for the system

This is the current preferred direction.

### Tone

- editorial
- political
- serious
- grounded
- sharp

Not:

- soft NGO brochure
- consulting deck
- campaign poster
- over-minimal tech deck

### Hierarchy

- strong oversized titles
- visible contrast between frame and detail
- clear dominant message on each slide
- less equal-weight box repetition

### Color logic

- near-black for structure and authority
- ActionAid red for urgency, pressure, conflict, or emphasis
- restrained neutrals for support

### Composition

- asymmetry is acceptable
- every slide should have one dominant move
- avoid overuse of boxed grids
- avoid default process arrows unless necessary
- avoid pseudo-smart decoration

## Failure modes to guard against

### 1. Generic corporate

Symptoms:

- neat but forgettable
- consultant boxes
- no political force

### 2. Generic minimalist

Symptoms:

- cleaner than before
- but thinned out
- loses serious content

### 3. Slogan drift

Symptoms:

- strong red statements
- but analysis underneath is weak
- feels like campaign rhetoric, not leadership material

### 4. Invention drift

Symptoms:

- wrong names
- invented specifics
- false examples

### 5. Over-compression

Symptoms:

- strategic content reduced to broad labels
- no decision-grade detail left

## Quality rubric for future generations

Every generated deck should be judged on:

1. Content integrity
2. Strategic clarity
3. Visual hierarchy
4. ActionAid character
5. Consistency with your taste
6. Non-generic composition
7. Whether it feels usable without major rebuilding

## Current reusable assets

### Base system document

- `NOTEBOOKLM_PRESENTATION_SYSTEM_11SLIDE.md`

Use this as the current structural reference for prompt-building logic, not as a final perfect system.

### Prompt experiments

- `BASE_PROMPT_NOTEBOOKLM_ACTIONAID.txt`
- `BASE_PROMPT_NOTEBOOKLM_ACTIONAID_Codex.txt`
- `BASE_PROMPT_NOTEBOOKLM_ACTIONAID_V3.txt`
- `BASE_PROMPT_NOTEBOOKLM_ACTIONAID_V4.txt`

These should be treated as explored directions, not final answers.

What they established:

- `v3` showed the risk of over-minimal compression
- `v4` showed the risk of forcing brand flavour too hard without enough fact protection

## Current preferred system direction

The best future system should:

- be generic in structure
- be specific in constraints
- be consistent in taste
- be visibly ActionAid
- protect content aggressively
- distinguish signal slides from evidence slides
- guide composition without over-templating every slide

## What this means operationally

The system should evolve toward:

1. one reusable NotebookLM operating prompt
2. one reusable ActionAid design-behavior layer
3. one reusable fact-lock section
4. one reusable slide-job template
5. one post-generation evaluation rubric

Then each new deck only swaps in:

- source docs
- hard facts
- audience
- slide architecture
- deck-specific content

## Final status

The process is not finished, but the direction is now much clearer.

The right ambition is not:

- “make NotebookLM obey fonts”

The right ambition is:

- “build a disciplined prompt system that makes NotebookLM generate slides in a consistent editorial language, with strong content fidelity and visible ActionAid character.”
