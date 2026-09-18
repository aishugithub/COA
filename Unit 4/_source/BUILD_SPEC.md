# Unit 4 · Memory Organizations — Student Notes: Build Spec
(prepared in advance so the scheduled build session has everything it needs, with no re-reading of PDFs)

## Deliverable
- File: `Unit4_MemoryOrganizations_Notes.html`
- Location: `C:\aishu\courses\COA_Classroom\Unit 4\Unit4_MemoryOrganizations_Notes.html` (new "Unit 4" folder, mirroring how Unit 3's files live in their own subfolder)
- Format: standalone HTML, same CSS/structure/visual language as
  `C:\aishu\courses\COA_Classroom\Unit 3\Unit3_Pipelining_Notes.html` (paper theme, dark "figure plate" boxes for diagrams,
  `.term`/`.key`/`.worked`/`.qbox`/`.explain` styling, TOC linking to `<h2 class="ch">` chapters). Copy that file's exact
  `<style>` block and structural conventions — do not re-invent the CSS.
- **Diagrams = actual textbook page crops** (Aishu's explicit choice), not redrawn SVGs. Embed the cropped PNGs
  (from `figs/` and `mano_figs/` alongside this spec) as `<img>` inside a `.plate`-style frame with a caption
  underneath naming the figure number and source book. Where a crop still shows more of the page than just the
  diagram, that's fine — tighten with a further visual crop if you want, but do not skip the image.
- **Text = same wording/definitions as the textbooks.** Draw content from the two full-text extracts provided
  (`hamacher_ch08_fulltext.txt`, `mano_ch12_fulltext.txt`) — paraphrase minimally, preserve exact terminology,
  and keep the bullet-point / key-term-highlighted style Unit 3 uses (not verbatim copy-paste paragraphs).
- **7 chapters, one per syllabus line item** (Aishu's choice), each with `x.y` subsections like Unit 3:
  1. Memory Hierarchy
  2. Main Memory — RAM and ROM Chips
  3. Auxiliary Memory
  4. Associative Memory
  5. Cache Memory
  6. Virtual Memory
  7. Memory Management Hardware
- **Include, per chapter (Aishu's choice — "yes, both"):**
  - At least one **worked numerical example** box (`.worked`), e.g.: chip-count/address-map sizing (Mano 12-1/12-4),
    cache hit-ratio / average-access-time calculation, tag/index/offset bit-splitting for a given cache size,
    virtual-to-physical address translation walk-through (Mano's hex example in 12-7, or Hamacher's Fig 8.25 style).
  - A short **question box** (`.qbox`) of 3-6 questions after each chapter, styled like Unit 3's — draw from the
    "PROBLEMS" section at the end of Mano's chapter (problems 12-1 through 12-12+, already in `mano_ch12_fulltext.txt`)
    and from Hamacher's end-of-chapter problems if present in the extracted text.
- Every key term must be bolded/`.term`-highlighted on first use (RAM, ROM, SRAM, DRAM, hit ratio, locality of
  reference, tag, page fault, TLB, segment, etc.) — mirror Unit 3's highlighting density.

## Syllabus scope (CSE23CT201, Unit 4 — 9 hours) — do not skip anything on this list
Source: `Syllabus_CSE23CT201_Computer_Organization_and_Architecture.pdf`
> Memory Hierarchy, Main memory: RAM and ROM chips, Auxiliary Memory, Associative memory, Cache memory,
> Virtual Memory, Memory Management Hardware.

**Explicitly OUT of scope for Unit 4** (belongs to Unit 5 per this syllabus, even though Hamacher Ch.8 covers it in
the same physical chapter): Direct Memory Access (DMA) — Hamacher Fig 8.12 "Typical registers in a DMA
controller" and Fig 8.13 "Use of DMA controllers in a computer system". Do **not** include these in Unit 4 notes.

## Two source textbooks — both fully extracted, use both
1. **Hamacher, Vranesic & Zaky, "Computer Organization and Embedded Systems", 5th ed., Chapter 8 "The Memory
   System"** (primary syllabus reference #1). Clean text layer extracted to `hamacher_ch08_fulltext.txt`
   (page markers `===== PAGE N (book p.XXX) =====`). Figures cropped precisely (diagram + caption only) into
   `figs/Fig_8_N.png`, indexed in `figures_manifest.json`. Covers: 8.1 Basic Concepts, 8.2 Semiconductor RAM
   Memories, 8.3 Read-Only Memories, 8.4 DMA (**exclude**, see above), 8.5 Memory Hierarchy, 8.6 Cache Memories,
   8.7 Performance Considerations, 8.8 Virtual Memory, plus disks/tape sections (8.x, no numbered subsection seen
   in extract — check text) for Auxiliary Memory. **Does not have a standalone Associative Memory section** — only
   associative *cache mapping* (Fig 8.17).
2. **M. Morris Mano, "Computer System Architecture", Chapter 12 "Memory Organization"** (syllabus reference #2).
   This is a scanned chapter (no text layer) — OCR'd to `mano_ch12_fulltext.txt` (OCR text, expect occasional
   character errors — cross-check against the page images in `mano_figs/` when quoting precisely). Sections map
   **exactly 1:1 onto the syllabus's 7 Unit-4 topics**:
   - 12-1 Memory Hierarchy (Fig 12-1)
   - 12-2 Main Memory — RAM and ROM Chips (Figs 12-2, 12-3, 12-4)
   - 12-3 Auxiliary Memory (Fig 12-5)
   - 12-4 Associative Memory (Figs 12-6, 12-7, 12-8, 12-9) — **this is the primary source for Chapter 4**, since
     Hamacher doesn't cover it. Use Mano's Argument Register / Key Register / Match Register treatment and its
     numerical no-match/match example.
   - 12-5 Cache Memory (Figs 12-10 through 12-15)
   - 12-6 Virtual Memory (Figs 12-16 through 12-20)
   - 12-7 Memory Management Hardware (Figs 12-21 through 12-25)
   Full-page crops (page + all figures on it, lightly margin-trimmed) are in `mano_figs/`, indexed in
   `mano_figures_manifest.json`. Some pages hold two figures — the crop covers both; use image-editing/cropping
   at build time if you want them separated, or just caption both under one plate.

## Chapter-by-chapter source map
| # | Chapter | Primary source(s) | Key figures |
|---|---|---|---|
| 1 | Memory Hierarchy | Hamacher §8.5 (Fig 8.14) + Mano §12-1 (Fig 12-1) | Fig 8.14, Fig 12-1 |
| 2 | Main Memory: RAM & ROM Chips | Hamacher §8.2–8.3 (Figs 8.2–8.11) + Mano §12-2 (Figs 12-2–12-4) | Fig 8.3, 8.4, 8.7, 8.8, 8.10, 8.11, 12-2, 12-3, 12-4 |
| 3 | Auxiliary Memory | Hamacher (disk/optical/tape figs 8.27–8.30) + Mano §12-3 (Fig 12-5) | Fig 8.27, 8.28, 8.29, 8.30, 12-5 |
| 4 | Associative Memory | **Mano §12-4 only** (Hamacher has no dedicated section) | Fig 12-6, 12-7, 12-8, 12-9 |
| 5 | Cache Memory | Hamacher §8.6 (Figs 8.15–8.23) + Mano §12-5 (Figs 12-10–12-15) | Fig 8.16, 8.17, 8.18, 12-11, 12-13, 12-14, 12-15 |
| 6 | Virtual Memory | Hamacher §8.8 (Figs 8.24–8.26) + Mano §12-6 (Figs 12-16–12-20) | Fig 8.25, 12-17, 12-19, 12-20 |
| 7 | Memory Management Hardware | Mano §12-7 (Figs 12-21–12-25); Hamacher's brief MMU/TLB mention | Fig 12-21, 12-24, 12-25 |

## Reference deck already built (style/scope cross-check, not the source of truth for wording)
`Unit4_Memory_Organizations.pdf` (uploaded by Aishu) — a classroom slide deck already covering all 7 topics in
4 parts. Useful for a sanity-check of scope and the "Unit Summary" / "Practice Questions" framing, but the **notes**
must be far more elaborate and textbook-literal than this deck (the deck is bullet-slide teaching material; the
notes are the full reading/reference document, matching Unit 3 Notes' depth).

## Files provided alongside this spec (all already extracted — do not re-fetch/re-OCR)
- `hamacher_ch08_fulltext.txt` — full clean text, Hamacher Ch.8 (67 pages)
- `figures_manifest.json` + `figs/Fig_8_N.png` — 30 precisely-cropped Hamacher figures (diagram+caption only)
- `mano_ch12_fulltext.txt` — OCR text, Mano Ch.12 (pages 445–483)
- `mano_figures_manifest.json` + `mano_figs/Page_XXX_*.png` — 21 full-page crops covering Mano Figs 12-1–12-25
- This `BUILD_SPEC.md`

## Style reference already inspected (do not need to re-open unless verifying)
`Unit3_Pipelining_Notes.html`: paper theme (`--paper:#fbfaf7`), Georgia-serif headings, `.plate` dark boxes
(`#0D1117` background) for figures with an italic caption below, `.key` callout boxes, `.worked` example boxes,
`.qbox` question boxes with a `.mk` mark-value tag, a 2-column `.toc` at the top linking to each `<h2 class="ch" id="cN">`.
7 numbered chapters, each with `<div class="lead">` under the `<h2>` naming the textbook section(s) it follows.
