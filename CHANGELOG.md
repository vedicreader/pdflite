# Release notes

<!-- do not remove -->

## 0.0.4
- `dev` is an extra, as nbdev's CI installs it, with the uv group pointing at it; CI gets liteparse and the OCR test passes.

## 0.0.3
- `pdf_md` fixed: 0.0.2 raised `AttributeError` reading `pdf_pages`.

## 0.0.2
- `pdf_pages`: each page with its route (`text`, `ocr`, `scanned`); OCR runs on scanned pages only.
- `thin_text`: an image-only page counts as scanned.
- `ocr_parse(pages=)`.

## 0.0.1
initial release
