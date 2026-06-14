# Checklist App — Memory & Lessons Learned

## Session 1 — 2026-06-08

### Design decisions
- Rachel chose **Soft Aurora** over Glassmorphism, Neobrutalism, and Dark Neon
- Key feedback: Glassmorphism was nice but harder to read outdoors; Neobrutalism too bold; Aurora felt calming
- Background was adjusted: base colour darkened from `#f0eeff` → `#c8baf0`, blob opacity increased to 0.75
- Accent colours went through several iterations — avoid pure teal (`#0891b2`) as it reads as "too blue"; avoid pure pink (`#ec4899`) as it reads as "too pink"; settled on deep purple (`#6d28d9`) → fuchsia (`#d946ef`)

### Technical gotchas
- **FAB gradient had explicit `0%` and `100%` stop markers** — `replace_all` on plain gradient strings didn't catch it. Always grep for both forms when updating colours across a file
- **Preview server stops when Claude Code goes idle** — local `localhost:3456` links only work while the session is active. At the start of each session, the server must be restarted (Claude Code does this automatically via `.claude/launch.json`). If the link is dead mid-session, ask Claude to restart it. `localhost` only works on the Mac — phones need the local IP (`192.168.x.x:3456`) and must be on the same Wi-Fi. Permanent fix: deploy to GitHub Pages so no server is needed
- Git repo was not initialised at session start — remember to `git init` on new projects before first commit

### UX decisions
- Completed items are separated into a "Completed (N)" section below unchecked items — keeps active items prominent
- Reset button unchecks all items for reuse — this is the core differentiator from a regular to-do app
- Confirm dialog required before deleting an entire list
- Items ordered: unchecked first, checked below with section header

### What's ready
- `index.html` is a fully working app with the original purple design
- `preview-aurora.html` has the finalised Soft Aurora design (static, no real data)
- Next step is to port the Aurora CSS into `index.html` to make it the real app
