# Checklist App — Project Rules & Architecture

## Overview
A reusable checklist app (single HTML file) for grocery runs, travel packing, and other personal lists. No frameworks, no backend — vanilla HTML/CSS/JS with localStorage.

## Tech Stack
- Single file: `index.html`
- No frameworks — vanilla HTML/CSS/JS only
- Data stored in `localStorage` key: `checklist_v1`
- Preview server: `npx serve -p 3456 .` (via `.claude/launch.json`)

## Data Model
```js
lists = [
  {
    id: string,        // genId() — timestamp + random
    name: string,      // list name e.g. "Grocery"
    items: [
      {
        id: string,
        text: string,
        checked: boolean
      }
    ],
    createdAt: number  // Date.now()
  }
]
```

## App Structure (SPA — two views)
- **Home view** (`#home-view`) — list of all checklists as cards
- **Detail view** (`#detail-view`) — items inside a chosen list
- Navigation via CSS class toggling: `slide-out` / `slide-in`
- No page reloads

## Key Functions
| Function | Purpose |
|---|---|
| `renderHome()` | Render all list cards on home screen |
| `renderDetail()` | Render items for current list |
| `goHome()` | Navigate back to home |
| `goDetail(listId)` | Navigate into a list |
| `toggleItem(itemId)` | Check/uncheck an item |
| `deleteItem(itemId)` | Remove an item |
| `resetList()` | Uncheck all items in current list |
| `deleteCurrentList()` | Delete entire list (with confirm dialog) |
| `openAddSheet()` | Open bottom sheet (add list or add item) |
| `confirmSheet()` | Save new list or item |
| `showDialog()` | Show confirm dialog |
| `save()` / `load()` | Read/write localStorage |

## Chosen Design — Soft Aurora
- **Font:** Plus Jakarta Sans
- **Background:** `#c8baf0` base + animated coloured blobs (purple, pink, teal, lavender)
- **Blob opacity:** 0.75
- **Cards:** `rgba(255,255,255,0.72)`, `backdrop-filter: blur(16px)`, `border-radius: 20px`
- **Card border:** `rgba(180,160,220,0.25)`
- **Primary gradient:** `linear-gradient(135deg, #6d28d9, #d946ef)` — deep purple to fuchsia
- **Progress bar gradient:** `linear-gradient(90deg, #6d28d9, #d946ef)`
- **Text primary:** `#1a1a2e`
- **Text soft:** `#5a5a7a`
- **Text muted:** `#9898b8`
- **FAB:** same gradient, `box-shadow: 0 6px 24px rgba(91,33,182,0.45)`

## Design Preview Files (for reference only — not the real app)
- `preview-aurora.html` — chosen Soft Aurora style ✅
- `preview-glass.html` — Glassmorphism (not chosen)
- `preview-neo.html` — Neobrutalism (not chosen)
- `preview-dark.html` — Dark Neon (not chosen)

## Rules
- Always apply changes to `index.html` — that's the real app
- Preview files are reference only — do not overwrite them
- Test on mobile viewport before declaring done
- All data must persist in localStorage
