# ccnt - Simple Calorie Counter

A mobile-first calorie counter web app built as a single static HTML file. No server, no frameworks, no build step.

## Why?

The main feature of my calorie counter is spending as little time as possible on logging meals. I've tried every app out there, and they're all bloated with functionality I don't need. My goal is to limit my daily calorie intake — all I need is to log how many calories I ate after each meal. Other apps required too many steps and too much time, which eventually made me stop using them altogether. After all, we basically eat a limited set of foods, and all you need is to tap one button — I had another serving of my favorite food.

I implemented this idea in my counter: after a short initial setup period where you add your foods, daily use should take just a few seconds.

The counter resets every day.

The app works locally — no subscriptions, no sync, no bloat.

## Android / IPhone Install

Android:
1. Open Chrome: Launch the Google Chrome browser on your Android device.
2. Visit the Site: https://mylh.me/ccnt/
3. Open Menu: Tap the three-dot menu icon in the upper right corner.
4. Install App: Select "Add to Home screen" or "Install app" if a prompt appears.
5. Confirm: Tap "Add" or "Install" in the pop-up.

Iphone: To install a Progressive Web App (PWA) on an iPhone,
1. Open https://mylh.me/ccnt/ in Safari
2. tap the Share button (box with upward arrow),
3. scroll down, and select Add to Home Screen.
4. Confirm the name, then tap Add in the top-right corner to place the app icon on your home screen

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
