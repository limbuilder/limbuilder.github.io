# LimBuilder Homepage Design

**Date:** 2026-07-22  
**Status:** Approved for planning  
**Repo:** `limbuilder.github.io`

## Goal

Replace the root redirect page with a minimal personal link hub that shows LimBuilder’s identity and lists existing tools, starting with yt-converter.

## Decisions

| Topic | Choice |
| --- | --- |
| Display name | `LimBuilder` (aligned with GitHub / domain) |
| Avatar | GitHub avatar: `https://github.com/limbuilder.png?size=200` |
| Page type | Linktree-style: avatar + name + short subtitle + project links |
| Visual style | Ink & Teal (dark base, teal accent; kinship with yt-converter) |
| Implementation | Single static `index.html` with inline CSS/animations |

## Layout

Centered single column, no navigation. First viewport is the whole composition:

1. Circular avatar
2. Display name: **LimBuilder**
3. Subtitle: `tools & experiments`
4. Project link list (one row per project)
5. Light footer: `© LimBuilder`

Max content width ≈ 420px. Mobile and desktop share the same centered layout.

## Visual system

### Color

- Background: `#0a0a0a`
- Surface (link rows): `#111`
- Border: `#2a2a2a`
- Text: `#fff` / muted `#888`
- Accent: `#00ACB3`
- Atmosphere: subtle teal radial glow so the page is not a flat black slab

### Typography

- Display: **Syne** (Google Fonts)
- Body / links: **DM Sans** (Google Fonts)

### Motion

1. Staggered entrance: avatar → name → subtitle → links (fade + slight rise)
2. Link hover: border/accent brightens; arrow shifts right
3. Avatar: very light teal border “breathing” — present but not flashy

## Content

### Project link (v1)

- Title: `yt-converter`
- Description: `Free YouTube → MP3 / MP4`
- URL: `/yt-converter/` (same-origin relative path)
- Behavior: entire row is clickable; open in a new tab (`target="_blank"` + `rel="noopener noreferrer"`)

### Out of scope (v1)

- Bio paragraph, social icon row, analytics, build tooling, multi-page framework
- Extra projects beyond yt-converter (add later by editing the HTML list)

## Technical plan

1. Replace root `index.html` (remove meta refresh / `location.replace` redirect to yt-converter)
2. Keep everything in one HTML file: markup + CSS (variables) + keyframe animations
3. Load Syne + DM Sans from Google Fonts
4. Avatar: GitHub CDN image with explicit `width`/`height` and meaningful `alt`
5. Basic SEO: `<title>`, meta description, canonical to `https://limbuilder.github.io/`
6. Favicon: GitHub avatar (or simple derived icon) linked in `<head>`
7. Accessibility: semantic landmarks, focus styles on the link row, sufficient contrast

## Success criteria

- Visiting `https://limbuilder.github.io/` shows the hub (no auto-redirect)
- Avatar, LimBuilder name, and yt-converter link are clear on first paint
- yt-converter opens correctly from the link row
- Page looks intentional on phone and desktop under Ink & Teal styling
