# Changelog

## 0.3.0 — 2026-05-11

- Menus join the popup-surface family. New keys for `menu.*` and `menubar.selection*` so the File / Edit / View dropdowns now use the same `#0B121C` floating-panel surface as the command palette, suggest widget, hover widget, notifications, and peek view. Previously menus fell back to VS Code defaults.
- Command palette polish: focused row foreground brightens to `#F5F9FC` (`quickInputList.focusForeground` / `focusIconForeground`), picker group headers render in teal (`#6CC9C7`) as subsection landmarks consistent with markdown H2-H6, and filter-match characters get the editor's amber find-match tint via `list.filterMatchBackground`.
- Keyboard shortcut chips themed as quiet metadata via `keybindingLabel.*`. Muted `#94A3B5` text on a barely-there pill instead of bright default white, so command names stay the primary read.
- List hover unified with list selection. `list.hoverBackground` and `list.hoverForeground` now match the keyboard-focus tint, so the command palette, file explorer, and any other list show the same visual highlight under either mouse or keyboard input.
- Menu item highlight tuned for the narrower row geometry: `menu.selectionBackground` uses 50% teal (`#6CC9C780`) so hover and keyboard navigation in dropdowns register clearly against the dark popup surface.

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
