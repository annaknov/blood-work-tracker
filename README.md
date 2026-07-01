# Blood Work Tracker — Setup Guide

<<<<<<< HEAD
A self-contained HTML file for tracking lab results over time. No account required, no data ever leaves your device.
=======
A self-contained HTML file for tracking lab results over time. No account required, no data ever leaves your device. This guide covers two ways to use the tracker with AI assistance, specifically configured for Anthropic's Claude. 

Before using it, read the DataPrivacy_Notice document for information about data privacy risks and best practices
>>>>>>> 4dc22d914f8d6028e12a7522bd761c2e49127eb4

---

## How the tracker works

Download `blood_work_tracker.html` and open it in any modern browser (Chrome, Firefox, Safari, Edge). Your data is saved in your browser's local storage — it persists between sessions on the same machine and browser. Nothing is ever sent to any server.

The tracker covers CBC, Metabolic, Lipids, Hormones, Thyroid, and Vitamins & minerals panels. Out-of-range values are flagged on the Overview tab based on the reference ranges from your most recent lab test.

---

## Option A — Let Claude fill it in (recommended, no setup required)

This is the easiest way to get started. You upload the tracker file and your lab report into Claude, and Claude reads your results and populates the tracker for you.

### Step 1 — Download the tracker

Save `blood_work_tracker.html` to your computer.

### Step 2 — Open Claude.ai

Go to [claude.ai](https://claude.ai) and sign in or create a free account.

### Step 3 — Upload the tracker and your lab results

Start a new conversation. Click the **paperclip / attachment icon** and attach both:
- `blood_work_tracker.html`
- Your lab report (screenshot, PDF, or copied text)

Then send a message like:

> "Please fill in this blood work tracker with the values from my lab report and return the updated file."

Claude will read your results, match them to the correct markers, extract the reference ranges from your report, and return a populated version of the tracker. Download the file it returns and open it in your browser.

### Step 4 — Adding future results

Each time you get new labs, repeat the process — upload the current tracker file alongside your new results and ask Claude to add the new entry. Your history and trends will build up over time.

### Step 5 — Back up your data

Once results are in the tracker, click **Export JSON** under **+ Add → Export / import data** to save a backup file. You can import this file to restore your data at any time.

---

## Option B — Enter values manually

If you prefer to enter values yourself, the tracker has a built-in form for every panel.

### Step 1 — Open the tracker

Open `blood_work_tracker.html` in your browser.

### Step 2 — Go to the + Add tab

Select the **test date** and optionally the **lab name** (e.g. Quest, Labcorp). Then choose a **panel** from the dropdown — CBC, Metabolic, Lipids, etc.

Input fields will appear for every marker in that panel. Enter the values from your lab report and click **Save entry**. Repeat for each panel you have results for.

### Step 3 — Set reference ranges (optional)

The tracker comes pre-loaded with reference ranges from the **NBME Laboratory Reference Values** (the standard reference table used in US medical licensing exams). These apply to adult males where sex-specific values are given.

If your lab report uses different ranges, you can update them in the **⚙ Ranges** tab:

1. Find the marker you want to update
2. Edit the **Low** and **High** values directly in the table
3. Click **Save changes**

The source column shows where each range came from — NBME default, your most recent lab result, or manually entered. Once you update a range manually, it won't be overwritten by future lab results. Use the **↺** button next to any row to restore it to the NBME default.

---

## Exporting and backing up your data

Your data lives in your browser's local storage, which means:

- It is **browser-specific** — data in Chrome won't appear in Safari
- It is **device-specific** — data on your laptop won't appear on your phone
- It will be **lost** if you clear your browser's site data

Use the **Export JSON** button under **+ Add → Export / import data** after each session to save a backup. To restore on another device or browser, open the tracker and click **Import JSON**.

---

## Sharing the template with others

Share the original `blood_work_tracker.html` file as downloaded. Each recipient opens it in their browser, starts with a blank tracker, and their data is completely separate and private to their own browser.
