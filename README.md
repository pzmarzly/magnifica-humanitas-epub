# Magnifica Humanitas EPUB

Clean EPUB versions of Pope Leo XIV's *Magnifica Humanitas*, generated from the Holy See's HTML source.

The EPUBs include:

- cover image
- metadata
- table of contents
- footnotes

It validates with `epubcheck` 5.3.0 with no errors or warnings.

## Download

The EPUBs are not committed to this repository. Every push to `main` rebuilds
them via the [Build EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/actions/workflows/build.yml)
GitHub Actions workflow, which publishes them to the rolling
[`latest` release](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest).

Each language is built from the Holy See's HTML source; the EPUB links always point to the newest build:

| Language | Source | Result |
| --- | --- | --- |
| English | [HTML](https://www.vatican.va/content/leo-xiv/en/encyclicals/documents/20260515-magnifica-humanitas.html) | [EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest/download/Magnifica%20Humanitas%20-%20Pope%20Leo%20XIV.epub) |
| French | [HTML](https://www.vatican.va/content/leo-xiv/fr/encyclicals/documents/20260515-magnifica-humanitas.html) | [EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest/download/Magnifica%20Humanitas%20-%20Pape%20Leon%20XIV%20(fr).epub) |
| German | [HTML](https://www.vatican.va/content/leo-xiv/de/encyclicals/documents/20260515-magnifica-humanitas.html) | [EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest/download/Magnifica%20Humanitas%20-%20Papst%20Leo%20XIV%20(de).epub) |
| Spanish | [HTML](https://www.vatican.va/content/leo-xiv/es/encyclicals/documents/20260515-magnifica-humanitas.html) | [EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest/download/Magnifica%20Humanitas%20-%20Papa%20Le%C3%B3n%20XIV%20(es).epub) |
| Italian | [HTML](https://www.vatican.va/content/leo-xiv/it/encyclicals/documents/20260515-magnifica-humanitas.html) | [EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest/download/Magnifica%20Humanitas%20-%20Papa%20Leone%20XIV%20(it).epub) |
| Polish | [HTML](https://www.vatican.va/content/leo-xiv/pl/encyclicals/documents/20260515-magnifica-humanitas.html) | [EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest/download/Magnifica%20Humanitas%20-%20Papie%C5%BC%20Leon%20XIV%20(pl).epub) |
| Portuguese | [HTML](https://www.vatican.va/content/leo-xiv/pt/encyclicals/documents/20260515-magnifica-humanitas.html) | [EPUB](https://github.com/pzmarzly/magnifica-humanitas-epub/releases/latest/download/Magnifica%20Humanitas%20-%20Papa%20Le%C3%A3o%20XIV%20(pt).epub) |

## Build

```sh
python3 -m pip install -r requirements.txt
for lang in en fr de es it pl pt; do
  python3 build_magnifica_humanitas_epub.py --lang "$lang"
done
epubcheck "Magnifica Humanitas - Pope Leo XIV.epub"
epubcheck "Magnifica Humanitas - Pape Leon XIV (fr).epub"
epubcheck "Magnifica Humanitas - Papst Leo XIV (de).epub"
epubcheck "Magnifica Humanitas - Papa León XIV (es).epub"
epubcheck "Magnifica Humanitas - Papa Leone XIV (it).epub"
epubcheck "Magnifica Humanitas - Papież Leon XIV (pl).epub"
epubcheck "Magnifica Humanitas - Papa Leão XIV (pt).epub"
```

The converter is not bound to English text. It is currently configured for the English, French, German, Spanish, Italian, Polish, and Portuguese Vatican pages; adding another language is mostly a matter of adding the Vatican URL and localized metadata.

Requires Python 3.12+.
