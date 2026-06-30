# Blood Work Tracker — Setup Guide

A self-contained HTML file for tracking lab results over time. No account required, no data ever leaves your device. This guide covers two ways to use the tracker with AI assistance, plus important guidance on protecting your health data before you start.

---

## ⚠️ Privacy & safety — read before sharing any health data

Lab results are medical records. Before sharing them with any AI tool — including Claude — it is worth taking time to understand what the risks actually are, where your data goes, and how to protect yourself.

### The core problem: AI chatbots are not covered by HIPAA

HIPAA — the Health Insurance Portability and Accountability Act — restricts how hospitals, insurers, and healthcare providers handle your medical data. It does not apply to AI companies. When you share a lab report with Claude, ChatGPT, Perplexity, or any other consumer AI chatbot, you are outside the legal protections that govern your doctor's office or your insurance company. The company's own privacy policy is the only thing governing what happens to your data, and those policies vary widely and can change.

A 2024 KFF survey found that most Americans are concerned about the privacy of their medical data when using AI tools — and that concern is well founded. The risks fall into a few categories.

### Risk 1: Training data

Most AI companies reserve the right to use conversations to improve their models, unless you explicitly opt out. If you paste your lab results into a chat without opting out, those values — potentially alongside other things you've shared in the conversation — could become part of future training data. Even if individual data points seem innocuous, aggregated health conversations at scale can reveal sensitive patterns.

What to do: On claude.ai, go to **Settings → Privacy** and disable the option that allows your conversations to be used for model training. Do this before sharing any health information.

### Risk 2: Data breaches and retention

Your conversation is stored on the AI company's servers for some period of time — sometimes indefinitely unless you manually delete it. AI companies are increasingly high-value targets for data breaches. Health data is particularly sensitive because, unlike a compromised password, you cannot change your blood values or your medical history.

What to do: Delete conversations containing health data after you are done with them. On claude.ai, you can delete individual conversations from the sidebar. Do not assume deletion is immediate or that it removes data from all backup systems.

### Risk 3: Re-identification from "anonymous" data

It is a common misconception that removing your name from a lab report makes it anonymous. Research has repeatedly shown that health data can be re-identified with surprisingly little additional information — your age, zip code, and a handful of biomarker values can be enough to narrow down your identity, particularly in smaller populations. A dataset that looks anonymous in isolation rarely stays that way when combined with other data sources.

What to do: Only share the numeric values you actually need the AI to process. The more context you strip away — dates, demographics, conditions, medications — the harder re-identification becomes.

### Risk 4: No guarantee of accuracy

AI models can misread, misparse, or misattribute lab values, especially from PDFs, screenshots, or non-standard lab formats. An error in parsing is usually obvious (a missing value), but a subtle numeric error — transposing digits, for example — could go unnoticed and affect how you interpret your trends over time. The tracker displays what it is given; it does not validate whether the values are medically plausible.

What to do: Always cross-check the values that appear in the tracker against your original lab report before relying on them. Never use this tool to make clinical decisions — it is a personal tracking aid, not a diagnostic tool.

### Risk 5: Secondary use by third parties

Some AI platforms share data with third-party partners for analytics, advertising, or product improvement purposes. Even if the primary AI company has a reasonable policy, data passed to downstream vendors may be subject to less stringent terms.

What to do: Read the privacy policy of any AI tool before sharing health data. Look specifically for clauses about third-party sharing, data retention periods, and your rights to deletion.

---

### What counts as protected health information (PHI)

PHI is any information that could identify you alongside a health detail. In a typical lab report this includes your full name, date of birth, address, phone number, patient ID or account number, ordering physician's name, the name and address of the lab or clinic, insurance information, and the date of service.

The numeric lab values themselves — a number like "WBC: 5.6" — are not inherently identifying on their own. The risk comes from combining them with identifiers, and from aggregating enough data points that re-identification becomes possible.

---

### Best practices before sharing lab data with any AI

**Remove all identifying information before pasting or uploading.** Delete your name, date of birth, patient ID, doctor's name, and lab facility name before sharing anything. Replace them with placeholders like `[REDACTED]` or simply delete them. The numeric values and marker names are all this tracker needs.

**Do not upload raw PDF lab reports.** PDFs from labs almost always contain your full name, date of birth, address, account number, and ordering physician embedded in the document header, footer, and metadata — even if they are not visible on screen. Uploading a PDF hands the AI company the entire file. Instead, copy and paste only the values section as plain text after reviewing it for identifiers.

**Crop screenshots carefully.** If you take a screenshot of your results, crop it to show only the values table. Lab report headers typically contain your name, DOB, patient number, and the ordering physician's details — none of which the tracker needs.

**Opt out of model training before you start.** On claude.ai: **Settings → Privacy → turn off conversation training**. On other platforms, look for equivalent settings — they are not always easy to find.

**Delete conversations when you are done.** Don't leave conversations containing health data sitting in your chat history.

**Only share what you need.** You can manually type in only the markers you want to track and leave everything else out. The tracker works fine with partial data.

**Treat AI output as a starting point, not a source of truth.** Always verify parsed values against your original report.

---

### Further reading

The risks of sharing health data with AI tools are an active area of public concern and ongoing reporting. The following resources provide useful context:

- KFF Tracking Poll — *Privacy Concerns and Uploading Personal Medical Data to AI* (2024): [kff.org](https://www.kff.org/public-opinion/kff-tracking-poll-on-health-information-and-trust-use-of-ai-for-health-information-and-advice/#c828efc6-7c8a-4a17-bf44-8a391004ee26--h-privacy-concerns-and-uploading-personal-medical-data-to-ai)

- Wall Street Journal — *Your Health Data and AI Chatbots*: [wsj.com](https://www.wsj.com/tech/ai/health-data-perplexity-claude-ai-d792a2df?mod=Searchresults&pos=1&page=1)

- New York Times — *Should You Share Your Medical Records with a Chatbot?* (December 2025): [nytimes.com](https://www.nytimes.com/2025/12/03/well/medical-records-chatbots.html)

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
