---
name: aishu-classroom-deck-builder
description: >-
  Build Aishu's signature classroom teaching decks for B.Tech courses (Computer
  Organization & Architecture and beyond). Use whenever the professor asks to build
  or rebuild a unit "for classroom teaching", "for class", "the classroom deck", "the
  PPT", or names a unit/chapter to present in the lecture hall. Produces ONE combined,
  self-contained animated HTML deck per syllabus unit (Unit-0 style), plus — later, on
  request — a presenter's guide, student notes, and a Bloom's question bank + answer key.
  This is the lecture-hall sibling of foothold-lesson-builder (which makes self-paced
  interactive lessons). Trigger on terse requests like "build unit 2 for class", "do the
  COA unit 3 deck", "make the classroom version".
---

# Aishu's Classroom Deck Builder

You are building **classroom instruction material** that Professor Aishu (Sri Ramachandra
Faculty of Engineering & Technology) projects on a screen and teaches in front of, one
keypress at a time. Students watch, think, and answer aloud — they never click anything.
This skill encodes her hard-won preferences; follow them exactly.

## Golden rules (learned directly from Aishu)

1. **Animation is the whole point.** COA is dismissed as "vague theory". Every abstract
   idea must be *shown moving* — data packets travelling a bus, the PC stepping down
   memory, bytes dropping into cells, a value overwriting another. A static slide about a
   dynamic concept is a failure. Prefer purpose-built SVG animation over bullet lists.
2. **No hand-up / mic / "ask the class" icons.** The active-learning instrument is the
   **concept-hook question**: an intriguing question shown big, then the answer revealed.
   Model them on the Unit-0 classic — *"the architecture didn't change, the organisation
   did — so why does the same program now run a billion times faster?"* Curiosity, not
   props.
3. **Importance badge, top-right, on (almost) every slide.** A colour-coded chip telling
   students how much this matters: **CORE** (purple, exam-critical), **SUPPORTING**
   (yellow, needed to understand), **EXTENDED** (blue, enrichment).
4. **"Get it into your memory" slides.** After explaining a concept — and after *each
   sub-concept* (e.g. after each of the five functional units, after PC/IR/MAR/MDR) —
   give a distinct **🧠 memory slide**: a green exam-answer card with the exact lines a
   student reproduces in the exam. This is where marks are won.
5. **Redundancy is welcome.** On CORE slides, give both the plain-language explanation
   *and* the textbook wording. Repeating a definition across the explanation slide and the
   memory slide is good, not sloppy. Never strip content to avoid repetition.
6. **Always name things where you describe them.** If a slide tells the "story" of a
   register/unit, its full name and definition belong *on that slide* — do not defer the
   name to the next slide.
7. **Scaffold from known → new.** Open every chapter by recalling what the student already
   built ("remember the half-adder from Unit 0.2", "in Ch 1 you named the five units").
8. **Student level always.** Plain language, one idea per slide, concrete numbers,
   Indian-classroom-relatable examples (₹, cricket, trains). If it needs more than ~35
   words of prose, it belongs in the presenter's guide, not the slide.
9. **Vivid memory operations.** Read = a *copy* returns, source unchanged. Write = new
   value *overwrites*, old value gone. Show both as animations, not text.
10. **Co-teacher parity.** Before building, read the PPTs in `References from co-teachers/`
    (especially Aysu's). The exam question-setter may be a different teacher — cover every
    topic they cover so students are never caught out. BUT keep topics in their **syllabus
    unit** (e.g. addressing modes belong to Unit 2, even though a co-teacher previews them).
11. **Go deep on the "obvious" foundational units — depth is where real understanding
    lives.** Never stop at "the control unit controls everything". Show HOW: it decodes
    the instruction in the IR into a precise sequence of control signals, and it runs on a
    **clock** — the computer's heartbeat, a square-wave pulse; the **clock rate** (Hz → GHz,
    e.g. 3 GHz = 3 billion ticks/second); one tick drives one micro-step; a faster clock
    means more steps per second, hence a faster machine (tie back to "same architecture,
    better organisation"). Mark such slides **EXTENDED**, but treat them as essential — Aishu
    considers this depth non-negotiable for her classroom.
12. **Finish one unit's whole story before the next; animate processes, not just values.**
    Cover all of memory (hierarchy + word/address for 32- vs 64-bit + the speed ranking)
    *before* starting the ALU — don't interleave units. And when you reach a unit that *does*
    something (ALU, control), animate the actual **process** — operands travelling from
    registers through the ALU, the operation selected by control, the result latched back —
    not a single value sliding past. A calculator program (input → registers → ALU → output)
    is the canonical five-units animation.

## Deliverables (per syllabus unit)

Build in this order; **decks first, documents later — and only on request**:

1. **UnitN_Deck.html** — ONE combined, self-contained animated deck for the whole unit
   (Aishu's confirmed preference: Unit-0 style, not per-lesson files). Chapters map 1:1 to
   the `course_COA` config's lesson list for that module.
2. **UnitN_PresenterGuide.docx** — per-slide talking points, timing, misconceptions,
   board-work, and the expected answers to the concept-hook questions. Carries the depth so
   slides stay sparse.
3. **UnitN_StudentNotes.docx** — detailed prose for students, textbook section references
   (Hamacher primary, Mano secondary), worked examples, and the question bank (no answers).
4. **UnitN_AnswerKey.docx** — every question with model answer, marks (1/2/5), Bloom's tag.

## Deck structure

- **16:9 landscape**, dark, fills the browser (professor presses F11). Big fonts readable
  from the back row: titles 52–72px, body ≥ 32px, diagram labels ≥ 18px in a large SVG.
- **Chapter arc**, repeated per chapter: `divider (chapter № + hook question)` →
  `scaffold (known→new)` → `concept-hook question` → `core concept slides w/ animation +
  badge` → `🧠 memory slide(s)` → more concepts → `🔑 key-insight slide`.
- **Navigation:** → / Space / click = next reveal step (then next slide); ← = previous;
  Home/End = first/last. Progress bar top; "slide n / N" bottom-right; chapter label
  bottom-left. Nothing else to click.
- **Embed real simulators** where they teach best, with visible credit. For COA, embed the
  **Little Man Computer** (© Peter L. Higginson, peterhigginson.co.uk/lmc) via `<iframe>`
  in Instruction Sequencing and the Capstone; always include an "open in new tab" fallback
  in case a browser blocks framing.
- **End the unit with a Capstone**: hand-trace one whole program (e.g. `C = A + B`) with a
  state table, a "your turn" simulator challenge, and a one-slide map of the whole unit.

## Visual system — use the template

`assets/deck_template.html` is the starter skeleton: it contains the exact palette, the
deck engine (fragment reveal + keys), and one worked example of every slide type
(divider, core slide + badge, concept-hook question, 🧠 memory slide, animated datapath,
key insight). **Start every new deck by copying it.** `assets/PALETTE_AND_PATTERNS.md` has
copy-paste snippets and the animation rules. Never invent new colours — the palette gives
visual continuity with the Foothold courses.

## Animation authoring rules (or it breaks)

- Packets travel a bus via CSS `offset-path`; the animation fires when the packet's `.frag`
  gets `.on`. **Pair each packet with its caption in the SAME `.frag`** so motion and
  narration reveal together — never split them into separate reveal steps.
- For step captions inside an animation, put them *inside the SVG* as a bottom caption band
  with an opaque background rect per step; later steps paint over earlier ones (a clean
  swap) and the SVG stays full-size. Do NOT stack caption `<p>`s under the SVG — it shrinks
  the graphic (Aishu flagged this).
- Anything that should be visible from the start (memory cells, register boxes) must NOT be
  a `.frag`, or it will start invisible.
- Every packet's `offset-path` must start and end exactly on its source/target box; sanity-
  check coordinates against the SVG `viewBox` so nothing flies off-screen.
- Requires a Chromium browser (Chrome/Edge) for `offset-path`. Note this to Aishu.

## Working process (do not skip)

1. **Gather first.** Read the syllabus unit, Aishu's captured textbook-content `.txt` if
   present, the `course_COA/config/course.config.js` (it fixes the chapter segregation),
   Unit 0 as the style template, and the co-teacher PPTs for parity.
2. **Propose the segregation**, then **propose the slide list** (chapters, one line per
   slide, marking which are animated / concept-hook / memory / key-insight). **Wait for
   Aishu's go-ahead** before building — unless she says proceed.
3. **Build the combined deck**, copying the template. Reuse any existing per-lesson decks by
   folding them in as chapters, restyled.
4. **Verify**: sections balanced (open = close), every `<svg>` closed, fragment reveals
   sequential, `<script>`/`</html>` present, slide counter matches. Coordinate-check the
   animations. If a headless browser is available, screenshot; otherwise say you verified
   structure and ask her to eyeball the motion in Chrome/Edge.
5. **One unit at a time.** Deliver the deck, show it, then move to docs / the Foothold
   course only when asked.

## Question bank (for the docs, later)

University-exam style, tagged with Bloom's level: ~6 × 1-mark (Remember/Understand),
~4 × 2-mark (Understand/Apply), ~3 × 5-mark (Apply/Analyze/Evaluate, ≥ 1 numerical/trace).
Map every chapter to its syllabus topic and CO. Textbooks: Hamacher/Vranesic/Zaky
(primary, chapter/section), Morris Mano (secondary); Tanenbaum / Hennessy-Patterson /
Stallings for enrichment.

## File locations & naming

Work inside the course repo: `COA_Classroom/UnitN/UnitN_Deck.html` (+ the three .docx).
Shared images live in `COA_Classroom/assets/`. Keep the deck a single self-contained file
(inline CSS/JS/SVG); the only external references are credited simulator iframes and images.
