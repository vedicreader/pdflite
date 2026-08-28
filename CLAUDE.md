# Working in this repo

nbdev. The notebooks under `nbs/` are the source; `pdflite/*.py` is generated. Edit the notebook,
run `nbdev_export`, never edit the `.py`. CI runs `nbdev_export` and fails on a diff.

## What belongs here

Anything that turns a PDF into text and repairs what conversion broke. litesearch, fossick and
kosha all import from here, so a fix lands once.

Chunking does not belong here. Neither does anything that knows about an index, a vault or a
document tree. `pdf_md` returns markdown and stops.

## The two shapes

`pdf_md(pages=False)` returns one string, pages joined by `---`. `pages=True` returns a list, one
entry per page, which is what a chunker that cites page numbers needs. Both come from the same
pass, so they cannot disagree.

## Dependencies

`fastcore` and `pdf-oxide` at runtime. `liteparse` is imported inside `ocr_parse`. No extras: an
optional package is imported where it is used and raises saying what to install.

## Prose in notebooks

Short. Lead with what the code does. Numbers instead of adjectives. No em dashes, no bold inside
a paragraph, no rhetorical questions. A rationale longer than three sentences belongs in a
docstring.

## Docstrings and comments

One line. A second sentence only for a measured number or a footgun. Inline comments in a `def`
signature are nbdev docments and become the API parameter table. A comment that restates the line
under it goes.
