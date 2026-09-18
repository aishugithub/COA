# COA Classroom — working rules

## Build on request (Aishu's workflow preference)
When Aishu asks for a **modification to a slide/deck**, apply it immediately — do
NOT stop to ask for a separate go-ahead before editing. Proposing the plan and then
building in the same turn is fine; waiting on a confirmation step is not what she wants.

## Golden rule: always go by the textbook
When building or editing any teaching material for this course, follow the
**textbook conventions** (Hamacher-based; see `References from co-teachers/`).
All the animations, reframings, and simplifications exist only to make the
**textbook** learning easy — never to introduce non-standard notation, invented
machines, or conventions that differ from the book.

Practical implications:
- Assembly examples use the textbook **load/store** convention: only `Load` and
  `Store` touch memory; arithmetic is **register-to-register** (e.g. `Add R4, R2, R3`).
- Describe instruction effects in **RTN** (Register Transfer Notation), e.g. `R2 ← [A]`,
  `R4 ← [R2] + [R3]`, `M[C] ← [R4]`.
- Do NOT frame examples as a "hypothetical CISC / x86 / 68000" machine — it's simply
  a processor with general-purpose registers, as the textbook presents it.

## Naming & the memory interface (Aishu's stressed conventions)
- **Reserve single letters A, B, C for memory locations** (as in `C = A + B`). NEVER
  label a register A/B/C/D. Registers are `R0…Rn`, or the named ones `PC, IR, MAR, MDR`.
- **Everything to and from memory passes through MDR.** MAR holds the address, MDR holds
  the data; there is no direct register↔memory path. So:
  - Read:  `MDR ← M[MAR]`
  - Write: `MDR ← R1`, then `M[MAR] ← MDR` (data goes R1 → MDR → memory, never R1 → memory).
  - Use MAR/MDR as primary names (what Aishu taught in Unit 1); note Mano's `AR/DR` as an alias.

## The constant demo program (Unit 1, Ch 2 — Basic Operational Concepts)
Canonical textbook **C = A + B**, reused across the whole module:
```
100:  Load  R2, A        R2 ← [A]
104:  Load  R3, B        R3 ← [B]
108:  Add   R4, R2, R3   R4 ← [R2] + [R3]
112:  Store R4, C        M[C] ← [R4]
```
Data: A = 5, B = 3 → C = 8. (The Chapter-1 role-play uses the same story at an
intuitive level.)

## Projector legibility (hard rule)
The room projector is low quality, so **all text must be bright**. Never use dark-grey
text on the dark background. In the decks this means `--muted` (and the whole palette)
is kept bright/near-white; keep it that way and avoid dim greys for any lettering.
Dark text is only allowed *on top of a bright fill* (e.g. dark text on a yellow packet).

## Deliverables
Unit decks live in `Unit1/Unit1_Deck.html` etc. — landscape HTML teaching decks
built with the classroom-lesson-builder style (stepwise `.frag` reveals, SVG
animations, "Commit to memory" exam-answer cards, Bloom-tagged questions).
