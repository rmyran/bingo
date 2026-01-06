---
name: copilot-instructions
description: Core workspace instructions for Copilot interactions with the Soc Ops bingo game project
---

# Soc Ops - Workspace Instructions

## ✓ Development Checklist (Required Before Commit)
- [ ] **Lint** — `npm run lint` passes without errors
- [ ] **Build** — `npm run build` succeeds with no warnings
- [ ] **Test** — `npm run test` passes all test suites

## Overview

**Soc Ops** is a React 19 + TypeScript bingo game for mixers. Players mark squares matching questions to get 5 in a row to win.

**Tech Stack**: Vite 7, Tailwind CSS v4, Vitest, ESLint, GitHub Pages deployment

### Structure
```
src/components/       # UI components
src/hooks/           # useBingoGame - state management
src/types/           # Domain types (BingoSquareData, GameState)
src/utils/           # bingoLogic.ts - win detection (tested)
src/data/            # questions.ts - question bank
```

## Key Patterns

**Game Logic**: 5x5 board with free center. Win = 5 marked squares in a row (horizontal, vertical, diagonal).

**Architecture**: 
- Components receive props & callbacks (no Context)
- `useBingoGame` hook orchestrates state
- `bingoLogic.ts` handles pure logic (unit tested)

**Adding Features**: Write tests first → implement → wire via hooks/props → run checklist

**Styling**: Use `@theme` in `src/index.css` for tokens. Leverage v4 features: `color-mix()`, opacity (`bg-black/50`), CSS variables for theming. See frontend-design.instructions.md to avoid generic AI aesthetics.

## Commands
- `npm install` — Install dependencies
- `npm run dev` — Start dev server
- `npm run build` — Production build
- `npm run lint` — Lint code (add `--fix` to auto-fix)
- `npm run test` — Run tests

## Key Files
- [src/hooks/useBingoGame.ts](src/hooks/useBingoGame.ts) — State & orchestration
- [src/utils/bingoLogic.ts](src/utils/bingoLogic.ts) — Win detection logic
- [src/types/index.ts](src/types/index.ts) — Type definitions
- [src/data/questions.ts](src/data/questions.ts) — Questions
- [src/index.css](src/index.css) — Tailwind & tokens

## References
- [frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md) — Design patterns
- [tailwind-4.instructions.md](.github/instructions/tailwind-4.instructions.md) — Tailwind v4 guide

**Deployment**: Push to `main` → auto-deploys to `https://{username}.github.io/soc-ops` via GitHub Actions
