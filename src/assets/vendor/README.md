# Self-hosted libraries

Pinned copies of the two libraries the site used to pull from `cdn.jsdelivr.net`.
Serving them ourselves means no visitor IP is disclosed to a third-party CDN, and
the site keeps working if that CDN has an outage.

| File | Library | Version | License | Source |
|---|---|---|---|---|
| `three.module.min.js` | three.js | r162 (`0.162.0`) | MIT | `https://cdn.jsdelivr.net/npm/three@0.162.0/build/three.module.min.js` |
| `lenis.min.js` | Lenis | 1.1.14 | MIT | `https://cdn.jsdelivr.net/npm/lenis@1.1.14/dist/lenis.min.js` |

Both are byte-for-byte the files the CDN serves, at the versions that were
already pinned — vendoring them did not upgrade anything. three.js uses the
**minified** build: same r162, 259KB -> 168KB gzipped and ~600KB less script
for the browser to parse.

`three.module.min.js` is referenced through the import map in `src/index.html`:

```html
<script type="importmap">{"imports":{"three":"./assets/vendor/three.module.min.js"}}</script>
```

Import map values must be absolute or begin with `./`, `../`, or `/` — a bare
`assets/...` path is invalid and will silently fail to resolve.

The site imports only `three` itself (`import * as THREE from 'three'`); no
`three/addons/*` modules are used, so this single bundled file is sufficient.
If addons are ever needed, they must be vendored here too, and the import map
extended with a `"three/addons/"` prefix entry.

three.js carries its MIT header inline. Lenis is minified with the header
stripped; its license is MIT, © Studio Freight.
