# Accessibility Compliance Notes

**Project:** A&P Lecture Core, Integumentary deck and related edits
**Files covered:** integumentary-anatomy-histology.html (new); foundations-human-anatomy.html and tissues-histology.html (edits)
**Date:** June 13, 2026
**Reviewer:** Dr. Sharilyn Rennie

## 1. WCAG version and target
WCAG 2.2 AA is the floor; AAA targeted on text contrast. The Integumentary deck reuses the verified deck shell (same semantic structure, skip link, keyboard lightbox, present-mode navigation, aria-live answer reveals, reduced-motion support) used by the Foundations, Cell, and Tissues decks.

## 2. Color contrast
Palette is the PRIMARY teaching set only (Navy #0B1530, Rust #8B3A2E, Brushed gold #C9A14A/#DCB45C/#B8924A, white, off-white #FAFAF9). No sage, no cream. Body navy text on white and off-white exceeds 7:1. White text on rust #8B3A2E and on navy exceeds 4.5:1 for the large/heading uses where applied. The field-guide cards use navy on gold for the epithelium header (dark on light gold) and white on rust/navy for the others, all passing AA for their sizes.

## 3. Keyboard navigation
Present mode is fully keyboard operable (Enter/arrow keys/Esc). Every interactive element (Present, Print/Save PDF, practice-question choices, lightbox open/close) is reachable by Tab and operable by Enter/Space. Visible focus is retained from the shared shell.

## 4. Screen reader
Tested against the shared shell behavior: section landmarks per slide with descriptive aria-labels, heading hierarchy h1 (page) > h2 (slide title) > h3 (sub-blocks), real text throughout (no text-as-image), and full alt text on all eight images in the Integumentary deck (the labeled skin model, the epidermal strata model, the thin/thick skin micrographs, and the hair model). Answer reveals use aria-live.

## 5. Edits to existing decks
- foundations-human-anatomy.html: added the Print / Save PDF button, its @media print rule, and its handler to match the Cell and Tissues decks. No content change.
- tissues-histology.html: added one "complete tissue field guide" slide (accessible HTML cards, real text, prints in two columns) and removed two stray em dashes from the SVG algorithm labels. No images altered.

## 6. Known limitations
- The thin/thick skin micrograph alt text describes the visual pattern; if a specific source credit is required, add it to the caption before distribution.
- Visual render was validated structurally (balanced markup, QR decodes to the correct live URL, no missing alt) but not screenshot-verified in a browser in this session. Recommend one pass in Present mode and one Print preview before pushing.

## 7. Reviewer
Dr. Sharilyn Rennie
