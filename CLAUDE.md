# Operator Dark — VS Code Color Theme

## What this is

A VS Code color theme extension. Navy-charcoal surfaces, desaturated contrast-first syntax, restrained teal/amber accents. Designed for long sessions.

## Project structure

```
package.json                              — Extension manifest (publisher `fbakkensen`, published to VS Code Marketplace)
themes/operator-dark-color-theme.json     — The theme (workbench + tokenColors + semanticTokenColors)
.claudedesign/                            — Source design from Claude Design (gitignored)
```

## How to install locally

Junction into VS Code's extension folder:

```powershell
New-Item -ItemType Junction -Path "$env:USERPROFILE\.vscode\extensions\operator-dark" -Target (Resolve-Path .).Path
```

Reload VS Code, then `F1` → `Preferences: Color Theme` → **Operator Dark**.

## How to validate

```powershell
# JSON parses cleanly
Get-Content package.json | ConvertFrom-Json | Out-Null
Get-Content themes/operator-dark-color-theme.json | ConvertFrom-Json | Out-Null
```

No build step. No dependencies. Edit the JSON, reload VS Code (`Developer: Reload Window`), see changes.

## Design decisions (locked in)

| Decision | Choice |
|---|---|
| Theme count | Single `Operator Dark` — no variants |
| Layers | All three: workbench colors, TextMate tokenColors, minimal semantic tokens |
| Diff approach | Theme-only (no companion extension), teal-green adds / warm coral deletes |
| ANSI terminal | Faithful to design palette, not stock-saturated |
| Italics | Comments only |
| Bracket colors | Custom: teal → amber → purple → type-blue |
| Semantic approach | Explicit semantic entries for `function`, `method`, `builtinfunctions` (+ AL variants), `decorator`, `comment`, `variable:al`, `property:al`, `enumMember:al`. Bypasses TextMate fallback for critical token types to avoid scope-suffix matching issues with AL extension |
| AL tokens | Sage green `#8CB87E` for `variable:al` (field references), `property:al`, `enumMember:al`, and TextMate `identifier.quoted.double.al` (covers quoted enum values like `::"All Customers"`) |
| Packaging | VS Code Marketplace, publisher `fbakkensen`, released since 0.2.0. Local install via the junction in "How to install locally" still works for development |

## Colorblind safety rule

**Never use red/green as the sole differentiator between two states.** This applies everywhere — workbench UI, syntax tokens, diff colors, terminal ANSI, git decorations, diagnostics, and any future additions. Every color pair that encodes meaning (add/delete, success/error, modified/untracked, valid/invalid) must be distinguishable across deuteranopia, protanopia, and tritanopia. The current palette uses teal-green (`#88D8AE`) vs warm coral (`#E89A95`) for diffs and green vs amber for git status — both pass this test. If adding new semantic color pairs, verify contrast across all three deficiency types before committing.

## Color palette reference

| Token | Hex | Role |
|---|---|---|
| `--nf-activity` | `#0F1822` | Activity bar |
| `--nf-sidebar` | `#131D29` | Sidebar, panels, tab bar |
| `--nf-editor` | `#121C28` | Editor background |
| `--nf-titlebar` / `--nf-status` | `#111B26` | Title bar, status bar |
| `--nf-fg` | `#ECF2F8` | Primary foreground (default text) |
| `--nf-var` | `#B5C2D0` | Variables, parameters, properties (slate blue) |
| `--nf-fg-mute` | `#94A3B5` | Muted text |
| `--nf-fg-faint` | `#6B7989` | Faint text, line numbers |
| `--nf-fg-bright` | `#F5F9FC` | Bright / active foreground |
| `--nf-teal` | `#6CC9C7` | Primary UI accent (links, focus, decorators) |
| `--nf-amber` | `#DEB071` | Strings |
| `--nf-keyword` | `#9B7FD4` | Keywords, storage |
| `--nf-ctrl` | `#C9A6E8` | Control flow |
| `--nf-fn` | `#E8B49B` | Functions, methods, tags (warm peach) |
| `--nf-type` | `#95BFE0` | Types, classes |
| `--nf-field` | `#8CB87E` | AL fields (sage green) |
| `--nf-num` | `#F0D0A0` | Numbers, constants |
| `--nf-comment` | `#74849A` | Comments (italic) |
| `--nf-error` | `#E89A95` | Errors, deletions |
| `--nf-warn` | `#DEB071` | Warnings |
| `--nf-info` | `#6CC9C7` | Info |

## Design source

The `.claudedesign/` folder (gitignored) contains the original Claude Design export with HTML/CSS prototypes and chat transcripts. The chat transcripts document every design iteration — read them if revisiting color choices.

## Future scope (not started)

- Companion extension for colorblind-friendly diff decorations (glyph markers, pattern fills)
- Theme variants (Darker, Warm)
