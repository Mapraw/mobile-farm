# CA Week 21–30 Y69 — Farm Dashboard (Vercel-ready, public, no login)

Static single-page dashboard for your girlfriend's farm data.
Anyone with the link can view + download Excel. No privacy / no login, as requested.

## What's inside

| File | Purpose |
|---|---|
| `index.html` | The whole website (Thai UI, Chart.js graphs, SheetJS upload/download) |
| `data.json` | Snapshot of Test › Sheet2 (6 farms, extracted 2026-09-10) |
| `refresh_sheet2.py` | Re-fills `test.xlsx › Sheet2` from the source workbook (Excel-side Refresh) |
| `vercel.json` | Optional static config |

## Deploy to Vercel (2 minutes)

Option A — drag & drop:
1. Go to https://vercel.com/new
2. Drag the `dashboard/` folder in → Deploy → share the link.

Option B — CLI:
```bash
cd dashboard
npx vercel --prod
```

No build step, no environment variables, free static hosting.

## Refresh flow (after she updates the source workbook)

Web (recommended):
1. Open the site → **🔄 Refresh Data** → select the updated
   `บันทึกการเลี้ยง CA week21-30 Y69 Try_1.xlsx`
2. Charts + table update instantly (parsed in the browser, same cells as Sheet2 row 2;
   `B8-1` = B8 date minus 1 day).
3. **⬇️ Download Excel** → gets `Test-Sheet2.xlsx` in Test › Sheet2 format.

Excel (keeps test.xlsx itself fresh):
```bash
python dashboard/refresh_sheet2.py
```
Each source sheet → one row in `test.xlsx › Sheet2`, same mapping as the yellow highlights.

## Note

- Source sheet `นพมาศH1 3-69` has farm name `นพมาศ1` in cell B3 (kept as-is from source).
- `นน.เฉลี่ยจับ` and `นน จับ (Kg)` both map to cell D61 (same value) — also as in her Sheet2 mapping.
- Only the first farm sheet (`ผล 3-69`) is fully filled (catch age/weight H60–H61);
  other sheets update automatically on Refresh once she fills them in.
"# mobile-farm" 
