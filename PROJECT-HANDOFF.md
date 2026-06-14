# A&P Lecture Core — Project Handoff

Paste this whole file into a new chat to resume the project with full context. Last updated June 13, 2026.

## What this project is

Building a reusable library of accessible, self-contained lecture decks for Dr. Sharilyn Rennie ("Scrubs"), used across BIO 004 (Solano), BIO 431, and BIO 304 (ARC). Each chapter ships as two matched deliverables: an interactive HTML deck (she re-records narration over it) and an accessible PowerPoint (students download it; required by an accommodation). Decks are class-agnostic and live in the shared repo so all three courses reuse them.

Repo: `github.com/drsrennie-stack/A-P-lecture-core` (GitHub Pages is ON, served via Jekyll).

## Decks built so far

| Chapter | HTML file | PPTX file | Slides | Status |
|---|---|---|---|---|
| Foundations (Language of Anatomy + Body Organization) | `foundations-human-anatomy.html` | `Foundations-Human-Anatomy.pptx` | 30 | Done, QR added |
| The Cell (anatomy + histology) | `cell-anatomy-histology.html` | `The-Cell-Anatomy-and-Histology.pptx` | 30 | Done, QR added |
| Tissues & Histology | `tissues-histology.html` | `Tissues-Histology.pptx` (PPTX still to build) | 31 | HTML done; PPTX pending |

Still to build: **Integumentary (anatomy + histology)** deck. Needs a skin-histology source plus the labeled "Skin" model plate (epidermis/dermis/hypodermis, sebaceous gland, arrector pili, apocrine + eccrine sweat glands, Pacinian corpuscle) added to the repo as a PNG.

## Per-chapter structure (the standard)

Six concepts per chapter, ~10–12 min video each. Each deck: title slide (logo + QR + PowerPoint/PDF links), part dividers, content slides, DOK 1–3 practice questions (interactive reveal), a "label/identify it" slide, and a bolded "Key takeaways" slide.

- **Cell** concepts: 1) cell & plasma membrane, 2) surfaces & junctions, 3) nucleus, 4) endomembrane system, 5) cytoskeleton/power/storage (+ cytosol & inclusions), 6) histology / form follows function.
- **Tissues** concepts: 1) four tissue types + how to read a slide, 2) epithelium, 3) connective tissue proper, 4) supporting & fluid CT (cartilage, bone, blood), 5) muscle, 6) nervous tissue + synthesis.

Every tissue/structure gets the same teaching block: **Where (location) · Job (function) · Spot it (special cells + how to ID)**.

## Design system (non-negotiable)

- **Palette (PRIMARY teaching):** Navy `#0B1530`, Rust `#8B3A2E`, Brushed gold `#C9A14A`/`#DCB45C`, White, off-white `#FAFAF9`. **No cream, no sage** in teaching materials.
- **Fonts:** web = Plus Jakarta Sans / system; PPTX = Calibri. Eyebrows in rust, uppercase.
- **Writing rules:** no em dashes (use commas/periods/parentheses). Student-facing byline is "Dr. Sharilyn Rennie" with **no credential suffix**.
- **Accessibility floor: WCAG 2.2 AA, target AAA.** Real text (never text-as-image), alt text on every image, ARIA labels on SVGs (`role="img"`), slide titles, skip link, keyboard-operable lightbox, `aria-live` reveals, `prefers-reduced-motion`, visible focus. Each project ships a `compliance-notes.md` (still to write for Cell and Tissues).
- **HTML/Kajabi rules:** bake the iframe height-sender (postMessage + ResizeObserver) before `</body>`; internal/same-domain links `target="_top"`; external links `target="_blank" rel="noopener"`.

## The reusable deck "shell"

All decks share one self-contained HTML shell (inline CSS/JS, no external files): present mode (full-screen, arrow-key nav, Esc), Print / Save PDF, click-to-zoom lightbox, `@media print` page breaks. Slide kinds: `divider` (navy hero), `content` (header + body), `q decision` (interactive DOK question with reveal). Diagrams are original inline SVGs with `role="img"` + `aria-label`.

Builder scripts live in the working outputs folder: `build_cell.py`, `build_cell_pptx.py`, `build_tissues.py`, `gen_svgs.py` (nuclear-pore + glycocalyx SVGs), `build_found_pptx.py`. PPTX uses python-pptx, layout L5 (Title Only) for accessible titles, alt text set via the picture's `descr` attribute.

## Critical constraint: how images reach the build

Images pasted inline in chat do **not** reach the file workspace. Only two paths work:
1. **Commit the image to the A-P-lecture-core repo** as a PNG; the build clones the repo and base64-embeds it (this is how the cell models, cell junctions, and the six tissue plates got in).
2. **Upload it as a document** (PDF/PPTX) — those reach the workspace, so micrographs can be extracted from them (this is how LeBoffe Ch2 images were used).

So: to add any new image, drop the PNG in the repo with a clear filename, or upload a PDF/PPTX containing it.

## Image sources & credits

- Dr. Rennie's lab models and composite plates: `Round cell model.png`, `white cell model.png`, `Cell Junctions.png`, `tissue-epithelium-1.png`, `tissue-epithelium-2.png`, `tissue-connective.png`, `tissue-cartilage.png`, `tissue-blood.png`, `tissue-muscle.png`.
- LeBoffe histology (uploaded as PDFs/PPTX, used with permission): Ch2 (the cell), Ch3 (epithelial), Ch4 (connective). **Credit line on every LeBoffe-derived figure:** "Histology image: LeBoffe histology, adapted by Rowley. Used with permission." Tissue plates use: "Histology plate by Dr. Sharilyn Rennie. Micrographs adapted from LeBoffe histology (Rowley)."
- **Copyright rule learned:** do NOT embed figures pulled from journals/websites (ScienceDirect, cytochemistry.net) into distributed decks. When she wanted a star-shaped nuclear-pore image and a glycocalyx image from the web, we built **original SVG diagrams** instead (copyright-clean). Same approach for any future web-found figure.

## QR codes / live URLs

Each title slide carries a QR (navy on white, error-correction M, verified to decode) pointing to that deck's live Pages URL, plus a "Download the PowerPoint" link and a "download the accessible PDF from Canvas" note.

- Foundations: `https://drsrennie-stack.github.io/A-P-lecture-core/foundations-human-anatomy.html`
- Cell: `https://drsrennie-stack.github.io/A-P-lecture-core/cell-anatomy-histology.html`
- Tissues: `https://drsrennie-stack.github.io/A-P-lecture-core/tissues-histology.html`

A QR resolves only after that exact HTML file is committed and Pages rebuilds. **The repo currently holds older copies of Foundations and Cell — push the latest versions so the QRs show the updated decks, and push the Tissues files (HTML + PPTX) since they are not in the repo yet.**

## Open items / to-do

1. Push latest files to the repo: Foundations (HTML+PPTX with QR), Cell (HTML+PPTX with QR, glycocalyx + nuclear-pore SVGs, cytosol slide), Tissues (HTML now; PPTX to come).
2. Build the **Tissues PPTX** to match the HTML (mirror approach, like the cell deck).
3. Build the **Integumentary** deck (needs skin-histology source + Skin plate in repo).
4. Two typos baked into the tissue plate label images (cannot be edited inside a PNG; fix at source or rely on slide captions): "C. Fibrocartilage **Epithelium**" should be just Fibrocartilage; "C. **Cardac** Muscle Tissue" should be Cardiac.
5. Optional real micrograph swaps: if she gets rights/CC versions, a real en-face nuclear-pore TEM and a glycocalyx TEM could replace the SVGs (add to repo).
6. Write `compliance-notes.md` for Cell and Tissues (Foundations has one).

## Student-privacy rule (load-bearing)

Never store student names, IDs, grades, or other PII in any persistent file. Treat student data as session-only.
