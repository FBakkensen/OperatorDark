# Changelog

## 0.2.0 — 2026-05-11

- Markdown preview styling that tracks the active theme via VS Code CSS variables — body, headings, links, inline code, code-block containers, blockquotes, tables, lists, horizontal rules, images, and `kbd`. Code-block syntax tokens are already themed by VS Code; only the container chrome is styled here.
- Hybrid width model in the markdown preview: prose (paragraphs, lists, headings, blockquotes) is bounded at ~880px for line-length readability; tables, code blocks, images, SVG / Mermaid diagrams, and horizontal rules go edge-to-edge of the editor pane.

## 0.1.0 — 2026-05-11

Initial public release.

- Single dark theme: navy-charcoal surfaces, desaturated contrast-first syntax palette
- Workbench, TextMate, and minimal semantic token coverage
- Theme-only diff colors (teal-green adds, warm coral deletes) — no companion extension required
- AL / Business Central token tuning: sage green for fields, properties, enum members, and quoted identifiers (e.g. `::"All Customers"`)
- Custom bracket pair colors: teal → amber → purple → type-blue
- Italic comments only
- Colorblind-safe color pairings — no add/delete or status pair relies on red vs green alone
