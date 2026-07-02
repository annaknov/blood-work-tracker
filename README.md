# 🩺 Blood Work Tracker

**A self-contained HTML file for tracking lab results over time.**  
No account required. No server. No data ever leaves your device.

![HTML](https://img.shields.io/badge/HTML-single%20file-orange?style=flat-square)
![Storage](https://img.shields.io/badge/storage-local%20only-green?style=flat-square)
![Dependencies](https://img.shields.io/badge/dependencies-none-blue?style=flat-square)

---

## What it does

- 📊 **Tracks results over time** across CBC, Metabolic, Lipids, Hormones, Thyroid, and Vitamins & minerals panels
- 🚨 **Flags out-of-range values** based on reference ranges from your most recent lab test
- 📈 **Shows trends** with a chart for every marker across visits
- 🏥 **Supports multiple labs** — Quest, Labcorp, or any other source, each with their own reference ranges stored per entry
- ✏️ **Inline editing** — click any value in the History tab to edit it directly
- 📋 **Reference ranges** pre-loaded from the NBME Laboratory Reference Values, automatically updated from your lab reports

---

## Getting started

**Download [`blood_work_tracker.html`](./blood_work_tracker.html) and open it in any modern browser.**

Your data is saved in your browser's local storage and persists between sessions. Nothing is sent to any server.

---

## Three ways to add your results

### Option A — Let Claude populate the tracker *(recommended)*

Upload the tracker file and your lab report to Claude and it fills everything in for you.

1. Go to **[claude.ai](https://claude.ai)** and start a new conversation
2. Attach `blood_work_tracker.html` + your lab report (screenshot, PDF, or copied text)
3. Send this message:

   > *"Please fill in this blood work tracker with the values from my lab report and return the updated file."*

4. Download the file Claude returns and open it in your browser

Claude extracts values and reference ranges automatically. For future visits, repeat with the updated file to build up your history.

---

### Option B — Ask Claude to generate a JSON file, then import it

Useful if you have multiple reports to process at once, or prefer not to upload the tracker file each time.

1. Go to **[claude.ai](https://claude.ai)** and attach your lab report(s)
2. Send this message:

   > *"Please extract all values from this lab report and return them as a JSON file I can import into my blood work tracker. Use this format:*
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
   > *Use these marker keys:*  
   > `wbc, rbc, hgb, hct, mcv, mch, mchc, rdw, plt, neut_abs, lymph_abs, mono_abs, eos_abs, baso_abs, neutrophils, lymphocytes, monocytes, eosinophils, basophils, glucose, bun, creatinine, egfr, anion_gap, sodium, potassium, chloride, co2, calcium, protein, albumin, globulin, ag_ratio, bilirubin, alp, ast, alt, hba1c, crp, total_chol, ldl, hdl, trig, non_hdl, vldl, tsh, free_t4, free_t3, total_t4, total_t3, t3_uptake, testosterone, free_test, shbg, dhea_s, estradiol, cortisol, lh, fsh, prolactin, vit_d, vit_b12, folate, ferritin, iron, tibc, iron_sat, magnesium, homocysteine, uric_acid, zinc`"

3. In the tracker, go to **+ Add → Import JSON** and select the file Claude returned

You can share multiple reports in one conversation and ask Claude to combine them into a single JSON file — one entry per visit.

---

### Option C — Enter values manually

1. Open the tracker and go to the **+ Add** tab
2. Set the test date, lab name, and choose a panel (CBC, Metabolic, Lipids, etc.)
3. Fill in the values and click **Save entry** — repeat for each panel
4. To enter a marker not in the standard panels, choose **Custom marker** from the dropdown

---

## Editing your data

| Where | What you can do |
|---|---|
| **History tab** | Click any cell to edit that value inline — Enter to save, Escape to cancel |
| **Overview / panel cards** | Click the ✎ pencil on any card to edit the latest value |
| **History ✎ button** | Edit the date, lab name, or re-enter values for a panel |
| **⚙ Ranges tab** | Edit the Low / High reference range for any marker |

---

## Reference ranges

Default ranges come from the **[NBME Laboratory Reference Values](https://www.nbme.org/)** — the standard reference table used in US medical licensing exams. Adult male values are used where sex-specific ranges are given.

The tracker automatically adopts ranges from your most recent uploaded result. The **⚙ Ranges** tab shows the source for every marker:

| Source | Meaning |
|---|---|
| *NBME default* | From the NBME published reference table |
| *From lab result* | Automatically set from your most recent result |
| *Manually entered* | You typed it in and saved it |

Use ↺ on any row to restore the NBME default for that marker.

---

## Backing up your data

> ⚠️ Browser local storage is browser- and device-specific. Data in Chrome won't appear in Safari, and your laptop won't sync with your phone.

After each session, use **Export JSON** under **+ Add → Export / import data** to save a backup file. Use **Import JSON** to restore it on any device or browser.

---

## Sharing with others

Share the original `blood_work_tracker.html` file. Each person opens it in their own browser and starts with a blank tracker — their data is completely private to their own device.
