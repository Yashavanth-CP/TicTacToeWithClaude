# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A browser-based Tic-Tac-Toe game built as a single self-contained HTML file (`tictactoe.html`). Pure HTML/CSS/JS — no frameworks, no dependencies, no build step.

## Running

Open `tictactoe.html` directly in any browser. No server, install, or compile step needed.

```bash
xdg-open tictactoe.html   # Linux
open tictactoe.html        # macOS
```

## Architecture

Everything lives in a single file with three sections:

1. **`<style>`** — Dark-themed CSS using CSS custom properties (`:root` vars). 3×3 CSS Grid board, radio-pill selectors, responsive layout. Winning cells use a `pulse` keyframe animation and colored `box-shadow` glow.

2. **HTML body** — Static skeleton: mode selector (HvH / HvAI), difficulty selector (Easy / Hard, hidden in HvH mode), scoreboard (X / Draws / O), status bar, board container (`#board`), restart button.

3. **`<script>`** — Vanilla JS with clear sections:
   - **State**: `board` (string[9]), `currentPlayer`, `gameOver`, `mode`, `difficulty`, `scores`, `aiThinking`
   - **Core logic** (pure functions): `checkWinner()` checks 8 win lines, `isDraw()`, `getEmptyCells()`
   - **AI**: `easyMove()` picks random empty cell; `hardMove()` uses minimax with alpha-beta pruning (AI plays O, maximizing)
   - **Rendering**: `buildBoard()` rebuilds the 9 cell buttons on every state change; `highlightWin()` adds `.winning` CSS class to winning cells
   - **Game flow**: `applyMove()` is the central dispatch — places mark, checks win/draw, switches turn, triggers AI if needed
   - **Controls wiring**: radio change listeners reset the game; keyboard shortcuts (`1`–`9` for cells, `R` to restart)

## Key Design Decisions

- The board is rebuilt from scratch on every move (`buildBoard()` clears innerHTML). This keeps rendering simple at the cost of minor DOM churn — acceptable for a 9-cell grid.
- AI moves have a 200ms `setTimeout` delay so they don't feel instant.
- Human is always X, AI is always O. Scores persist across rounds until page refresh.
