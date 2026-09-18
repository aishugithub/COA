# Palette, semantics & animation patterns

## Colour palette (copy verbatim — never invent new colours)

    bg #0D1117   surface #161B22   card #1C2333
    accent #58A6FF   accentGlow #1F6FEB
    green #3FB950   yellow #D29922   purple #BC8CFF
    red #F85149   orange #F0883E   teal #39D0D8
    text #E6EDF3   muted #8B949E   border #30363D

**Semantics:** green = correct / success / a returned copy · red = wrong / broken / an
overwrite · yellow-orange = warnings & lower-level contrast · purple = key ideas & CORE ·
accent blue = the concept being taught & EXTENDED · teal = memory / registers / values.

## Importance badge decision

- **CORE** (`b-core`, purple) — will be examined; students must master it.
- **SUPPORTING** (`b-sup`, yellow) — needed to understand the core, lighter in the exam.
- **EXTENDED** (`b-ext`, blue) — enrichment / context, good to know.

## The seven slide types (in `deck_template.html`)

1. `divider` — chapter № + title + one-line hook question.
2. core/supporting concept slide — `<div class="badge …">` + explanation + textbook line.
3. `qslide` — concept-hook question, answer in a `.frag`.
4. `heroslide` + `animwrap` — an animation that fills the stage.
5. `memslide` — 🧠 exam-answer card.
6. `keyslide` — 🔑 one-sentence chapter close.
7. simulator embed (commented pattern) — iframe + credit + fallback link.

## Animation gotchas (each one cost a real bug)

- **Pair packet + caption in the SAME `.frag`.** If the packet and its caption are separate
  reveal steps, all packets play before any caption appears. Put the caption band inside the
  SVG within the packet's `<g class="frag">`.
- **Caption band inside the SVG**, not stacked `<p>`s below it — otherwise the graphic
  shrinks. Give each caption an opaque bg rect; later steps paint over earlier (clean swap).
- **Visible-from-start elements must not be `.frag`s** (memory cells, register boxes) or they
  start invisible and look inconsistent with their neighbours.
- **Give moving cards a fill** (e.g. `fill:var(--accent)`); an unfilled SVG rect renders black.
- **Coordinate-check** every `offset-path` start/end against the box centres and the `viewBox`.
- `offset-path` needs a **Chromium browser (Chrome/Edge)**. Tell Aishu; add F11 note.

## Read vs Write (make them unmistakable)

- **Read** — processor sends address + Read; a *copy* returns on the data bus; source
  UNCHANGED. RTN `DR ← [LOC]`. Use green/teal.
- **Write** — processor sends address + data + Write; the new value OVERWRITES the old, which
  is gone. RTN `M[LOC] ← R1`. Show the old value being replaced; use red accent for the loss.

## Pre-delivery checklist

- [ ] `<section>` opens == closes; every `<svg>` closed; `<script>`/`</html>` present.
- [ ] Fragment reveals are sequential and each animation fires with its caption.
- [ ] Every chapter: divider → scaffold → ≥1 concept-hook question → core slides →
      🧠 memory slide(s) → 🔑 key insight.
- [ ] Badge on (almost) every slide; CORE slides carry textbook wording too.
- [ ] Co-teacher PPT topics all covered; syllabus placement respected.
- [ ] Simulator embeds credited with a new-tab fallback.
- [ ] Slide counter matches; opens correctly in Chrome/Edge at F11.
