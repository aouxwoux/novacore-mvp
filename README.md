# NOVACORE — Freight intelligence

A GitHub Pages-ready, interactive MVP for verifying packed-parcel shipping data, calculating expected courier charges, reconciling invoices, and preparing evidence-backed disputes.

## Run

No build, package installation, API keys, or server backend required. Serve this folder with any static server, or open `index.html`. All asset paths are relative, including under a GitHub Pages repository path.

## Publish on GitHub Pages

Push these files to the `main` branch. In repository **Settings → Pages**, select **GitHub Actions** as the source. The included workflow publishes the site on each push. The resulting address is `https://<username>.github.io/<repository>/`.

## Judge demo: 3 minutes

1. Open **Judge walkthrough**. Explain the problem: courier adjustments need to be checked against sealed-parcel measurements.
2. Open **Capture a parcel**. The default 0.6 kg, 30 × 20 × 15 cm parcel has 1.8 kg volumetric weight, rounds to 2 kg billable weight, and costs ₹120 under the illustrative contract. Save its measurement.
3. Inspect **NV-1001**. Expected ₹120; invoiced ₹160 at 3 kg. The ₹40 difference is a candidate overcharge. Download its evidence packet. Photos can be attached; seed records intentionally do not invent photographic evidence.
4. Open **Reconciliation → Run demo invoice → Match invoice**. Three previously uninvoiced AWBs are matched; one new exception is found. Importing the same invoice again preserves existing records.
5. Open **Packaging lab**. The smaller 25 × 18 × 10 cm box rounds to 1 kg. ₹40 less freight minus ₹5 extra packaging = ₹35 estimated net savings per shipment.
6. Return to **Overview**. Explain why open overcharges and confirmed credits are tracked separately. Simulated claim outcomes can be recorded in the dispute detail.

## What works

- Live contract-based volumetric, chargeable, and rounded billable weight calculations.
- Versioned dispatch-time contract snapshots, retained when rate rules change.
- SKU/profile mismatch and billing-boundary validation with a measurement hold and physical re-check.
- Parcel capture and browser-local photo attachments.
- Invoice CSV matching by AWB, duplicate detection, and unmatched-row reporting.
- Claim state recording with a positive credit amount, reference, and verification acknowledgment required for confirmed recovery.
- Self-contained HTML evidence packet with calculation, invoice detail, and embedded photos; open it and print to PDF.
- CSV ledger export, packaging comparison, search, filters, mobile layout, and demo reset.

## Demo boundaries

Seeded shipments, rate rules, invoices, and credits are illustrative. The single demo rate card represents one national surface-service zone; real carrier contracts require destination/service rules, taxes, and applicable surcharges. No fixed percentage saving is promised.

Data and compressed photo evidence are stored only in this browser's local storage. This is not shared cloud storage, authentication, or a production audit log. If browser storage fills, changes remain in memory and a warning is shown. Export records before clearing storage. No courier claim is transmitted, no digital scale is connected, and claim outcomes are not independently verified. Packaging estimates exclude changes to damage and return costs.

For the first real pilot: connect one packing station, use contracted rate cards, secure shared evidence storage, reconcile one billing cycle, confirm credits from courier statements, and measure labor time plus damage/return rates.

## Architecture

`index.html`, `styles.css`, `app.js`, and `engine.js`: dependency-free static application. Google Fonts is an optional visual enhancement; system fonts provide a fallback. No remote customer data or analytics services are used. `.github/workflows/pages.yml` deploys the static folder.
