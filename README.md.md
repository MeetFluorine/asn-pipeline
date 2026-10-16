# ASN Pendency – Auto Dashboard

A single-file HTML tool that turns the **MultiUOMSerialReport** download into the ASN pendency list.

Everything runs in your browser. The file is never uploaded anywhere, and the Excel library is built into the page, so it works without internet.

## How to use

1. Open `ASN_Pendency_Dashboard.html` in Chrome or Edge.
2. Drop `MultiUOMSerialReport.xlsx` (a `.zip` containing it also works) into the box. A progress bar shows the stages.
3. Check the counts and the tabs.
4. Click **Download Excel**. The file is saved as `<file name>_ASN_Pendency.xlsx`.

## What it does

| Step | Rule |
|---|---|
| 1. Pending rows | Keeps rows where `GRNNo` (column Q) is blank |
| 2. Current date | Removes rows whose `CreatedOn` (column O) is today's date, since an ASN uploaded today is not pending yet. Untick **Remove rows created today** to keep them |
| 3. Date format | `CreatedOn` is shown as `dd-mm-yyyy h:mm`, for example `22-05-2026 16:54`. In Excel it is a real date with that format |

The result keeps all 17 columns of the original report, in the original order.

## Tabs

- **ASN pendency:** the filtered rows. This is the answer.
- **By ASN:** ASNNo, Client, oldest CreatedOn, number of serial rows and age in days.
- **By Client:** Client, ASNs pending, serial rows, oldest CreatedOn and age in days.

The counts above the tabs show rows scanned, blank GRNNo, created today (removed), ASN pendency rows, ASNs pending and clients. A check line confirms that the pendency rows plus the removed rows equal the blank GRNNo rows. Age in days is today's date minus the oldest CreatedOn date.

## Excel download

| Sheet | Contents |
|---|---|
| ASN Pendency | The filtered rows, with filter dropdowns on the header row |
| By ASN, By Client | Optional. Tick **Add “By ASN” and “By Client” sheets** before downloading |

## Troubleshooting

| Problem | Fix |
|---|---|
| "Could not read the file" | Use the original download, not a re-saved copy |
| "No sheet with a GRNNo column was found" | The report must have a `GRNNo` header in its first row |
| Fewer rows than expected | The check line shows how many were removed as created today. Untick the option to keep them |
| Nothing happens after dropping the file | Reload with Ctrl+F5 and drop the file again |

## Files

- `ASN_Pendency_Dashboard.html`: the tool (one file, no install).
- `README_ASN_Pendency.md`: this guide.
