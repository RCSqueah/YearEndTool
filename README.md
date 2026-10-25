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
- **Tax year**: set from the period end date. Importing last year's working papers sets this year's period to the twelve months after last year's, and rolling an export forward moves it on a year. Change the period end on the Client tab and the tax year follows.
- **Tax rates**: built in for 2024/25, 2025/26 and 2026/27 (England, Wales and Northern Ireland), so nothing needs entering. They can be viewed or changed under Tax rates at the bottom of the Export tab, which is also where a year that isn't built in yet can be added.
- **Client email**: writes the year's information request from last year's workings. It names each household bill, vehicle, bank, investment, pension, property and charity, with last year's figures if you want them, and ends with a general question about other income and changes. Untick anything you don't need, edit the wording, then copy it or open it in your email app.
- **Use of Home**: running costs, work space by rooms, time by hours a week (divided by the hours in a working day, 7.5 by default), business days a week or a %, and an optional partner's share. The HMRC flat rate is shown alongside, and you choose which method to claim. Amounts accept sums like `127.23*12`.
- **Capital allowances**: main pool (18%, AIA, small pools allowance), special rate pool (6%), and single-asset pools for vehicles and equipment with private use. A car can take 18%, 6% or the 100% first-year allowance; a van or equipment can take AIA. Disposals give balancing allowances or charges. Last year's calculation is shown underneath.
- **Tax**: laid out as the return asks for it. Self-employment (SA103), employments (SA102), interest and dividends by account, pensions, UK property (SA105), other income, pension contributions and Gift Aid by charity. Every section takes as many lines as needed, each with its own notes and last year's figure. The tab also covers student loan, the High Income Child Benefit Charge, Class 4 NI and payments on account.
- **Tax return**: the figures to enter, by page and box number.
- **Removed lines**: removing a line shows an Undo button, and recently removed lines can be restored from the list under each table.
- **Export**: two downloads.
  - **Excel workbook** with Summary, Use of Home, CA, Tax and Tax return sheets. The Summary sheet has the profit, the other income and reliefs, the year's rates and the tax calculation as Excel formulas, so typing a different trading profit into it updates the tax. The full workings are kept in a hidden sheet, so next year you drop the file back in to roll forward.
  - **Xero manual journal CSV** for the Use of Home. Each cost item's business share is debited to account 300 to the penny, and the balancing credit goes to 990 (clearing). Both codes, the date and the tax rate can be changed on the Export tab. Import it in Xero under Accounting → Manual journals → Import.

Work in progress is saved in the browser as you type. The exported workbook is the copy to keep with the client's file.

## One-time setup

1. In this repo on GitHub, go to **Settings → Pages**.
2. Under **Build and deployment**, set Source to **Deploy from a branch**, Branch to **`main`**, and Folder to **`/docs`**. Click **Save**.
3. After a minute or two the page shows the address, e.g. `https://rcsqueah.github.io/YearEndTool/`.

## A new tax year

Open **Export → Tax rates** and click **Add next year's rates**. Change the figures HMRC has changed (e.g. Child Benefit, student loan thresholds) and they're saved in the browser. To build a year into the tool for everyone, add it to `BUILTIN_RATES` in `docs/index.html`.

| File | What it does |
|---|---|
| `docs/index.html` | The tool itself |
| `docs/vendor/xlsx-0.18.5.full.min.js` | A bundled copy of SheetJS for reading and writing Excel files |
