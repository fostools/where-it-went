# Where It Went

See where your money went. Drop in a folder of bank and credit card statements and get a spending dashboard: monthly trends, categories, recurring charges, fees and things worth a second look.

Everything runs in your browser. Your statements are never uploaded anywhere.

## Use it

Open `index.html` (or the GitHub Pages site for this repo), then click **Choose folder**, **Choose files**, or drag files onto the page. The page opens with made-up sample data until you add your own.

Supported files:

- **CSV** exports from banks, cards and apps like Monarch, Mint or Copilot
- **Excel** (`.xlsx`, `.xls`) activity downloads, such as Amex
- **PDF** statements with real text (Chase and similar layouts). Scanned, image-only PDFs can't be read; export a CSV instead.
- **Zip** archives of any of the above

Overlapping or repeated statements are detected, so the same transaction is never counted twice.

## What it shows

One **Period** filter (last 3/6/10/12 months, year to date, any single year or month, or custom dates) and one **Account** filter apply to every section of the page.

- **Overview**: total and monthly spending, income, interest and fees, recurring cost, a monthly chart stacked by category, spending by category, top merchants. Click a month bar, one colored segment of a bar, a legend entry, a category, a merchant, or "View transactions" on any finding to see the transactions behind it.
- **Money flow**: a Sankey chart from account to category to biggest merchants. Click any band or node to see its transactions.
- **Things to look at**:
  - interest and fees by account
  - cash-advance charges (for example, Venmo paid with a credit card)
  - possible duplicate charges
  - overlapping services (news, AI assistants, live TV, music, credit monitoring)
  - one merchant billing you more than once a month
  - price increases
  - spike months
  - large one-time charges
- **Transactions**: search, filter, sort, and recategorize. Changing a category applies to every charge from that merchant and is remembered in your browser.
- **Recurring**: charges on a steady schedule, with cadence, yearly cost and whether they're still active
- **Ask** (only when the page is opened inside Claude): chat with Claude about your transactions. Claude answers by running lookups on the loaded data (totals by merchant, category, month or account; matching rows; recurring charges; findings), and each answer links to the transactions it used. On GitHub Pages or a plain browser this tab stays hidden.
- **Files**: what was read from each file, the account and period it covers, and anything skipped

## How it works

A single HTML file, with no build step and no server. It uses these libraries, loaded from cdnjs:

- [PapaParse](https://www.papaparse.com/) for CSV
- [SheetJS](https://sheetjs.com/) for Excel
- [pdf.js](https://mozilla.github.io/pdf.js/) for PDF text
- [JSZip](https://stuk.github.io/jszip/) for zip archives

Transactions are normalized so that money out is positive. Card payments, transfers and income are kept out of spending. Each transaction is categorized from the statement's own category when it has one, otherwise from merchant keyword rules.

## Limits

- Data isn't saved between visits; reload and add the files again. Only your category changes are kept.
- PDF layouts vary by bank. If a PDF isn't read, use the bank's CSV export.
- Merchant names come from statement text and can be messy (some exports run the merchant and city together).

## License

MIT. See [LICENSE](LICENSE).
