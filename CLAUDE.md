# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

ccnt is a mobile-first calorie counter — a single static HTML file (`index.html`) with no build step, no frameworks, and no server. Just open in a browser.

## Architecture

Everything lives in `index.html`: HTML structure, CSS (`<style>`), and vanilla JS (`<script>`).

**Data layer** — All state is in `localStorage` under three keys:
- `ccnt_settings` — daily calorie limit
- `ccnt_items` — food item catalog (array of objects with id, name, portionGrams, caloriesPer100g, caloriesPerPortion)
- `ccnt_log` — consumption log entries (pruned after 30 days)

**Key behaviors:**
- 10-minute merge window (`MERGE_WINDOW`): consecutive +/− taps on the same item update the existing log entry rather than creating new ones
- Log entries are denormalized — editing a food item doesn't retroactively change historical log entries
- Food list is sorted by usage frequency (from log history)
- Food search uses the Open Food Facts API (`world.openfoodfacts.org`)

**UI pattern:** Bottom-sheet modals (`.modal-overlay` + `.modal`) for item editing and limit setting. The `render()` function rebuilds the entire food list on every state change.
