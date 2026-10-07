# Mystery Pixel Fraction Puzzle Generator

One offline file: open `index.html` in any modern browser. No server, no account, no install.

Upload a picture (PNG, JPG or WebP), choose a grid size and up to 12 colors (snapped to a standard 12-crayon box, no in-between shades), choose the fraction questions, and get:

- a printable **student sheet** (A4 portrait, stacked fractions, color key with answer ranges),
- a colored **answer key** (optionally with each answer in its cell),
- a per-cell **answer list** (print or CSV),
- a **settings file** (JSON) that rebuilds the same puzzle.

## How answers stay correct

The engine picks each cell's answer first, then builds a problem that produces it, using whole-number
arithmetic only. Every problem is re-checked by an independent verifier (cross-multiplication, no decimals)
before the sheet is drawn; a failed problem is discarded and redrawn. If a color's answer range has no valid
problem under the chosen rules, the tool says which color and suggests a denominator instead of printing a wrong sheet.

The seed is printed on every sheet. The same picture, settings and seed always give the same puzzle.

**Check the engine** (bottom of the settings panel) builds 10,000 random puzzles and re-verifies every answer.

## Printing to PDF

Use the print buttons, then in the browser's print dialog choose **Save as PDF**, A4, portrait, and turn on
**Background graphics** so colors and black squares print.

## Scope (version 1)

English labels, A4 portrait, addition and subtraction only, no accounts or backend.
