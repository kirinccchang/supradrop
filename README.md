# SupraDrop

[繁體中文](README.zh-TW.md) | **English**

**Find Bluebook citation errors in your Word document footnotes** — automatically, in seconds, without installing anything.

🔗 **[lawreview.tools/supradrop](https://lawreview.tools/supradrop/)**

---

## Why this exists

Law review articles live or die by their citations. A misplaced *supra* note, an ambiguous *Id.*, a *Cf.* without an explanatory parenthetical — these are the kinds of errors that slip through manual review, especially in a document with hundreds of footnotes. Catching them means reading every short-form citation by hand: tracing each *supra* back to its original footnote, checking each *Id.* for ambiguity, verifying every signal has its parenthetical. It takes hours, and even careful editors miss things.

SupraDrop does it for you. Upload your Word document and get a complete list of every citation logic error — with the exact footnote number, the problem, and the Bluebook rule — in under a minute.

## What it does

SupraDrop reads your `.docx` file directly in your browser, scans every footnote, and flags violations of **24 Bluebook citation rules** across six categories: *supra* usage, *Id.* usage, signal parentheticals, pincites, URL archiving, and *hereinafter* consistency.

Every finding is marked as either an **error** (a mandatory Bluebook requirement your document violates) or a **warning** (a strong Bluebook recommendation worth reviewing). You can then download an annotated copy of your document with Word comments inserted at each problem footnote.

No installation. No account. No upload. Your document never leaves your browser.

## The 24 rules it checks

### Supra

| Rule | Severity | What it catches |
|------|----------|-----------------|
| `SUPRA_NONEXISTENT` | 🔴 Error | *supra* note N — but footnote N doesn't exist in this document (R. 4.2) |
| `SUPRA_FORWARD` | 🔴 Error | *supra* points to a *later* footnote — supra must always refer backward (R. 4.2) |
| `SUPRA_TO_SHORT_CITE` | 🔴 Error | *supra* points to another *supra* or *Id.* — supra must point to a full citation (R. 4.2) |
| `SUPRA_MISMATCH` | 🔴 Error | The author or title before "supra" doesn't appear in the referenced footnote — the footnote number is likely wrong |
| `SUPRA_WRONG_SOURCE_TYPE` | 🔴 Error | *supra* used for a case, statute, or constitution — prohibited by R. 4.2(a); use a short-form citation instead |
| `SUPRA_NO_PINCITE` | 🟡 Warning | Missing `, at [page]` when referring to a specific page (R. 4.2) |

### Id.

| Rule | Severity | What it catches |
|------|----------|-----------------|
| `ID_NO_PRECEDING` | 🔴 Error | *Id.* appears with no preceding citation to reference (R. 4.1) |
| `ID_AMBIGUOUS` | 🟡 Warning | The preceding footnote cites multiple sources — *Id.* is ambiguous about which one it refers to (R. 4.1) |
| `ID_STALE` | 🟡 Warning | *Id.* used more than 5 footnotes after the source was first cited — consider a short-form citation (R. 4.1) |

### Signal Parentheticals

| Rule | Severity | What it catches |
|------|----------|-----------------|
| `CF_NO_PAREN` | 🔴 Error | *Cf.* without an explanatory parenthetical beginning with a present participle (R. 1.2, R. 1.5) |
| `BUT_CF_NO_PAREN` | 🔴 Error | *But cf.* without an explanatory parenthetical (R. 1.2, R. 1.5) |
| `COMPARE_WITH_NO_PAREN` | 🔴 Error | *Compare … with …* without a parenthetical on each cited authority (R. 1.2, R. 1.5) |
| `SEE_GEN_NO_PAREN` | 🟡 Warning | *See generally* without an explanatory parenthetical — Bluebook strongly prefers one (R. 1.2, R. 1.5) |
| `EG_FORMAT` | 🟡 Warning | *See e.g.,* missing the required comma after "See" — write *See, e.g.,* not *See e.g.,* (R. 1.1) |
| `SEE_ALSO_NO_PAREN` | 🟡 Warning | *See also* without an explanatory parenthetical — Bluebook strongly prefers one (R. 1.2, R. 1.5) |
| `BUT_SEE_NO_PAREN` | 🟡 Warning | *But see* without an explanatory parenthetical — Bluebook strongly prefers one (R. 1.2, R. 1.5) |

### Pincites

| Rule | Severity | What it catches |
|------|----------|-----------------|
| `QUOTE_NO_PINCITE` | 🔴 Error | Direct quotation without a pincite (R. 3.2(a), R. 5.2) |
| `PINCITE_HYPHEN` | 🔴 Error | Page range uses a hyphen (`-`) instead of the required en-dash (`–`) (R. 3.2(a)) |
| `PINCITE_UNSHORTENED` | 🟡 Warning | Ending page not shortened: `1124–1129` should be `1124–29` (R. 3.2(a)) |
| `PINCITE_PP` | 🟡 Warning | `pp.` before a page number — the Bluebook never uses `pp.` for pincites; write the page number directly (R. 3.2) |

### Format

| Rule | Severity | What it catches |
|------|----------|-----------------|
| `FOOTNOTE_NO_PERIOD` | 🟡 Warning | Footnote does not end with a period (R. 1.1) |

### Internet URLs

| Rule | Severity | What it catches |
|------|----------|-----------------|
| `URL_NOT_ARCHIVED` | 🔴 Error | Internet citation without a perma.cc permanent archive link (R. 18.2.1) |

### Hereinafter

| Rule | Severity | What it catches |
|------|----------|-----------------|
| `HEREINAFTER_FORMAT` | 🔴 Error | *hereinafter* appears outside square brackets — write `[hereinafter X]`, not `(hereinafter X)` or bare text (R. 4.2(b)) |
| `HEREINAFTER_NEVER_USED` | 🟡 Warning | `[hereinafter X]` is defined but never referenced in any later footnote (R. 4.2(b)) |

## Features

- **Severity filter** — view All issues, Errors only, or Warnings only with one click
- **Smart suggestions** — `SUPRA_MISMATCH` searches the full document and suggests which footnote number you likely meant
- **Rule toggling** — enable or disable individual rules to match your journal's house style
- **Dismiss false positives** — mark any issue as dismissed; dismissed items stay hidden but can be reviewed later
- **Export annotated .docx** — your original document with a Word comment inserted at every problem footnote, ready to share with authors
- **Export CSV** — a structured table of every issue: footnote number, rule code, severity, and full description
- **Export TXT** — a plain-text report for quick sharing or printing
- **Multiple documents** — audit several `.docx` files in a single session without reloading
- **Fully client-side** — your documents never leave your browser; nothing is uploaded anywhere

## How to use

1. Open **[lawreview.tools/supradrop](https://lawreview.tools/supradrop/)**
2. Upload one or more `.docx` files — drag and drop onto the upload area, or click to browse
3. SupraDrop scans all footnotes instantly and displays results in the **Issues** tab
4. Use the **All / Errors / Warnings** filter pills to prioritize what to fix first
5. Click any flagged footnote to read the full text and the relevant Bluebook rule
6. Dismiss anything that doesn't apply to your document
7. Download the **annotated .docx** (with Word comments), **CSV**, or **TXT** report

> **Tip — Rules tab:** Each document has a **Rules** tab where you can toggle individual checks on or off. Useful when your journal follows a house style that differs from standard Bluebook — for example, if your journal doesn't require *see generally* parentheticals.

## Try it with the sample document

This repository includes [`SupraDrop_TestFixture.docx`](SupraDrop_TestFixture.docx), a sample Word document with intentional citation errors seeded across all 24 rules. Upload it at [lawreview.tools/supradrop](https://lawreview.tools/supradrop/) to see every check in action.

## Requirements

- A modern browser: Chrome, Firefox, Safari, or Edge
- A `.docx` Word document (not `.doc` or PDF)

## Privacy

Your documents are processed entirely in your browser's memory. No file is ever uploaded to any server. No account is required. No usage data is collected.

## Part of lawreview.tools

SupraDrop is one tool in the **[lawreview.tools](https://lawreview.tools)** suite — a free, open-source collection of Bluebook tools for law review editors and legal scholars:

| Tool | What it does | When to use it |
|------|-------------|----------------|
| **[Zotero Perma Archiver](https://lawreview.tools/zotero)** | Auto-archives URLs to perma.cc as you save items in Zotero | While writing |
| **[PermaDrop](https://lawreview.tools/permadrop/)** | Batch-archives all URLs in a `.docx` to perma.cc | Before submission |
| **SupraDrop** | Audits citation logic across all footnotes | Before submission |

Typical workflow: Zotero Perma Archiver while researching → PermaDrop to archive remaining URLs → SupraDrop to catch citation errors → submit.

## License

Copyright (C) 2026 [Kirin Chang](https://kirinchang.com)  
Research Fellow, U.S.-Asia Law Institute, NYU School of Law

Licensed under the [GNU Affero General Public License v3.0](LICENSE).  
If you modify this tool and run it as a network service, you must release your modified source code under the same license.

Not affiliated with or endorsed by The Bluebook or Zotero.
