# Mystery Pixel Fraction Puzzle Generator

One offline file: open `index.html` in any modern browser. No server, no account, no install.

Upload a picture (PNG, JPG or WebP), choose a grid size and up to 12 colors (snapped to a standard 12-crayon box, no in-between shades), choose the fraction questions, and get:

- a printable **student sheet** (A4 portrait, stacked fractions, color key with answer ranges),
- a colored **answer key** (optionally with each answer in its cell),
- a per-cell **answer list** (print or CSV),
- a **settings file** (JSON) that rebuilds the same puzzle.

## Type what to draw

Instead of uploading, choose **Type what to draw** and type a word such as `cat`, `rocket` or `es krim`.

- **36 built-in pixel pictures** (animals, fruit, vehicles, weather, toys and more) work offline. They use
  only crayon colors with a black outline, and land on the grid one square per pixel, so they are always clear.
  English and common Indonesian words are understood.
- **Draw anything with AI** (optional, needs internet): pick an AI service, paste its API key, and the tool asks
  it to draw the subject as crayon-color pixel art (12×12 to 24×24).
  - **Google Gemini**: free tier with daily limits (free key at aistudio.google.com).
  - **OpenRouter**: some models are free (names end in `:free`); the model list loads automatically, free first.
  - **OpenCode Zen**: some models are free; press "Load models".
  - **Anthropic (Claude)** and **OpenAI**: paid. Claude offers the latest models (Fable 5.1, Opus 5.5 recommended,
    Sonnet 5.5, Haiku 5.5) and older ones still served.
  - **Other (OpenAI-compatible)**: any `/v1` address, such as Groq or a local Ollama.

  Every service has a model list, "Load models" (lists what your key can use), and a box to type any model name.
  Keys go only to the chosen service, are never put in saved settings files, and are remembered on the computer
  only if you tick the box. The official Anthropic SDK (MIT License) is bundled for Claude; other services are
  called over their standard web APIs. Small and free models draw less reliably than large ones.

## How pictures are turned into squares

- The background is found from the picture's edges (plain, gradient or colored) and removed, so only the
  outside becomes black squares. White parts inside the picture stay as a "White: leave uncolored" color.
- The picture is trimmed to the subject, and the rows are matched to its shape.
- Every pixel votes for its nearest crayon (matched by hue first, so shaded colors keep their color);
  each square takes the winning crayon. No averaged "mud" colors.
- Black outlines become black squares, and stray single squares are cleaned up.
- Pixel art (small, or saved enlarged) gets exactly one square per art pixel.

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
