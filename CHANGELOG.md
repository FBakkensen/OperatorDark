# Changelog

## 0.5.0 — 2026-05-11

- Editor sticky scroll themed (`editorStickyScroll.*`). Function and class headers that stick at the top of the editor when scrolling deep blend with the editor surface `#121C28` and gain a subtle border underneath.
- Snippet tabstops use the teal focus accent. Active placeholders show 10% teal fill with a 25% teal border, final tabstops are fainter, same focus semantic as the cursor.
- Lightbulb code-action icons mapped to three semantics: amber for the standard lightbulb, diff-add green `#88D8AE` for auto-fix (safe to apply), and teal for AI-suggested fixes (distinct accent for AI-flavored actions).
- Banner (deprecation strips, untrusted-workspace prompts, etc.) themed as a quiet amber pill: 25% amber background, bright foreground, amber icon.
- Panel polish: `panel.dropBorder`, `panelTitle.border`, `panelSection.*`, `panelSectionHeader.*`, and `panelStickyScroll.*` now on-theme. Ports view running-process icon uses the diff-add green.
- Terminal extras: selection background matches the editor's teal selection, find-match uses the editor's amber find color, `terminalCommandDecoration.successBackground/errorBackground` follow the diff-add green / coral colorblind-safe pair instead of the default red/green. Terminal tab active border uses teal.
- GitHub Copilot surfaces themed. Ghost text (inline suggestions) renders in faint `#6B7989` to stay clearly distinct from committed code. Inline chat joins the popup family at `#0B121C` with teal focus border and subtle inline-diff tint (15% teal-green inserted, 15% coral removed). Chat panel slash commands render as teal pills via `chat.slashCommand*`, edited-file indicators use amber.

## 0.4.0 — 2026-05-11

- Extensions panel themed. Install / Manage buttons reuse the workbench `button.*` family (primary teal `#4A9897` with full teal hover), remote badge picks up `badge.background`, verified-publisher icon uses teal (trust), pre-release and rating-star icons use amber, sponsor heart uses coral. Previously the prominent Install button rendered in the default green that fought the rest of the palette.
- Run & Debug view themed with a tri-color state vocabulary. Toolbar actions use teal for forward motion (play, step, restart, start), amber for pause, coral for stop, muted grey for disconnect. Breakpoints render in coral for active, muted for disabled and unverified, teal for the current stack frame position. Exception and state labels reuse the `inputValidation.*` pill pattern (25% alpha tint over the surface, bright matching foreground). Variable inspector tokens reuse the editor's syntax token colors via `debugTokenExpression.*`.
- Source Control commit graph branch lines use the bracket-pair cycle plus coral as the fifth: teal, amber, soft-purple, type-blue, coral. Same five-color rhythm the eye already learns from editor brackets, applied to the SCM graph. `scmGraph.historyItem*` hover surfaces reuse the established additions-green and deletions-coral.
- Sidebar drop indicator (`sideBar.dropBackground`) themed with the standard 10% teal hover tint. Sticky scroll (`sideBarStickyScroll.*`) blends with the sidebar surface `#131D29` with a subtle border underneath; deliberately not lifted to the popup `#0B121C` surface because sticky scroll is persistent navigation, not a dismissable popup.
- Inactive tree indent guides themed at `#FFFFFF08`, slightly fainter than the active `#FFFFFF14` already in use.

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
