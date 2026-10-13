# Kareth Store Manager PWA

A mobile-friendly, offline-first web app for a small hardware and convenience store.

## Features
- Product records: name, category, SKU, barcode, cost, stock, reorder level, supplier
- Selling price suggestions using either markup-on-cost or target-margin calculations
- Manual product lookup and barcode input; optional camera scanning where `BarcodeDetector` is supported
- Sales recording, automatic stock deduction, sales history, estimated gross profit
- Dashboard, low-stock alerts, inventory valuation, date-filtered reports, CSV sales export
- JSON backup and restore
- Local-only storage on one browser/device

## Important data and security notes
- Records are stored in the browser's localStorage on this device. They are not synchronized to another phone.
- Export a JSON backup frequently. Browser data clearing or uninstalling can erase records.
- Restore replaces current records, so export a backup first.
- Gross profit is revenue minus the recorded product cost; it excludes tax, overhead, discounts not recorded correctly, and other expenses beyond the sale discount.
- This is a starter app, not a tax-compliant POS or accounting system. Test with sample data before using it for real transactions.
- Barcode camera scanning varies by browser/device. A Bluetooth barcode scanner that types into the field is a practical alternative.

## Installation on Android
A PWA service worker requires a secure origin (HTTPS) or `localhost`. Opening the HTML file directly may allow basic use but will not enable reliable installation/offline caching.

1. Extract this ZIP on a computer.
2. Host the folder on an HTTPS static host you control, or run a local development server for testing.
3. Open `index.html` through that HTTPS address in Chrome on Android while online.
4. Use Chrome menu (⋮) → **Install app** or **Add to Home screen**.
5. Open the app once while online so its shell can be cached.
6. Add a test product and sale, export a JSON backup, and test restore before entering real inventory.

## Test locally on a computer
If Python 3 is installed, open a terminal in the extracted folder and run:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in your browser. This is suitable for testing on the same computer, not for directly installing to a phone. For phone installation, use HTTPS.

## Pricing examples
- Cost ₱80 with 25% markup: ₱80 × 1.25 = ₱100.
- Cost ₱80 with 25% target margin: ₱80 ÷ (1 − 0.25) = ₱106.67.

## File structure
- `index.html` — complete application
- `manifest.webmanifest` — PWA metadata
- `sw.js` — offline app-shell cache
