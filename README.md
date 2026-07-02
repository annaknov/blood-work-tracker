# Blood Work Tracker

A self-contained HTML file for tracking lab results over time. No account required, no data ever leaves your device.

---

## How the tracker works

Download `blood_work_tracker.html` and open it in any modern browser (Chrome, Firefox, Safari, Edge). Your data is saved in your browser's local storage — it persists between sessions on the same machine and browser. Nothing is ever sent to any server.

The tracker covers CBC, Metabolic, Lipids, Hormones, Thyroid, and Vitamins & minerals panels. Once you have results, out-of-range values are flagged on the Overview tab based on the reference ranges from your most recent lab test.

---

## Option A — Let Claude populate the tracker directly (recommended)

The easiest way to get started. Upload the tracker file and your lab report into Claude and it will populate everything for you — no typing required.

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

Claude will read your results, match them to the correct markers, extract the reference ranges from your report, and return a populated version of the file. Download the file it returns and open it in your browser.

### Step 4 — Adding future results

Each time you get new labs, repeat the process — upload the current tracker file alongside your new results and ask Claude to add the new entry. Your history and trends will build up over time.

### Step 5 — Back up your data

Once results are in the tracker, click **Export JSON** under **+ Add → Export / import data** to save a backup. You can import this file to restore your data at any time.

---

## Option B — Ask Claude to generate a JSON file, then import it

If you prefer not to upload the tracker file each time, you can ask Claude to generate a JSON file from your lab results and import that directly into the tracker. This is useful if you have multiple reports to process at once, or if you want to keep the tracker file separate from your conversations with Claude.

### Step 1 — Share your lab results with Claude

Go to [claude.ai](https://claude.ai) and start a new conversation. Attach your lab report (screenshot, PDF, or copied text) and send a message like:

> "Please extract all values from this lab report and return them as a JSON file I can import into my blood work tracker. Use this format:
>
> ```json
> [
>   {
>     "date": "YYYY-MM-DD",
>     "lab": "Lab name",
>     "values": { "marker_key": numeric_value },
>     "ranges": { "marker_key": { "low": number, "high": number } }
>   }
> ]
> ```
>
> Use the marker keys from this list: wbc, rbc, hgb, hct, mcv, mch, mchc, rdw, plt, neut_abs, lymph_abs, mono_abs, eos_abs, baso_abs, neutrophils, lymphocytes, monocytes, eosinophils, basophils, glucose, bun, creatinine, egfr, anion_gap, sodium, potassium, chloride, co2, calcium, protein, albumin, globulin, ag_ratio, bilirubin, alp, ast, alt, hba1c, crp, total_chol, ldl, hdl, trig, non_hdl, vldl, tsh, free_t4, free_t3, total_t4, total_t3, t3_uptake, testosterone, free_test, shbg, dhea_s, estradiol, cortisol, lh, fsh, prolactin, vit_d, vit_b12, folate, ferritin, iron, tibc, iron_sat, magnesium, homocysteine, uric_acid, zinc"

Claude will return a `.json` file with your results formatted and ready to import.

### Step 2 — Import the JSON file into the tracker

Open `blood_work_tracker.html` in your browser. Go to **+ Add → Import JSON**, select the file Claude returned, and your results will be loaded into the tracker immediately.

### Adding multiple reports at once

You can share several lab reports in one conversation and ask Claude to combine them into a single JSON file with one entry per visit. This is the fastest way to populate historical data.

---

## Option C — Enter values manually

If you prefer to enter values yourself, the tracker has a built-in form for every panel.

### Step 1 — Open the tracker

Open `blood_work_tracker.html` in your browser.

### Step 2 — Go to the + Add tab

Select the **test date** and optionally the **lab name** (e.g. Quest, Labcorp). Then choose a **panel** from the dropdown — CBC, Metabolic, Lipids, etc.

Input fields will appear for every marker in that panel, with the reference range shown beneath each one. Enter the values from your lab report and click **Save entry**. Repeat for each panel you have results for.

You can also enter a **custom marker** not in the standard panels by selecting **Custom marker** from the panel dropdown. Enter the name, value, unit, and reference range.

### Step 3 — Edit values

You can edit any value at any time:
- **History tab** — click directly on any value in the table to edit it inline. Press Enter to save, Escape to cancel.
- **Overview / panel cards** — click the ✎ pencil icon on any card to edit the latest value for that marker.

### Step 4 — Update reference ranges (optional)

The tracker comes pre-loaded with reference ranges from the **NBME Laboratory Reference Values** for markers where a published range exists. These apply to adult males where sex-specific values are given.

If your lab report uses different ranges, update them in the **⚙ Ranges** tab: find the marker, edit the Low and High values, and click **Save changes**. The Source column tracks where each range came from. Use the **↺** button on any row to restore the NBME default.

---

## Exporting and backing up your data

Your data lives in your browser's local storage, which means:

- It is **browser-specific** — data in Chrome won't appear in Safari
- It is **device-specific** — data on your laptop won't appear on your phone
- It will be **lost** if you clear your browser's site data

Use **Export JSON** under **+ Add → Export / import data** after each session to save a backup. To restore on another device or browser, open the tracker and use **Import JSON**.

---

## Sharing with others

Share the original `blood_work_tracker.html` file as downloaded. Each person opens it in their own browser and starts with a blank tracker. Their data is completely separate and private to their own device.
