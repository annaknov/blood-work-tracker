# Blood Work Tracker

A single-file, self-contained HTML app for tracking your lab results over time. No server, no account, no app to install — just open the file in a browser.

![Blood Work Tracker screenshot](https://i.imgur.com/placeholder.png)

## Features

- **Track 70+ markers** across CBC, Metabolic, Lipids, Hormones, Thyroid, and Vitamins & minerals panels
- **Trend charts** for every marker across visits
- **Out-of-range alerts** highlighted on the overview
- **AI-powered paste parsing** — paste raw lab text and Claude extracts the values automatically
- **Manual entry** for any panel and date
- **Export / import** your data as JSON for backup or moving between devices
- **Dark mode** support
- **Zero dependencies** except Chart.js (loaded from CDN) and an internet connection for AI parsing

## Getting started

1. Download `index.html`
2. Open it in any browser (Chrome, Firefox, Safari, Edge)
3. Go to **+ Add** and enter your first lab results

That's it. Your data is saved in your browser's localStorage — it stays on your device.

## Adding results

**Manual entry** — choose a date, lab name, and panel, then fill in the values you have. You don't need to fill everything; leave blank what you don't have.

**AI paste parsing** — copy the text from your lab portal or PDF and paste it into the text box. The app uses the Claude API to extract and match values automatically. This requires an internet connection.

## Backing up your data

Use **Export JSON** in the + Add tab to download all your data as a file. Use **Import JSON** to restore it on another device or browser. Exports are plain JSON so you can inspect or edit them in any text editor.

## Sharing / deploying

Since it's a single HTML file you can:

- Host it on **GitHub Pages** — push to a repo, enable Pages, done
- Drop it in **Dropbox / Google Drive** and open with a browser
- Self-host on any static file server

## Customizing reference ranges

Reference ranges in the file are general population defaults. Labs use different ranges depending on the machine and population — always check your own lab's printed reference intervals. To edit ranges, open `index.html` in a text editor and find the `PANELS` object near the top of the `<script>` section. Each marker looks like:

```js
{ key: 'wbc', name: 'WBC', unit: 'K/μL', low: 4.0, high: 11.0 }
```

Change `low` and `high` to match your lab's values.

## Privacy

All data is stored in your browser's localStorage. Nothing is sent anywhere except when using the AI paste feature, which sends your pasted text to the Anthropic API. No account or login is required.

## License

MIT — do whatever you want with it.
