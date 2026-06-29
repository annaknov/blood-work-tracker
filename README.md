# Blood Work Tracker — Setup Guide

A self-contained HTML file for tracking lab results over time. No account required, no data ever leaves your device. This guide covers two ways to use the "Parse with AI" feature, which reads raw lab text and fills in your results automatically.

---

## How the tracker works

Open `blood_work_tracker.html` in any modern browser (Chrome, Firefox, Safari, Edge). Your data is saved in your browser's local storage — it persists between sessions on the same machine and the same browser. Nothing is sent to any server except when you use the AI parse feature.

You can always add results manually: go to **+ Add**, pick a panel (CBC, Metabolic, Lipids, etc.), enter values one by one, and click **Save entry**.

The AI parse feature is optional but saves significant time — paste a block of raw text copied from your lab portal or PDF and it extracts and maps every value automatically.

---

## Option A — Local use with your own Anthropic API key

This option runs entirely on your own machine. You pay for API usage directly (roughly $0.01 per parse — see costs below).

### Step 1 — Get an API key

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

Swap `YOUR_API_KEY_HERE` for your actual key (keep the quotes around it).

Save the file and open it in your browser. The **Parse with AI** button will now work.

### Step 3 — Use the AI parse feature

1. Copy your lab results from your lab portal (Quest, Labcorp, etc.) or a PDF — any format works, including tables, plain lists, or messy text with reference ranges mixed in
2. In the tracker, go to **+ Add**
3. Set the **Test date** and optionally the **Lab / source** name
4. Paste your copied text into the large text area at the bottom
5. Click **Parse with AI ↗**
6. Within a few seconds, your results will be saved and appear in the Overview

### API costs

Each parse call sends your pasted text plus a list of marker names to the Anthropic API, then receives a short JSON response. Using `claude-sonnet-4-6`:

| | Rate | Typical per parse |
|---|---|---|
| Input tokens | $3.00 / 1M tokens | ~$0.005 |
| Output tokens | $15.00 / 1M tokens | ~$0.003 |
| **Total per parse** | | **~$0.008** |

A full panel (CBC + metabolic + lipids + thyroid) pasted at once is still a single call — under one cent. Running labs monthly for a year costs roughly **10–15 cents total**.

You can monitor usage and set spending limits at [console.anthropic.com/settings/limits](https://console.anthropic.com/settings/limits).

### Security note

Your API key is stored in plaintext inside the HTML file. This is safe for **personal local use** — the file stays on your machine and the key is never exposed to anyone else. However:

- **Do not share this file** with your key inside it
- **Do not upload it** to GitHub, Google Drive, Dropbox, or any public or shared location
- **Do not host it** as a public webpage

If you want to share the template with others, share the original file **without** a key inside it (or delete the key line before sharing).

---

## Option B — Upload to Claude.ai (no API key needed)

If you have a Claude.ai account (Free, Pro, or Team), you can upload the HTML file directly into a conversation and Claude will act as the AI backend. No API key setup required.

### Step 1 — Open Claude.ai

Go to [claude.ai](https://claude.ai) and sign in. Any plan works, including the free tier (though free accounts have message limits per day).

### Step 2 — Upload your tracker file

Start a new conversation. Click the **paperclip / attachment icon** in the message input area and select `blood_work_tracker.html`.

### Step 3 — Ask Claude to parse your results

Paste your lab results into the chat alongside a message like:

> "Here are my lab results from [date]. Can you parse these and give me the values formatted so I can paste them into my blood work tracker?"

Claude will read the file to understand what markers the tracker uses, then return a clean list of key-value pairs matched to the tracker's format.

### Step 4 — Add the parsed values to your tracker

With the values Claude returns, go to **+ Add** in your tracker, choose the matching panel, and enter the numbers. Or ask Claude to format them as tracker-compatible JSON and use the **Import JSON** button under **Export / import data**.

### Alternatively — use the paste feature with Claude's help first

You can also use Claude.ai to clean up messy lab text before pasting it into the tracker's AI parse box:

1. Share your raw lab text with Claude in the chat
2. Ask it to reformat the results as a simple list: `Marker Name: value unit`
3. Copy Claude's cleaned output
4. Paste that into the tracker's paste box and use **Parse with AI** (requires Option A key)

---

## Exporting and backing up your data

Your data lives in your browser's local storage, which means:

- It is **browser-specific** — data in Chrome won't appear in Safari
- It is **device-specific** — data on your laptop won't appear on your phone
- It can be **cleared** if you clear your browser's site data

To back up or move your data, use the **Export JSON** button under **+ Add → Export / import data**. This saves a `.json` file with all your entries. To restore it on another device or browser, open the tracker there and click **Import JSON**.

It is good practice to export a backup after each time you add new results.

---

## Sharing the template with others

Share the original `blood_work_tracker.html` file (without any API key added). Recipients open it in their browser and start with a blank tracker. They can either add their own API key (Option A) or use Claude.ai to help parse results (Option B).

The tracker uses a localStorage key of `bloodwork_v1` — each person's data is completely separate and private to their own browser.
