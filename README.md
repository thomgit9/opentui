[![Documented with Setinstone.io](https://img.shields.io/badge/⛰️Documented%20with-Setinstone.io-success?logo=book&logoColor=white)](https://calendly.com/set-in-stone-thomas-benoit/setinstone-demo)

# OpenTUI

## Presentation

**OpenTUI** is an open-source TypeScript library for building **terminal user interfaces (TUIs)**.  
It provides a modular and high-performance foundation for creating interactive CLI-based UI components and applications.  
OpenTUI aims to serve as the foundational framework for both [opencode](https://opencode.ai) and [terminaldotshop](https://terminal.shop).

This monorepo includes multiple bindings and reconcilers for various frameworks:

- [`@opentui/core`](packages/core) — The standalone core library providing primitives, an imperative API, and renderer.
- [`@opentui/solid`](packages/solid) — SolidJS reconciler for OpenTUI.
- [`@opentui/react`](packages/react) — React reconciler for OpenTUI.
- [`@opentui/vue`](packages/vue) — Vue reconciler (currently unmaintained).
- [`@opentui/go`](packages/go) — Go bindings (currently unmaintained).

Latest update: *feat(core): allow configuring cursor style* ([commit 5e41a03](https://github.com/thomgit9/opentui/commit/5e41a034a8deba3e4db566279ffa750e3dc6f6ba)) on **2025‑11‑05** by [Adictya](https://github.com/Adictya).  

License: [MIT](LICENSE)

Contributors include: [kommander](https://github.com/kommander), [msmps](https://github.com/msmps), [Adictya](https://github.com/Adictya), [fezproof](https://github.com/fezproof), [remorses](https://github.com/remorses), [bhushan6](https://github.com/bhushan6), [KurtGokhan](https://github.com/KurtGokhan), and others.

---

## Installation

> **Requirement:** You must have [Zig](https://ziglang.org/learn/getting-started/) installed on your system to build the packages.

### Using Bun (recommended)

```bash
bun install @opentui/core
```

### Quick Start with Template

You can scaffold a new TUI app using [`create-tui`](https://github.com/msmps/create-tui):

```bash
bun create tui
```

---

## Usage

### Running Core Examples (from repo root)

```bash
bun install
cd packages/core
bun run src/examples/index.ts
```

### Local Development Linking

Use the `link-opentui-dev.sh` script to test OpenTUI changes in another project without publishing.

**Basic usage:**
```bash
./scripts/link-opentui-dev.sh /path/to/your/project
```

**Options:**
- `--react` — Link `@opentui/react`
- `--solid` — Link `@opentui/solid` and `solid-js`
- `--dist` — Link `dist` directories instead of source
- `--copy` — Copy `dist` output instead of creating symlinks (requires `--dist`)

**Examples:**
```bash
./scripts/link-opentui-dev.sh /project/path              # Core only
./scripts/link-opentui-dev.sh /project/path --solid      # Link core + solid
./scripts/link-opentui-dev.sh /project/path --react --dist
./scripts/link-opentui-dev.sh /project/path --dist --copy
```

**Notes:**
- Target project must have `node_modules` initialized.
- Source mode enables hot-reloading.
- Use `--dist` when testing build artifacts.
- Use `--copy` for symlink-limited environments (e.g. Docker, Windows).

---

## Main Functions and Classes

| Name | File | Description | Inputs | Outputs |
|---|---|---|---|---|
| `Renderable` | `packages/core/src/Renderable.ts` | Base class representing a renderable terminal element. | Props (dimensions, content) | Renderable instance |
| `CliRenderer` | `packages/core/src/renderer.ts` | Main TUI renderer managing the render lifecycle in terminal. | Render tree, target stream | Renders UI in terminal |
| `Timeline` | `packages/core/src/animation/Timeline.ts` | Handles animation sequencing and synchronized transitions. | Keyframes, duration | Animation control object |
| `TextBuffer` | `packages/core/src/text-buffer.ts` | Manages text input and display buffer. | String data | Buffer object |
| `EditorView` | `packages/core/src/editor-view.ts` | Provides a full TUI editor abstraction for text editing. | Input events, buffer | Updated editable content view |
| `KeyHandler` | `packages/core/src/KeyHandler.ts` | Maps and handles keyboard input events. | Key events | Action dispatch |
| `Yoga` | `packages/core/src/index.ts` | Layout engine interface for flexbox-style terminal elements. | Layout nodes | Computed layout |
| `AppContext` | `packages/react/src/components/app.tsx` | Context managing CLI renderer and keyboard handler in React. | React context inputs | Context provider |
| `useAppContext()` | `packages/react/src/components/app.tsx` | React hook exposing the OpenTUI app context. | None | `{ keyHandler, renderer }` |
| `render()` | `packages/vue/src/renderer.ts` | Vue-specific terminal rendering entry point. | Vue component | Renders TUI app in console |
| `extend()` | `packages/vue/src/extend.ts` | Extends the Vue TUI renderer with custom renderables. | Custom components | Updated renderer registry |
| `opentui.go` | `packages/go/opentui.go` | Go bindings entry point for OpenTUI core. | Go struct definitions | Exposed TUI bindings |

---

## ⛰️ Documented With SetinStone.io
Focus on the only task that matters: building your codebase! With every developer push, Set In Stone’s Mirror Documentation Agent updates your README.md via a pull request — ready for you to review, edit, and approve.

[Book a demo](https://calendly.com/set-in-stone-thomas-benoit/setinstone-demo)