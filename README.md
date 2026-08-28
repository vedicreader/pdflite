# pdflite

PDF to markdown. Layout repair, OCR fallback, and images written to disk.

```python
from pdflite import pdf_md

md    = pdf_md('statement.pdf', out_path='out')              # one string, pages joined by ---
pages = pdf_md('statement.pdf', out_path='out', pages=True)  # one entry per page
```

`pdf_md` converts every page with pdf-oxide, then fixes four things conversion gets wrong:

- a word broken across lines by a hyphen is rejoined
- a two-column table reflowed into one stream is swapped for the plain-text layer, but only when
  that strands fewer values
- a scanned page with no text layer goes through OCR
- reader chrome from a print-to-PDF is dropped

The parts are exported too: `clean_md`, `fix_layout`, `orphan_vals`, `scrambled_layout`,
`needs_ocr`, `ocr_parse`, `oxide_parse`.

## Install

```
pip install pdflite
```

OCR needs `liteparse`, imported when it runs. There are no extras: an optional package is one
that is imported where it is used and raises saying what to install.

## Why it exists

litesearch, fossick and kosha each had a copy of these helpers, and four of the five had drifted.
A PDF cleaned through one kept junk the same PDF cleaned through another dropped. One copy, one
behaviour.
