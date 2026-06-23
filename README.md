# dev-poll

A single-page personal portfolio / **DevPool application** site for **Piyawat Upala** — a Swiss /
brutalist design recreated from a reference motion video, built as one self-contained `index.html`
with **CDN-only** libraries (no build step, no `node_modules`).

🔗 Repo: [github.com/piyawat4rm/dev-poll](https://github.com/piyawat4rm/dev-poll)

---

## ✨ Features

- **Single file** — everything (markup, styles, scripts) lives in `index.html`.
- **Animated hero** — an infinite horizontal name marquee with a cut-out portrait, driven by GSAP.
- **Scroll experience** — Lenis smooth scrolling synced with GSAP ScrollTrigger; reveal-on-scroll,
  clip-path image reveals, and an animated wordmark.
- **Light / dark theme** — a nav toggle backed by CSS variables; defaults to light, persists the
  choice to `localStorage`, and is deep-linkable via `?theme=light|dark`.
- **Live API demo** — fetches Star Wars characters at runtime and **paginates client-side via
  `Array.slice`** (Prev / Next + page indicator), with a staggered card animation on each page.
- **Fully responsive** — mobile-first using standard Tailwind breakpoints (`sm md lg xl`), with a
  hamburger menu below `md`.
- **Bilingual content** — Thai + English (e.g. the About / application fields).
- Respects `prefers-reduced-motion`.

---

## 🧱 Libraries used (all via CDN)

| Library | Version | Purpose | Source |
|---|---|---|---|
| **Tailwind CSS** | v3 (Play CDN) | Utility-first styling, theme tokens, dark mode | `https://cdn.tailwindcss.com` |
| **GSAP** | 3.x | Animation engine (marquee, reveals, stagger) | `cdn.jsdelivr.net/npm/gsap@3` |
| **ScrollTrigger** | 3.x | Scroll-driven GSAP animations | `cdn.jsdelivr.net/npm/gsap@3/dist/ScrollTrigger.min.js` |
| **Lenis** | 1.x | Smooth scrolling (synced to ScrollTrigger) | `cdn.jsdelivr.net/npm/lenis@1` |
| **Google Fonts** | — | `Anton` (display), `Inter` (body), `Noto Sans Thai` (Thai) | `fonts.googleapis.com` |

### External API

| API | Endpoint | Used for |
|---|---|---|
| **starwars-api** (akabab) | `https://akabab.github.io/starwars-api/api/all.json` | 87 characters, paginated by slice in the "Fetch & Tech Stack" section |

> Tailwind's Play CDN compiles in the browser and is intended for prototyping/demos. For a
> production build, install Tailwind via its CLI/PostCSS pipeline instead.

---

## 📁 Project structure

```
dev-poll/
├── index.html          # the entire site (HTML + Tailwind config + <style> + scripts)
├── images/
│   ├── profile-cutout.png          # hero portrait (background removed)
│   ├── ant-design--code-filled.svg # nav logo
│   └── fullstack-meme.jpg          # meme section
├── reference-video.mp4 # the design this site was recreated from
└── README.md
```

---

## 🚀 Run locally

No build needed — but serve over HTTP (not `file://`) so the fonts, images, and `fetch()` work:

```bash
# from the project root
python3 -m http.server 8000
# then open http://localhost:8000
```

(Any static server works, e.g. `npx serve`.)

---

## 🗂️ Sections

1. **Hero** — fixed pill nav (logo · links · theme toggle · hamburger), giant name marquee + portrait.
2. **About** — DevPool application fields: ชื่อ · สังกัด/งานใน กฟภ. · เหตุผลที่อยากเข้า DevPool.
3. **Fetch & Tech Stack** — live Star Wars character grid (paginated) + the tech-stack list.
4. **Define · Design · Deliver** — layered headline + image with a clip-path reveal.
5. **Meme** — a developer meme.
6. **Contact / Footer** — CTA, giant wordmark, social links.

---

## 🎨 Theming

Colors are CSS variables (`--c-paper`, `--c-ink`, `--c-coal`, …) mapped to Tailwind color names
(`bg-paper`, `text-ink`, `border-hair`, …). The `.dark` class on `<html>` flips the variables, so the
whole page re-themes from one place. The display fonts and breakpoints are configured inline in the
`tailwind.config` block near the top of `index.html`.

---

## ✏️ Customizing

Editable spots are marked with comments in `index.html`:

- **About answers** — `<!-- แก้ไขเหตุผลของคุณเองได้ที่ย่อหน้านี้ -->`
- **Tech stack rows** — `<!-- แก้ไขรายการเทคโนโลยีของคุณเองได้ที่นี่ -->`
- **API endpoint / page size** — see the `loadStarwars()` function (`PER_PAGE = 6`).
