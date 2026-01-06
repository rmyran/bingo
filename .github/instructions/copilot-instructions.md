````instructions
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

React 19 + TypeScript bingo game for in-person mixers. Players mark squares to get 5 in a row. 

**Stack**: Vite 7, Tailwind v4, Vitest, ESLint flat config

**Structure**: `components/` UI | `hooks/useBingoGame` state + localStorage | `utils/bingoLogic` pure logic + tests | `data/questions` 24 questions (center is free)

**Data Flow**: `useBingoGame` hook → props/callbacks (no Context). State = `{gameState, board, winningLine, winningSquareIds, showBingoModal}`. Actions = `startGame()`, `handleSquareClick(id)`, `resetGame()`, `dismissModal()`.

**Game Logic**: 5×5 board, center (index 12) free. Win = 5 marked in row/col/diagonal. `checkBingo()` returns `BingoLine{type, index, squares}`.

## Patterns

**Add Features**: Types in `types/` → tests in `*.test.ts` → logic in `utils/` → wire via `useBingoGame` → update components → run checklist

**Styling**: Theme tokens in `src/index.css` via `@theme`. Use Tailwind v4 (`color-mix()`, `bg-black/50`). Follow [frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md) to avoid generic AI aesthetics. See [tailwind-4.instructions.md](.github/instructions/tailwind-4.instructions.md).

**Testing**: Vitest + Testing Library + jest-dom. See `utils/bingoLogic.test.ts` for examples.

## Commands
- `npm run dev` — Vite dev server
- `npm run build` — Production build
- `npm run lint` — ESLint (add `--fix`)
- `npm run test` — Run tests

**Deployment**: Push to `main` → GitHub Actions → `https://{user}.github.io/{repo}`

## Key Files
- [src/hooks/useBingoGame.ts](src/hooks/useBingoGame.ts) — State orchestration
- [src/utils/bingoLogic.ts](src/utils/bingoLogic.ts) — `generateBoard()`, `checkBingo()`, `getWinningSquareIds()`
- [src/types/index.ts](src/types/index.ts) — Types
- [src/data/questions.ts](src/data/questions.ts) — Questions (need 24)

````
