# Self-hosted fonts

These are the **latin** and **latin-ext** subsets of the Google Fonts originals,
served from our own origin so that no visitor IP address is disclosed to Google.
(Loading fonts from `fonts.googleapis.com` / `fonts.gstatic.com` transmits the
visitor's IP to Google on every page view; that is what these files avoid.)

The `@font-face` rules live inline at the top of the `<style>` block in
`src/index.html`, with the same `unicode-range` values Google publishes, so the
browser still downloads only the subset it actually needs.

| File | Family | Weights used |
|---|---|---|
| `anta-latin.woff2`, `anta-latin-ext.woff2` | Anta | 400 |
| `dancing-script-latin.woff2`, `dancing-script-latin-ext.woff2` | Dancing Script | 600 |
| `montserrat-latin.woff2`, `montserrat-latin-ext.woff2` | Montserrat | 400, 500 |
| `outfit-latin.woff2`, `outfit-latin-ext.woff2` | Outfit | 200, 300, 400, 500, 600 |
| `share-tech-mono-latin.woff2` | Share Tech Mono | 400 — **currently unused** |

`Share Tech Mono` is declared but no rule in `index.html` uses it. It is kept
because CLAUDE.md lists it in the brand system as the labels/mono face, and
`unicode-range` means an unused family is never actually downloaded. Delete the
file and its `@font-face` if it stays unused.

Montserrat and Outfit are **variable** fonts: Google serves one file for all of
their weights, so each weight's `@font-face` points at the same file here too.
That is why there are 9 files for 19 declarations.

## Licensing

All five families are licensed under the **SIL Open Font License, Version 1.1**,
which expressly permits redistribution and self-hosting. Full license text:
<https://openfontlicense.org/open-font-license-official-text/>

- Anta — © The Anta Project Authors (<https://github.com/googlefonts/anta>)
- Dancing Script — © The Dancing Script Project Authors (<https://github.com/impallari/DancingScript>)
- Montserrat — © The Montserrat Project Authors (<https://github.com/JulietaUla/Montserrat>)
- Outfit — © The Outfit Project Authors (<https://github.com/Outfitio/Outfit-Fonts>)
- Share Tech Mono — © The Share Tech Mono Project Authors (<https://github.com/googlefonts/sharetechmono>)

## Regenerating

Re-run the fetch against the same `css2` URL with a modern browser User-Agent
(an old UA makes Google serve TTF instead of WOFF2), keep only the `latin` and
`latin-ext` subsets, and dedupe by source URL.
