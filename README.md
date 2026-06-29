# Blood Work Tracker

A free, private blood work tracker that runs entirely in your browser. No account, no server, no data ever leaves your device.

## Features

- Track 60+ lab markers across CBC, Metabolic, Lipids, Hormones, Thyroid, and Vitamins & Minerals panels
- Visual range bars and trend charts for every marker
- Flags out-of-range values automatically
- Paste raw lab text and let AI parse it into the tracker
- Export and import your data as JSON for backup or to move between devices
- Dark mode supported

## How to use

1. Open the tracker at the link below
2. Go to **+ Add** and either enter values manually or paste raw lab text
3. Use **Export JSON** to back up your data at any time

## Privacy

All data is stored in your browser's local storage only. Nothing is sent to any server except when you use the AI paste feature, which sends your pasted lab text to the Anthropic API to extract values. No data is stored or logged by Anthropic beyond the standard API call.

## AI paste feature

The "Parse with AI" button works automatically when accessed via the live link below (no API key needed). If you download the HTML file and open it locally, you would need to add your own Anthropic API key to use that feature — though all other functionality works offline.

## Live link

👉 **[Open the tracker](https://YOUR-USERNAME.github.io/blood-work-tracker)**

*(Replace with your actual GitHub Pages URL after setup)*

## Reference ranges

All reference ranges are standard adult lab ranges. If your lab uses different ranges, you can edit the `PANELS` object at the top of `index.html`.
