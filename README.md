# Approval Flow

Offline, single-file web app for multi-stage approval workflows. Route a request through a chain of approvers, record a decision and notes at each stage, send notification emails, and export everything to Excel.

It is one self-contained `Approval_Flow.html` file — no dependencies, no build step, no server, no CDN. Open it in a browser and it works.

## What it does

- **Multi-stage routing** — a request moves through approver stages one at a time. A routing-slip track shows where it is (done / current / waiting).
- **Approval notes** — at each decision the approver can add notes (reason, conditions, references). Notes are saved to the stage, shown in the history, carried into the next notification email, and included in exports.
- **Email notifications** — at every transition the app prepares the message: new request → first approver, each approval → next approver, final approve/reject → back to the requester. Each opens in your default mail app (`mailto:`) or copies to the clipboard. Nothing is sent automatically.
- **Reusable routes** — save approval chains once and pick them when raising a request.
- **Excel export** — download a single request (sheets: Request, Route, History) or a full report across all requests (sheets: Requests, Stages, History). Real `.xlsx` files generated in the browser; numbers export as numbers so you can sort and total in Excel.
- **Audit history** — every request keeps a timestamped log of who did what.

## Run it

Open `Approval_Flow.html` in any modern browser (Chrome, Edge, Firefox). That's it.

To host a shareable link, enable **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / root) and open:

```
https://<your-username>.github.io/<repo-name>/Approval_Flow.html
```

## Data and privacy

- All data is stored locally in the browser's `localStorage`. It stays on that machine/browser and is never uploaded.
- The app makes no network calls — no external scripts, fonts, CDNs, or telemetry. It runs fully offline.
- Email is handled through your own mail client via `mailto:`; the app does not transmit anything itself.

Because data is per-browser, requests created on one machine won't appear on another. Use the Excel export to share or archive.

## Tech

Plain HTML, CSS, and vanilla JavaScript in a single file. The `.xlsx` writer (ZIP + worksheet XML) is built in, so no spreadsheet library is required.

## Notes

- Anyone with the file can record any stage's decision — it's built as a single-operator / coordinator console. If you need each approver restricted to their own stage, that requires an identity/auth layer.
- Tested in current Chromium and Firefox browsers.

## License

See [LICENSE](LICENSE).
