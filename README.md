<!-- Updated README.md generated from NoteFlow files -->
# NoteFlow

NoteFlow is a single-file, local-first note-taking app that runs entirely in your browser. It's built so your notes and data stay on your device unless you explicitly export or back them up.

Live demo (from another account): https://noteflowlocal.github.io/ (not part of this repo)

![NoteFlow Screenshot](./assets/noteflow-screenshot.png)

## Key ideas

- Single HTML file app — open `NoteFlow.html` in any modern browser and use it offline.
- Local-first: pages, icons, themes, and content are stored in your browser's localStorage by default.
- Export/Import: download your entire workspace as a JSON file for backups or migration.
- Optional Google Drive backup that writes to *your* Drive (you must provide credentials).

## Quick start

1. Download or open `NoteFlow.html` from this repository.
2. (Optional) Rename it to `index.html` for convenience when serving locally.
3. Open the file in Chrome, Firefox, Edge, or another modern browser.
4. Create pages, edit rich content, and everything will auto-save locally.

Tip: The project also includes `Homepage.html` — check it if you want a custom landing page.

## Features (summary)

- Rich text editor (headings, bold, italic, lists, blockquotes, code blocks)
- Page hierarchies using the `::` separator (infinite nesting)
- Pin/Star pages (favorite page loads on startup)
- Templates (Meeting Notes, Project Plan, To-Do, Journal, Weekly, Notes, Blank)
- Checklists and interactive task items
- Drag & drop sidebar reordering and nesting
- Duplicate, rename, and delete pages (deleting a parent removes children)
- Image paste/upload and base64 embedding
- Insert tables, audio, video, and web embeds
- Collapsible sections and callouts
- Emoji picker for page icons
- Word/character count and a 50-state undo/redo history per page
- Debounced auto-save (around 30s) and manual export/import
- Theme engine (Default, Dark, Sepia, Forest, Ocean, Sunset) and per-page theming
- Slash commands for quick block insertion
- Optional Google Drive backup (requires API_KEY + CLIENT_ID)

## Data & backup

- Primary storage: browser `localStorage` (fast, offline, browser-specific).
- Export: use the in-app Export button to download a JSON export (recommended regularly).
- Import: use the in-app Import button to restore a previously exported JSON — note: import replaces current pages.

Google Drive backup (optional):

1. Create credentials in Google Cloud Console (APIs & Services → Credentials): an OAuth 2.0 Client ID for a Web application and an API Key.
2. Open `NoteFlow.html` in a text editor and find the Google API placeholders in the script:

   ```js
   // Google Drive API Configuration
   const CLIENT_ID = 'YOUR_CLIENT_ID';
   const API_KEY = 'YOUR_API_KEY';
   ```

3. Replace with your credentials and uncomment `initGoogleDrive();` near the bottom of the script (in the `DOMContentLoaded` handler).
4. Reload the page. The Save to Drive button should become functional and will save to your Drive (NoteFlow does not receive or store those credentials).

Security note: Do not commit your credentials to a public repo.

## Keyboard shortcuts (selected)

- Ctrl/Cmd+N — New page
- Ctrl/Cmd+S — Save
- Ctrl/Cmd+Z — Undo
- Ctrl/Cmd+Y — Redo
- Ctrl/Cmd+B — Bold
- Ctrl/Cmd+I — Italic
- F11 — Toggle Focus Mode
- Esc — Close modals/panels

See the in-app shortcut help for the full list.

## Developer notes

- The app is intentionally distributed as a single self-contained HTML file (`NoteFlow.html`). Open this to run the app.
- If you want to customize the app, edit `NoteFlow.html` and search for `// Google Drive API Configuration`, `pageTemplates`, or `data-theme` definitions.
- To change/add themes, search for `[data-theme="` in the style block and update CSS variables under `:root`.

## Contributing & Improvements

Small, safe suggestions that add value:

- Add a screenshot or animated GIF to `README.md` (there's an image at `assets/noteflow-screenshot.png`).
- Add a `LICENSE` file to make the intended license explicit.
- Add a small script to validate JSON exports or an automated export test.

If you'd like help splitting the single HTML into a modular source tree or adding automated tests, I can propose a plan and apply changes.

## Files of interest

- `NoteFlow.html` — the main app (single-file). Open this to run the app.
- `Homepage.html` — optional landing page included in this repo.
- `assets/` — images and static assets.

---

NoteFlow — local-first, private, and simple. Your notes, your device, your choice.
