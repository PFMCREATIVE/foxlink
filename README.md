# FoxLink v0.0.1

Our own https link in place of LinkYourFile (Sam 2026-10-15). A FoxLink is `https://<host>/open?p=<base64>`:
the same `?p=` value LinkYourFile and the old `foxio://open?p=` links carry (standard base64 of the
Lucid path, `=` as `%3D`), so every existing value works unchanged.

`open/index.html` decodes the path in the browser only (no network, no analytics), hands the browser
`foxview://open?p=…`, then `foxio://open?p=…` a moment later for builds before FoxLink, and shows the
path with a Copy button and Finder steps when nothing opens. `index.html` is the landing page.

Hosting is Sam's call (GitHub Pages or Cloudflare Pages on a PFM domain); nothing here is published.
Test locally: `python3 -m http.server 8765 --directory FoxLink` then open
`http://localhost:8765/open/?p=<value>`; `Tests/test_foxlink_page.py` checks the decode in node.
