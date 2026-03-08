# ccnt - Calorie Counter

A mobile-first calorie counter web app built as a single static HTML file. No server, no frameworks, no build step.

## Features

- Track daily calorie intake with a simple +/− interface
- Food item catalog with portion sizes and calories per 100g
- Search the [Open Food Facts](https://world.openfoodfacts.org/) database to auto-fill nutrition data
- Color-coded progress bar (green → yellow → red) for daily limit tracking
- Configurable daily calorie limit
- All data stored in browser localStorage
- 10-minute merge window: consecutive taps on the same item update the existing log entry
- Log entries are denormalized — editing an item doesn't change history
- Automatic cleanup of log entries older than 30 days

## Usage

Open `index.html` in a browser. No server required.

## Data Storage

All data lives in `localStorage` under three keys:

- `ccnt_settings` — daily calorie limit
- `ccnt_items` — food item catalog
- `ccnt_log` — consumption log (pruned after 30 days)
