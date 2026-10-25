# Year End Tool

A browser tool for a sole trader's year-end Use of Home, capital allowances (CA) and tax estimate. It follows the layout of the firm's working papers (the Expenses sheet's Use of Home section, the CA sheet and the Tax sheet) and brings forward what was claimed last year.

It is a single web page with no server, hosted free on **GitHub Pages**, like the Extraction Tool. It makes no AI calls and needs no API key. Files you drop in are read in your browser and never uploaded anywhere.

## What it does

- **Client & import**: drop in any mix of the following.
  - **Last year's working papers** (.xlsx with Checklists, Expenses, Tax, CA and TB sheets). It brings forward:
    - the client name and period;
    - each Use of Home item, with last year's figure and its working (e.g. `200*12`);
    - the rooms split, hours a week, shared work space and last year's notes;
    - each car's TWDV c/fwd as this year's b/fwd, with its business use %;
    - the main pool balance;
    - last year's Tax sheet totals as comparatives, the student loan plan and Child Benefit status, and a regular Gift Aid amount;
    - last year's profit, Use of Home, CA and taxable profit from the TB.
  - **Last year's export from this tool**. Rolls everything forward a year, with c/fwd values becoming b/fwd. If it's the same tax year, it reopens the workings for editing.
  - **Extraction Tool Bank Statement or Bills CSV**. Lines coded to the Use of Home account are grouped into Rent, Council tax, Water, Gas and electricity and so on, and matched to last year's items. Dropping the same file in twice replaces its figures rather than doubling them.
  - **Xero Account Transactions export**. Reads the Use of Home account by name, and a "1 of 3 rooms" adjustment journal for the work space split.
  - **Extraction Tool backup** (.json). Finds this client's Use of Home account code.
- **Use of Home**: running costs, work space by rooms, time by hours a week (days of 10 hours out of 7) or a %, and an optional partner's share. The HMRC flat rate (£10/£18/£26 a month) is shown alongside, and you choose which method to claim. Amounts accept sums like `127.23*12`.
- **Capital allowances**: main pool (18%, AIA, small pools allowance), special rate pool (6%), and single-asset pools for cars with private use (18% or 6%, 100% FYA for new zero-emission cars, disposals with balancing allowances or charges).
- **Tax**: taxable trading profit, other income, pension and Gift Aid relief, student loan, the High Income Child Benefit Charge, Class 4 NI, payments on account and the 31 January payment. Uses 2025/26 and 2024/25 rates for England, Wales and Northern Ireland.
- **Export**: one Excel workbook with Summary, Use of Home, CA and Tax sheets. The full workings are kept in a hidden sheet, so next year you drop the file back in to roll forward.

Work in progress is saved in the browser as you type. The exported workbook is the copy to keep with the client's file.

## One-time setup

1. In this repo on GitHub, go to **Settings → Pages**.
2. Under **Build and deployment**, set Source to **Deploy from a branch**, Branch to **`main`**, and Folder to **`/docs`**. Click **Save**.
3. After a minute or two the page shows the address, e.g. `https://rcsqueah.github.io/YearEndTool/`.

## Adding a new tax year's rates

Rates live in the `RATES` table near the top of the script in `docs/index.html`. Copy the latest year, change the figures that changed (e.g. Child Benefit, student loan thresholds), and the new year appears in the Tax year list.

| File | What it does |
|---|---|
| `docs/index.html` | The tool itself |
| `docs/vendor/xlsx-0.18.5.full.min.js` | A bundled copy of SheetJS for reading and writing Excel files |
