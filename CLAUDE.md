# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a personal AI learning and experimentation workspace. Files here are standalone experiments, demos, and prototypes — not a single unified application.

## Running Files

Since there is no build system, files run directly:

- **HTML files** — open in any browser: `xdg-open tictactoe.html` (Linux) or just drag into a browser
- No install, compile, or serve step is needed for static files

## Current Contents

- [tictactoe.html](tictactoe.html) — Self-contained Tic-Tac-Toe game (pure HTML/CSS/JS, no dependencies). Includes Human vs Human, Human vs AI modes, Easy (random) and Hard (minimax + alpha-beta) difficulty, score tracking, and keyboard shortcuts (`1`–`9` for cells, `R` to restart).
