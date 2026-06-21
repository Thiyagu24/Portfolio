# Thiyagarajan V — Portfolio

A dark, chrome-accented portfolio site built with Vite, React, TypeScript, and Tailwind CSS.

## Install & run

```bash
npm install
npm run dev       # local dev server
npm run build     # production build to dist/
npm run preview   # preview the production build
```

## Project structure

```
src/
  data/portfolio.json     ← all editable content lives here
  types/portfolio.ts      ← TypeScript types for the data shape
  hooks/usePortfolio.ts   ← typed hook that exposes the data
  components/             ← presentational components (no hardcoded content)
  index.css               ← global styles, hero gradient, marquee animation
  App.tsx                 ← assembles all sections
```

## Editing content

Everything visible on the site — name, bio, skills, experience, projects,
education, testimonials, social links — comes from `src/data/portfolio.json`.
Edit that file and the site updates automatically; no component code needs
to change.

Notes on specific fields:

- **`profile.social`**: leave any value as an empty string `""` to hide that
  link everywhere (hero, footer). Currently `github`, `instagram`, and
  `website` are empty — fill them in once those links exist.
- **`projects[].link`**: leave empty to hide the "Live Project" button on
  that card.
- **`projects[].image`**: leave empty to show a dark placeholder with the
  project title instead of a broken image.
- **`projects[].highlight`**: set to `true` to pin a project to the top of
  the Projects section.
- **`testimonials`**: currently empty (no testimonials were available yet).
  Add objects in the shape `{ id, quote, name, role, avatarColor }` and the
  Testimonials section will appear automatically with the marquee enabled.
- **Services**: the four service rows (Backend, AI/LLM, Frontend, Cloud) are
  currently hardcoded in `src/components/ServicesSection.tsx` — there's a
  `TODO` comment there marking where to move them into the JSON file once
  the offering is finalized.

## Design notes

- Background `#0C0C0C`, chrome/silver gradient headline (`.chrome-text` /
  `.hero-heading` in `index.css`), purple → magenta → orange gradient CTAs
  (`.accent-btn`), Kanit font throughout.
- The Testimonials marquee is CSS-only, pauses on hover, and falls back to
  a horizontally scrollable, snap-aligned row under
  `prefers-reduced-motion: reduce`.
- All sections use `scroll-margin-top` so the fixed navbar doesn't cover
  anchored headings on jump-to-section navigation.
