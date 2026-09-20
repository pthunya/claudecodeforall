# AGENTS.md

This file provides guidance to coding agents (Claude Code, etc.) when working with code in this repository.

## What this is

A single static-HTML Thai food recommendation site, no build tooling, no package manager, no framework, no test runner. The entire app (HTML + CSS + JS) lives in one file: `thai-food-website/index.html`.

## Running / testing

There is no build step and no automated test suite.

- View the site: open `thai-food-website/index.html` directly in a browser (e.g. `open thai-food-website/index.html` on macOS). It runs fine from `file://` — the only external resources are a Google Fonts stylesheet and the local `tomyum-goong.jpg`.
- Verification is manual. `thai-food-website/task.md` §7 has the outstanding manual test checklist: random-pick button, category filter, favorite heart toggle + persistence, and reload-to-confirm-localStorage.
- After any change, reload the page in a real browser and click through the affected feature — there's no other way to catch regressions here.

## Architecture (all inside `index.html`)

- **Data**: `dishes` is a plain array of objects (`id`, `name`, `category`, `desc`, `icon`, optional `img`, optional `ingredients`) hardcoded in the `<script>` block. `categories` is a separate hardcoded list used to drive the filter bar — adding a dish with a new category also requires adding it here.
- **State**: three variables — `favorites` (a `Set` of dish ids), `currentFilter`, `searchQuery` — plus two localStorage keys: `thaiFoodFavorites` (the persisted favorite ids) and `thaiFoodFavoritesRevealed` (a one-way flag; once the favorites section has been shown for the first time it stays visible permanently even if favorites drops back to 0 — see "Favorite" in CONTEXT.md).
- **Rendering**: no framework/virtual DOM. Each `render*` function (`renderFilterBar`, `renderGrid`, `renderRandomResult`, `renderFavorites`, `renderDetailPage`) rebuilds `innerHTML` from current state via string templates. State-changing handlers (e.g. `toggleFavorite`) call the relevant `render*` functions directly afterward rather than any reactive/diffing mechanism.
- **Detail view**: implemented as a modal overlay (`#detailOverlay`), not a real page/route. It's synced to `location.hash` (`#dish-<id>`) via `syncDetailFromHash()` / `openDetail()` / `closeDetail()`, so the detail view is shareable and back-button-friendly despite being a single-page app.
- **Events**: one delegated `click` listener on `document` dispatches by `data-*` attribute (`data-toggle-fav`, `data-filter`, `data-close-detail`, `data-card-id`) instead of per-element listeners — new interactive elements should follow this pattern rather than adding new `addEventListener` calls.

## Domain language

Read `thai-food-website/CONTEXT.md` before touching terminology or behavior — it defines **Dish**, **Category**, **Random Pick**, and **Favorite**, and flags two non-obvious rules: Random Pick always draws from all dishes regardless of the active Category filter, and the Favorites section never re-hides once revealed.

## Other repo contents

- `hello_world/main.rs` is an unrelated scratch file, not part of the website.
- `.claude/settings.json` wires `Stop` and `PermissionRequest` hooks to speak "Done" / "Need Approve" via macOS `say`.
