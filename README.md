# Year End Tool

A browser tool for a sole trader's year-end Use of Home, capital allowances (CA) and tax estimate. It follows the layout of the firm's working papers (the Expenses sheet's Use of Home section, the CA sheet and the Tax sheet) and brings forward what was claimed last year.

It is a single web page with no server, hosted free on **GitHub Pages**, like the Extraction Tool. It makes no AI calls and needs no API key. Files you drop in are read in your browser and never uploaded anywhere.

## What it does

- **Clients**: each client's workings for each tax year are saved separately in the browser. Pick a client from the list at the top, or open one from the **Clients** tab, which shows every client's progress (information requested and received, meeting, accounts sent, approved, return filed), next step, taxable profit and 31 January payment. Importing another client's files, or rolling a client forward a year, starts its own record rather than overwriting the one open. **Back up all clients** saves everything (with your rates, firm details and sign-off) to a file; **Restore from backup** brings it back or moves it to another browser.
- **Progress**: on the Import tab. Some dates fill themselves in: copying the information request, ticking off everything received on the Meeting tab, and copying the accounts email.
- **Import**: drop in any mix of the following.
  - **Last year's working papers** (.xlsx with Checklists, Expenses, Tax, CA and TB sheets). It brings forward:
    - the client name and period;
    - each Use of Home item, with last year's figure and its working (e.g. `200*12`);
    - the rooms split, hours a week, shared work space and last year's notes;
    - each car's TWDV c/fwd as this year's b/fwd, with its business use %;
    - the main pool balance;
    - last year's Tax sheet totals as comparatives, the student loan plan and Child Benefit status, and a regular Gift Aid amount;
    - last year's profit, Use of Home, CA and taxable profit from the TB.
  - **Last year's tax return** (the HMRC SA100 PDF with its supplementary pages, as a "Copy only" print). Gives last year's figures for self-employment (SA103S), employments (SA102), interest, dividends, pensions, other income (TR3), pension contributions and Gift Aid (TR4), student loan and Child Benefit (TR5), UK property (SA105), and the tax calculation (SA110), including the payments on account set for this year. The full self-employment pages (SA103F) aren't read yet.
  - **Last year's export from this tool**. Rolls everything forward a year, with c/fwd values becoming b/fwd. If it's the same tax year, it reopens the workings for editing.
  - **Extraction Tool Bank Statement or Bills CSV**. Lines coded to the Use of Home account are grouped into Rent, Council tax, Water, Gas and electricity and so on, and matched to last year's items. Dropping the same file in twice replaces its figures rather than doubling them.
  - **Xero Account Transactions export**. Reads the Use of Home account by name, and a "1 of 3 rooms" adjustment journal for the work space split.
  - **Extraction Tool backup** (.json). Finds this client's Use of Home account code.
- **Tax year**: set from the period end date. Importing last year's working papers sets this year's period to the twelve months after last year's, and rolling an export forward moves it on a year. Change the period end on the Client tab and the tax year follows.
- **Tax rates**: built in for 2024/25, 2025/26 and 2026/27 (England, Wales and Northern Ireland), so nothing needs entering. They can be viewed or changed under Tax rates at the bottom of the Export tab, which is also where a year that isn't built in yet can be added.
- **Client email**: two emails. The **information request** writes the year's information request from last year's workings. It names each household bill, vehicle, bank, investment, pension, property and charity, with last year's figures if you want them, and ends with a general question about other income and changes. Untick anything you don't need, edit the wording, then copy it or open it in your email app. **Accounts for approval** goes with the accounts PDF. It summarises turnover, expenses and net profit against last year, and the tax due with the January and July payments, then asks the client to sign the Client Approval page. Attach the PDF yourself (there's a download button beside it), as email links can't carry attachments.
- **Client emails**: on the Import tab, drop the client's emails (.eml or Outlook .msg) onto the import box, or paste an email's text. Each is saved with the client's workings (sender, date, subject and text) and goes into the audit file and the workbook's Audit trail sheet.
- **Extraction Tool**: the Import tab links to the Extraction Tool, opening it in a new tab on the same client (both tools are on the same site, so it uses the same Claude key, clients and coding rules). Read and code the year's documents there and click **Send to Year End Tool**: the lines appear on the Import tab straight away, and **Add to these workings** fills the Use of Home tab and the Accounts tab like a Bank CSV, with sales invoices as income. Each Extraction Tool job arrives as its own batch; sending the same job again replaces it, and any batch can be removed.
- **Accounts**: the client's Unaudited Financial Statements as a PDF, in the firm's layout: Cover, Directory, Client Approval, Accountants' and Bookkeepers' Report, and Profit and Loss.
  - This year's figures come from the Extraction Tool's Bank or Bills CSV, grouped by account code (for example 100 Revenue, 200 Direct Costs, 300 to the Use of Home tab, 980 left out), or from a Xero Profit and Loss export. Each Xero account is matched to a Profit and Loss line, and you can change any match. The tool's Use of Home and capital allowances are added unless the journals are already in Xero.
  - Last year's column comes from last year's accounts PDF, the working papers' Profit and Loss sheet, or last year's export.
  - Any line can be adjusted. The Tax tab's self-employment figures come from here (it can be switched to its own figures for clients without accounts in the tool).
  - The firm's details are saved in the browser.
- **Last year's meeting**: at the top of the Meeting tab, what came up last year: from last year's working papers, the notes in the PRE-MEETING NOTES and MEETING NOTES columns by section; from last year's export, the meeting notes, adjustments agreed, information still outstanding and checklist notes. **Add to this year's notes** turns it into a follow-up list.
- **Meeting**: the year end meeting's date, attendees and notes; the post-meeting checklist from the working papers with last year's answers; a tick list of the information received; and the adjustments agreed (costs paid personally, private use, income not banked, and HMRC mileage at 45p/25p). Adjustments flow into the Accounts tab and Tax tab, and become a "Meeting adjustments" Xero journal balanced to 990. The meeting date fills the Client Approval date.
- **Use of Home**: running costs, work space by rooms, time by hours a week (divided by the hours in a working day, 7.5 by default), business days a week or a %, and an optional partner's share. The HMRC flat rate is shown alongside, and you choose which method to claim. Amounts accept sums like `127.23*12`.
- **Capital allowances**: main pool (18%, AIA, small pools allowance), special rate pool (6%), and single-asset pools for vehicles and equipment with private use. A car can take 18%, 6% or the 100% first-year allowance; a van or equipment can take AIA. Disposals give balancing allowances or charges. Last year's calculation is shown underneath.
- **Tax**: laid out as the return asks for it. Self-employment (SA103), employments (SA102), interest and dividends by account, pensions, UK property (SA105), other income, pension contributions and Gift Aid by charity. Every section takes as many lines as needed, each with its own notes and last year's figure. The tab also covers student loan, the High Income Child Benefit Charge, Class 4 NI and payments on account.
- **Tax return**: the figures to enter, by page and box number.
- **Removed lines**: removing a line shows an Undo button, and recently removed lines can be restored from the list under each table.
- **Audit file**: on the Export tab, a readable PDF of everything about the client's year for the client file, opening with a meeting summary (notes, adjustments agreed, information outstanding, checklist points with notes), then progress dates, the files brought in and when, the meeting (notes, checklist, information received and adjustments agreed), the accounts line by line (imported, adjusted, Use of Home and capital allowances, meeting), the Use of Home, capital allowances and tax workings with their notes, the tax return figures, the Xero journals, and the emails. The Excel workbook also has Meeting, Journals and Audit trail sheets.
- **Export**: two downloads.
  - **Excel workbook** with Summary, Use of Home, CA, Tax and Tax return sheets. The Summary sheet has the profit, the other income and reliefs, the year's rates and the tax calculation as Excel formulas, so typing a different trading profit into it updates the tax. The full workings are kept in a hidden sheet, so next year you drop the file back in to roll forward.
  - **Xero manual journals CSV** with up to three journals, each balanced to 990 (clearing). **Use of Home** debits each cost item's business share to 300, to the penny, with the item's note from the Use of Home tab. **Capital allowances** debits each pool's allowance to 315, described as e.g. "Mercedes EQA: TWDV b/fwd £16,810 @ 18% WDA and 50% business use, TWDV c/fwd balance is £13,784.20". **Meeting adjustments** debits costs paid personally, credits private use (to 980) and unbanked income. Any journal can be left out, and the account codes, date and tax rate can be changed on the Export tab. Import it in Xero under Accounting → Manual journals → Import.

Work in progress is saved in the browser as you type, one record per client and tax year. Clearing the browser's data deletes it, so back up from the Clients tab now and then. The exported workbook is the copy to keep with the client's file.

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
| `docs/vendor/jspdf-2.5.1.umd.min.js` | A bundled copy of jsPDF, which writes the accounts PDF |
| `docs/vendor/pdfjs-3.11.174/` | A bundled copy of Mozilla's PDF.js, which reads last year's accounts PDF |
| `docs/firm-logo.js` | The firm's logo for the accounts PDF |
