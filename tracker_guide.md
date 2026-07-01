# Blood Work Tracker — How It Works

A complete guide to what the tracker does and how to use every part of it.

---

## How your data is stored

Everything is saved in your browser's **local storage** — no server, no account, no internet required. Data persists between sessions as long as you use the same browser on the same device. To move data to another device or browser, use **Export JSON** and **Import JSON** in the + Add tab.

---

## The tabs

### Overview
Your dashboard. Shows:
- **Summary bar** — total entries, markers tracked, total data points, and a count of ↑ High and ↓ Low values from your most recent test (highlighted red/orange when non-zero)
- **Out-of-range box** — if your latest results have any flags, they appear here grouped into High and Low sections, each showing the value and the reference limit it exceeded
- **Marker cards** — one card per marker you've ever entered, organized by panel. Each card shows the latest value, its status badge (Normal / ↑ High / ↓ Low / No ref range), the reference range used, a range bar, the change since your last test, and a trend chart if you have more than one data point
- **Edit tip** — a reminder that you can click the ✎ pencil on any card to edit the latest value inline, or go to History to edit any historical value

Out-of-range flags on the Overview are always based on the **reference ranges from your most recent lab test**.

### CBC / Metabolic / Lipids / Hormones / Thyroid / Vitamins & minerals
Same marker cards as the Overview, but filtered to just that panel. Useful when you want to focus on one area without scrolling through everything.

### History
A full table of every entry you've added, with one row per lab visit and one column per marker. Rows with any out-of-range value have a subtle red background and a ⚠ warning icon next to the date. Hovering a cell shows the reference range that applied to that specific result.

**Editing in History:**
- **Click any value cell** to edit it inline — type a new number, press Enter to save or Escape to cancel
- **Click a "—" cell** (where no value exists for that marker) to add one
- **✎ button** on the right of each row — opens the entry in the + Add form so you can edit the date, lab name, or enter values for a different panel
- **✕ button** — deletes the entire entry after confirmation

### + Add
Where you enter new results manually. Set the **test date** and **lab name**, pick a **panel** from the dropdown, and fill in the values. Each field shows the current reference range beneath it. Click **Save entry** when done. Repeat for each panel.

Also contains:
- **Let Claude fill it in** — instructions for uploading the tracker and your lab report to claude.ai and letting Claude populate it automatically
- **Export JSON** — saves all your data as a backup file
- **Import JSON** — restores data from a previously exported file

### ⚙ Ranges
View and edit the reference ranges used to flag values as high or low.

- The table shows every tracked marker with its current **Low** and **High** range, and a **Source** column indicating where the range came from
- **Source types:**
  - *NBME default* — from the NBME Laboratory Reference Values (adult male), used when no other range is available
  - *From lab result* — automatically adopted from your most recent uploaded result
  - *Manually entered* — you typed it in and saved it
- **Editing** — change the Low or High value for any marker directly in the table. The Source column updates to "Manually entered" as soon as you type. Click **Save changes** to persist
- **↺ button** — resets that marker back to its NBME default
- Markers not covered by the NBME document show blank inputs and "No default — set from lab result" as the source. They won't flag as high or low until a range is set from a lab result or manually

---

## Reference ranges — how they work

Each data point stores the reference range that applied **at the time it was entered**. This means:
- If you switch labs (e.g. Quest to Labcorp), each entry is evaluated against its own lab's ranges, not a global setting
- The Overview always flags based on the **most recent entry's ranges**
- The History table colors each cell using that specific entry's stored range — so an old Quest result is never judged by Labcorp's numbers
- Trend charts show the reference lines as dashed red lines. If ranges changed between labs, the lines will visually step between them

---

## Marker cards — what each element means

| Element | What it shows |
|---|---|
| **Name + unit** | Marker name and unit of measurement |
| **Collected date · lab** | When and where the latest result was drawn |
| **Ref: X – Y** | The reference range for the latest result |
| **Large number** | The latest value (red = high, orange = low, black = normal) |
| **Badge** | Normal / ↑ High / ↓ Low / No ref range |
| **Range bar** | Visual position of the value within the reference range |
| **● Out of range in N prior results** | Appears when the latest is normal but earlier results were flagged |
| **↑/↓ X vs [date]** | Change from the previous result |
| **Trend chart** | All historical values with red dashed reference lines |
| **Description** | Clinical context explaining what the marker means |
| **✎ pencil** | Click to edit the latest value inline |

---

## Editing values

| Where | What you can edit |
|---|---|
| **Overview / panel cards** | Latest value for that marker (click ✎) |
| **History — any cell** | Any value from any entry (click the cell) |
| **History — ✎ row button** | Date, lab name, and values for a specific panel |
| **⚙ Ranges tab** | Low and High reference range for any marker |

---

## Backing up and moving data

- **Export JSON** — saves all entries as a `.json` file. Do this after each session if you want a backup
- **Import JSON** — restores from an exported file. Imports entries not already present (matched by date)
- Data is **browser and device specific** — Chrome on your laptop won't see Safari data, and your phone won't see your laptop's data unless you export and import
- Clearing browser site data or private/incognito mode will erase local storage

---

