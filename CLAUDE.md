# Operator Dark — VS Code Color Theme

## What this is

A VS Code color theme extension. Navy-charcoal surfaces, desaturated contrast-first syntax, restrained teal/amber accents. Designed for long sessions.

## Project structure

```
package.json                              — Extension manifest (local-only, no publisher)
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
| Layers | All three: workbench colors, TextMate tokenColors, semantic tokens |
| Diff approach | Theme-only (no companion extension), teal-green adds / warm coral deletes |
| ANSI terminal | Faithful to design palette, not stock-saturated |
| Italics | Comments only |
| Bracket colors | Custom: teal → amber → purple → type-blue |
| AL tokens | Semantic overrides for property/method/field (sage green `#B7D6A6` for `member:al`) |
| Packaging | Local-only — no marketplace publisher yet |

## Colorblind safety rule

**Never use red/green as the sole differentiator between two states.** This applies everywhere — workbench UI, syntax tokens, diff colors, terminal ANSI, git decorations, diagnostics, and any future additions. Every color pair that encodes meaning (add/delete, success/error, modified/untracked, valid/invalid) must be distinguishable across deuteranopia, protanopia, and tritanopia. The current palette uses teal-green (`#88D8AE`) vs warm coral (`#E89A95`) for diffs and green vs amber for git status — both pass this test. If adding new semantic color pairs, verify contrast across all three deficiency types before committing.

## Color palette reference

| Token | Hex | Role |
|---|---|---|
| `--nf-activity` | `#0F1822` | Activity bar |
| `--nf-sidebar` | `#131D29` | Sidebar, panels, tab bar |
| `--nf-editor` | `#182433` | Editor background |
| `--nf-titlebar` / `--nf-status` | `#111B26` | Title bar, status bar |
| `--nf-fg` | `#D0DCE7` | Primary foreground |
| `--nf-fg-mute` | `#94A3B5` | Muted text |
| `--nf-fg-faint` | `#6B7989` | Faint text, line numbers |
| `--nf-fg-bright` | `#ECF2F8` | Bright / active foreground |
| `--nf-teal` | `#6CC9C7` | Primary accent |
| `--nf-amber` | `#DEB071` | Secondary accent, strings |
| `--nf-keyword` | `#BAA1E0` | Keywords, storage |
| `--nf-ctrl` | `#CC9DD8` | Control flow |
| `--nf-fn` | `#88D8D8` | Functions, methods |
| `--nf-type` | `#95BFE0` | Types, classes |
| `--nf-prop` | `#E2B999` | Properties |
| `--nf-field` | `#B7D6A6` | AL fields (sage green) |
| `--nf-num` | `#E5BC81` | Numbers, constants |
| `--nf-comment` | `#74849A` | Comments (italic) |
| `--nf-error` | `#E89A95` | Errors, deletions |
| `--nf-warn` | `#DEB071` | Warnings |
| `--nf-info` | `#6CC9C7` | Info |

## Design source

The `.claudedesign/` folder (gitignored) contains the original Claude Design export with HTML/CSS prototypes and chat transcripts. The chat transcripts document every design iteration — read them if revisiting color choices.

## Future scope (not started)

- Companion extension for colorblind-friendly diff decorations (glyph markers, pattern fills)
- Theme variants (Darker, Warm)
- Marketplace publishing (publisher ID, icon, README, screenshots)
