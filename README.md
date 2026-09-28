# SampleReady — functional V1 web-app prototype

A responsive, interactive web app based on the 13-screen `SampleReady.V1.pdf` Figma export. It is an **independent PM portfolio prototype**, not an official metabolomics lab portal or a validated scientific/shipping protocol.

## Features

- Seven-stage submission wizard: project, samples, containers, labels, controls, packaging, review.
- Editable experiment groups and replicates; live digital-record preview.
- Import an existing `.xlsx` metabolomics sample submission workbook (detects the `Metabolomics Sample Name` header in the DATA SHEET, including the uploaded template's row 2).
- Preserve imported full sample names, sample group, replicate, sample number, and tube label where available.
- Generate short rack-style tube IDs (`A1`, `A2`, etc.); edit IDs and detect duplicate, missing, or over-20-character IDs.
- Add and edit physical control tubes, and verify packaging requirements.
- Export a standalone Excel/CSV manifest. If you import a compatible workbook, export adds the mapping to its existing DATA SHEET and adds a `SampleReady Manifest` sheet; the original workbook's other sheets are retained on a best-effort basis.
- Print a tube-ID mapping guide. Automatically save form state in browser local storage.
- Responsive styling modeled after the PDF: navy/teal, light neutral background, stepper, cards, sample tube and rack diagrams.

## Run locally

1. Install [Node.js](https://nodejs.org/) 20+.
2. In this folder, run `npm install`.
3. Run `npm run dev` and open the local URL displayed in the terminal.
4. Run `npm run build` to verify the production build.

## Publish with GitHub Pages

1. Create a new GitHub repository, e.g. `sampleready`, and upload/push the **contents** of this folder (including `.github/workflows/deploy.yml`).
2. Push to the `main` branch.
3. Open the repository's **Settings → Pages → Build and deployment**, and select **GitHub Actions** as the source.
4. Under **Actions**, wait for `Deploy SampleReady to GitHub Pages` to finish. GitHub displays the published URL in the Pages settings or deployment result.

The Vite base is `./`, so this works under a GitHub Pages project subpath.

## Privacy and scientific limitations

- **Do not upload real unpublished research metadata to a public/shared computer.** Imports and local storage are processed client-side; the app has no server or laboratory database integration.
- This is a concept demo, not an approved shipping protocol. Tube compatibility, maximum fill, lyophilization caps, controls, dry-ice handling, and temperature requirements must be confirmed by the receiving lab.
- Completing the checklist **does not submit or register samples**. The approval checkbox records only the user's statement that approval occurred externally.
- Import/export targets the common DATA SHEET headers. Complex spreadsheet macros, formulas, formatting, validation, and external links may not survive round-tripping. Keep the original workbook as a backup and validate exports before real use.
- This app does not transmit user data to a backend. Google Fonts are fetched from Google's font CDN; you can remove the `@import` in `src/style.css` for an entirely self-contained font stack.

## Suggested next steps

Validate the short-ID mapping and rack assumptions with both researchers and receiving lab staff. Test the spreadsheet importer with multiple real *anonymized* form variants before treating it as a production feature.
