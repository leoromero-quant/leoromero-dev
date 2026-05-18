# leoromero.dev

Personal landing site for Leonardo Suárez Romero, PhD. Single-page static site,
designed to mirror the visual identity of `prob-edge.com` so the personal brand
and the commercial product read as a coherent ecosystem.

## Stack

- Static HTML + inline CSS (no framework, no build step)
- Tokens compatible with prob-edge.com (dark theme, cyan/green gradient)
- System font stack + `ui-monospace` for accents
- Vercel for deploy

## Local preview

Open `index.html` directly in a browser, or serve with any static server:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

## Deploy

1. Push to `github.com/leoromero-quant/leoromero-dev`.
2. Connect the repo to Vercel.
3. Add custom domain `leoromero.dev` in the Vercel project settings.
4. Point DNS at Vercel per the instructions in the Vercel domain UI.

The `vercel.json` in this repo sets clean URLs, no trailing slashes, and
sensible security headers.

## Notes on content

- No mention of RyR Data Science, Smart-Delta LLC, or HNW practice per the
  brand-separation policy.
- The Writing section currently has two entries: the scheduled LinkedIn
  Prob-Edge article (publishes 2026-05-19) and the doctoral dissertation.
  Add new pieces by appending `<li>` entries inside `<ul class="writing-list">`.
- The Projects section is the single most-trafficked block when a recruiter
  visits. Keep the three cards (Prob-Edge, Smart-Beta, PaPs Mercados) ahead
  of anything experimental.

## License

Site copy and code: All rights reserved.
