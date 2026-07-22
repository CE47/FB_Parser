# FB Leads CSV Cleaner

A simple, browser-based tool for cleaning and deduplicating Facebook Lead Ads CSV exports. No server required — runs entirely in your browser.

**Live App:** https://ce47.github.io/FB_Parser/

## Features

- **Drag & drop** multiple CSV files at once (no file limit)
- **Auto-detects encoding** — handles UTF-16 LE/BE (Facebook's default export format) and UTF-8
- **Tab-separated and comma-separated** formats supported
- **Smart column detection** — recognizes different Facebook Lead Ads export formats:
  - Separate `first name` / `last name` columns
  - Combined `full_name` column (auto-splits into first/last)
  - Malformed headers where Facebook embeds the first record's data as column names
- **Phone number cleaning** — strips `p:` prefix, `+` signs, and non-numeric characters, leaving only digits
- **Deduplication** — removes duplicate contacts based on first name + last name (case-insensitive)
- **Merges data** — if a duplicate has missing email/phone, fills it in from other occurrences
- **One-click CSV export** — downloads a clean file with columns: First Name, Last Name, Email, Phone

## Usage

1. Open `index.html` in any modern browser (or visit the GitHub Pages link)
2. Drag and drop your Facebook Lead Ads CSV export files onto the drop zone
3. Review the parsed contacts in the table
4. Click **Download CSV** to export the deduplicated contacts

## Supported CSV Formats

The tool handles the three known Facebook Lead Ads export variants:

| Format | Example Headers (after `platform`) |
|--------|-----------------------------------|
| Full name | `email`, `full_name`, `phone`, `inbox_url` |
| Split name | `first name`, `last name`, `email`, `phone`, `inbox_url` |
| Malformed header | Data values appear as headers (e.g., `john@email.com`, `09171234567`, `John Doe`) |

## Technical Notes

- Zero dependencies — pure HTML, CSS, and vanilla JavaScript
- All processing happens client-side; no data is sent to any server
- Works offline once the page is loaded
- Compatible with all modern browsers (Chrome, Firefox, Safari, Edge)
