# Magnifica Humanitas EPUB

Clean EPUB versions of Pope Leo XIV's *Magnifica Humanitas*, generated from the Holy See's HTML source.

Sources:

- English: https://www.vatican.va/content/leo-xiv/en/encyclicals/documents/20260515-magnifica-humanitas.html
- French: https://www.vatican.va/content/leo-xiv/fr/encyclicals/documents/20260515-magnifica-humanitas.html
- German: https://www.vatican.va/content/leo-xiv/de/encyclicals/documents/20260515-magnifica-humanitas.html
- Spanish: https://www.vatican.va/content/leo-xiv/es/encyclicals/documents/20260515-magnifica-humanitas.html
- Italian: https://www.vatican.va/content/leo-xiv/it/encyclicals/documents/20260515-magnifica-humanitas.html
- Polish: https://www.vatican.va/content/leo-xiv/pl/encyclicals/documents/20260515-magnifica-humanitas.html
- Portuguese: https://www.vatican.va/content/leo-xiv/pt/encyclicals/documents/20260515-magnifica-humanitas.html

The EPUBs include:

- cover image
- metadata
- table of contents
- footnotes

It validates with `epubcheck` 5.3.0 with no errors or warnings.

## Download

The EPUBs are not committed to this repository. They are built on every push
by the [Build EPUB](../../actions/workflows/build.yml) GitHub Actions workflow
and published as build artifacts.

To fetch them:

1. Open the [Build EPUB workflow runs](../../actions/workflows/build.yml).
2. Click the most recent successful run.
3. Download the `magnifica-humanitas-en` and/or `magnifica-humanitas-fr`
   artifacts from the **Artifacts** section at the bottom of the run summary.

With the [GitHub CLI](https://cli.github.com/) you can download them directly:

```sh
gh run download --repo pzmarzly/magnifica-humanitas-epub \
  --name magnifica-humanitas-en \
  --name magnifica-humanitas-fr
```

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
