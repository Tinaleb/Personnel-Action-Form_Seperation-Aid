# PAF Generator

A browser-based tool that completes the SCIS Personnel Action Form (5000 Series) for employee separations — one at a time or in bulk. Built for supervisors and program managers who process terminations regularly and shouldn't have to hand-type the same form dozens of times.

Everything runs on your device. The blank form is embedded in the page, PDFs are generated locally in the browser, and **no employee data is ever sent or stored anywhere**.

---

## Quick start

Open the app (GitHub Pages URL or `index.html` directly). Four fields are all that's required:

1. **Employee name**
2. **Client site / area**
3. **What happened** (separation code)
4. **Last date worked**

Tap **Download this PAF**. A completed, named PDF (`PAF_Lastname_Firstname_YYYY-MM-DD.pdf`) downloads, ready to sign and send to HR.

### What auto-fills

Choosing the separation code does most of the work:

- **Voluntary / Involuntary** checkbox is set automatically (layoffs count as involuntary, code 99 leaves both blank)
- **Rehire eligibility** is suggested — no-call-no-show and walked-off default to ineligible, layoffs to eligible — and can be overridden with a tap
- **Reason** line is drafted in HR-ready language and stays editable
- **Effective date** and **last date paid** copy from last date worked
- **Requested by** and **department number** are remembered on your device after first use

Address, phone, SSN last four, refunds, and comments live under *More fields (optional)*.

---

## Signing (optional)

Under **Signature**, you can sign the *Requested by* line without any other software — three ways:

- **Draw** — sign with a mouse, finger, or stylus on the pad
- **Type** — type your name and pick a signature-style font
- **Upload** — use a PNG or a photo of your signature on paper

Tap **Save signature** and it's stamped onto the *Requested by* line of every PAF you download, single or bulk. Check **Remember on this device** to keep it for next time. The **Manager / Approved-by** line is always left blank for that person to sign themselves.

---

## Bulk mode — same reason for everyone

For layoffs, contract expirations, or any batch sharing one separation reason:

1. In **Bulk entry**, pick the code and the shared last date worked
2. Paste the employee list, one per line
3. Tap **Add all to batch**, then **Download all**

Names alone are enough. After a name you may add a site, a pay rate, or a per-person date to override the defaults — in any order, separated by commas, tabs, or dashes. Pasting a range straight from Excel works.

```
Smith, John A.
Johnson, Marcus — GDOTS Wilkes Barre
Rivera, Ana, $21.75/hr
Lee, David, GDOTS Hanover, $23.00/hr, 07/12/2026
```

A live counter confirms how many employees were detected before you commit them to the queue.

### Mixed reasons

Use the single-entry form, tap **Add to batch** after each person (the form clears itself), then **Download all** once.

---

## Publishing on GitHub Pages

1. Create a repository (e.g. `paf-generator`)
2. Upload `index.html`, `README.md`, and `LICENSE` to the repository root
3. **Settings → Pages → Source**: branch `main`, folder `/ (root)`, save
4. Live at `https://<username>.github.io/paf-generator/` within a couple of minutes

Updates are just a new commit of `index.html` — Pages redeploys automatically.

**Note on visibility:** Pages on a free account requires a public repository, meaning anyone with the link can open the tool. It contains only the blank form — no employee information — so this is generally acceptable, but a private repository (GitHub Pro) is an option if preferred.

---

## Repository contents

| File | Purpose |
|---|---|
| `index.html` | The complete app — UI, fill logic, and embedded blank SCIS-PAF-5000 |
| `README.md` | This guide |
| `LICENSE` | Terms of use |

The only external dependency is the pdf-lib library loaded from a CDN on page load; after loading, the app works without a connection.

---

## Notes

- Signature lines are intentionally left blank for wet or digital signature after download
- The Separation Code dropdown mirrors the official code list on form SCIS-PAF-5000 (Rvsd 6/12/2018)
- Each user's browser remembers its own "Requested by" default — supervisors sharing the link each get their own
- Nothing typed into the app leaves the device; closing the tab clears any unsaved queue
