# Blood Work Tracker — Setup Guide

A self-contained HTML file for tracking lab results over time. No account required, no data ever leaves your device. This guide covers two ways to use the tracker with AI assistance, specifically configured for Anthropic's Claude. 

Before using it, read the DataPrivacy_Notice document for information about data privacy risks and best practices

Your data is saved to your browser's local storage, so it'll persist between sessions on the same device.

---


## How the tracker works

Download `blood_work_tracker.html` and open it in any modern browser (Chrome, Firefox, Safari, Edge). Your data is saved in your browser's local storage — it persists between sessions on the same machine and browser. Nothing is sent to any server except when you use the AI parse feature.

You can always add results manually: go to **+ Add**, pick a panel (CBC, Metabolic, Lipids, etc.), enter values, and click **Save entry**.

The AI-assisted options below save time when you have a lot of values to enter.

---

## Option A — Use Claude.ai directly (recommended, no setup required)

This is the easiest way to get started. You upload the tracker file into Claude, and Claude handles reading your results and populating the tracker — no API key or code editing needed.

### Step 1 — Download the tracker

Save `blood_work_tracker.html` to your computer.

### Step 2 — Open Claude.ai

Go to [claude.ai](https://claude.ai) and sign in or create a free account.

### Step 3 — Upload the tracker into a conversation

Start a new conversation. Click the **paperclip / attachment icon** in the message box and select `blood_work_tracker.html`. Then send a message like:

> "Please view this file and open the tracker so I can use it."

Claude will read the file and render an interactive version of the tracker directly in the conversation that you can open and use.

### Step 4 — Share your lab results with Claude

You can share your results in two ways:

**Paste as text.** Copy the values section from your lab portal (after removing any identifying information — see the privacy section above). Paste the text into the chat and ask:

> "Here are my CBC results from June 2026. Can you add these to the tracker?"

**Share a screenshot.** Take a screenshot of your results table, crop out any identifying header information, and attach it to the chat. Then ask:

> "Here's a screenshot of my lab results. Please populate the tracker with these values."

Claude will read the values, match them to the correct markers, and add them to the tracker automatically.

### Step 5 — Export your data for next time

Once your results are in the tracker, click **Export JSON** under **+ Add → Export / import data** to save a backup file. Next time you open the tracker in Claude, you can import this file to restore your previous entries and see trends over time.

---

## Option B — Local use with your own Anthropic API key

This option lets the tracker's built-in "Parse with AI" button work without going through Claude.ai. Everything runs locally in your browser. You pay for API usage directly (under $0.01 per parse).

### Step 1 — Get an Anthropic API key

1. Go to [console.anthropic.com](https://console.anthropic.com) and create an account
2. Navigate to **API Keys** in the left sidebar
3. Click **Create Key**, give it a name (e.g. "Blood Work Tracker"), and copy the key — it starts with `sk-ant-`
4. Add a payment method under **Billing** (you only pay for what you use — there is no subscription)

### Step 2 — Add your key to the HTML file

Open `blood_work_tracker.html` in a text editor (TextEdit on Mac, Notepad on Windows, or any code editor like VS Code).

Search for the `parsePaste` function — look for this block:

```js
const resp = await fetch('https://api.anthropic.com/v1/messages', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
```

Replace it with:

```js
const resp = await fetch('https://api.anthropic.com/v1/messages', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'x-api-key': 'YOUR_API_KEY_HERE',
    'anthropic-version': '2023-06-01',
  },
```

Swap `YOUR_API_KEY_HERE` for your actual key (keep the quotes around it). Save the file.

### Step 3 — Use the Parse with AI feature

1. Open the saved HTML file in your browser
2. Go to **+ Add**
3. Set the **Test date** and optionally the **Lab / source** name
4. Paste your lab values (plain text, identifiers removed) into the text area at the bottom
5. Click **Parse with AI ↗**
6. Your results will be saved within a few seconds and appear in the Overview

### API costs

Each parse call sends your pasted text plus a list of marker names to the Anthropic API and receives a short JSON response. Using `claude-sonnet-4-6`:

| | Rate | Typical per parse |
|---|---|---|
| Input tokens | $3.00 / 1M tokens | ~$0.005 |
| Output tokens | $15.00 / 1M tokens | ~$0.003 |
| **Total per parse** | | **~$0.008** |

A full panel (CBC + metabolic + lipids + thyroid) in a single paste is still one call — under one cent. Running labs monthly for a year costs roughly **10–15 cents total**. You can monitor usage and set spending limits at [console.anthropic.com/settings/limits](https://console.anthropic.com/settings/limits).

### Security note for your API key

Your API key is stored in plaintext inside the HTML file. This is fine for personal local use — the file stays on your machine. However:

- **Do not share this file** with your key inside it
- **Do not upload it** to GitHub, Google Drive, Dropbox, or any shared location
- **Do not host it** as a public webpage

If you want to share the template with others, share the original file without the key (or remove the key line before sharing).

---

## Exporting and backing up your data

Your data lives in your browser's local storage, which means:

- It is **browser-specific** — data in Chrome won't appear in Safari
- It is **device-specific** — data on your laptop won't appear on your phone
- It will be **lost** if you clear your browser's site data

Use the **Export JSON** button under **+ Add → Export / import data** after each session to save a backup. To restore on another device or browser, open the tracker and click **Import JSON**.

---

## Sharing the template with others

Share the original `blood_work_tracker.html` file without any API key added. Each recipient opens it in their browser, starts with a blank tracker, and chooses whichever option works for them. Their data is completely separate and private to their own browser.
