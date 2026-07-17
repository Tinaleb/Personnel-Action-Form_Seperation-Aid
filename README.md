# PAF Generator

Fills the SCIS Personnel Action Form (5000 Series) for employee separations — single or in bulk — entirely in the browser. No data is sent anywhere; the blank form is embedded in the page and PDFs are generated on the device.

## Use it

Open `index.html` (or the GitHub Pages URL once published).

**Single separation:** fill the four required fields — name, site, what happened, last date worked — and tap **Download this PAF**. Everything else auto-fills from the separation code and can be overridden.

**Bulk, same reason:** in the *Bulk entry* section, pick the code and shared last date worked once, then paste the employee list — one per line. Just names is enough; add a site, rate, or date after the name to override defaults (comma, tab, or dash separated — pasting straight from Excel works). Tap **Add all to batch**, then **Download all**.

**Mixed reasons:** use the single form and **Add to batch** per person, then **Download all**.

Files download as `PAF_Lastname_Firstname_YYYY-MM-DD.pdf`. Signature lines are left blank for signing after download. "Requested by" and department number are remembered on the device.

## Publish on GitHub Pages

1. Create a new repository (e.g. `paf-generator`)
2. Upload `index.html` and this `README.md` to the repository root
3. Repository **Settings → Pages → Source**: select branch `main`, folder `/ (root)`, and save
4. The app will be live at `https://<username>.github.io/paf-generator/` within a minute or two

To update the app later, replace `index.html` and commit — Pages redeploys automatically.

> Note: a public repository means anyone with the link can open the tool. It contains only the blank form — no employee data is ever stored in it — but set the repo to private with GitHub Pro if you prefer (private repos require a paid plan for Pages).

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire app — form UI, fill logic, and the embedded blank SCIS-PAF-5000 |
| `README.md` | This file |

The only external dependency is the pdf-lib library loaded from cdnjs, so an internet connection is needed on first load; after that the page works offline if kept open or saved locally.
