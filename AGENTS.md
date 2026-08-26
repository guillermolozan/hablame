# AGENTS.md

Single-file web app: everything (HTML, CSS, JS) lives in `hablame.html`. No build system, no dependencies, no tests. Don't scaffold extra files or tooling.

## Running / testing
- Open `hablame.html` directly, or serve statically (e.g. `python3 -m http.server`).
- Verify manually in **Chrome** or **Safari (iOS 17+)** — Firefox lacks the Web Speech API and just shows the unsupported banner.
- Microphone access requires a secure context; if permission fails from `file://`, serve over `http://localhost`.

## Conventions & gotchas
- All user-facing strings are Spanish; default recognition language is `es-PE`. Keep new strings in Spanish.
- Deliberate behaviors — do not "fix": `recognition.onend` restarts the stream unless `manualStop` (Chrome cuts after silence), and `FIRST_WORD_GRACE` (6 s) delays silence-stop before the first word.
- Adding a setting requires touching all of: `DEFAULTS`, the settings-sheet markup, `el`, `applyConfig()`, and an input listener. Persistence goes through the `store` wrapper (localStorage keys `config` / `history`, with in-memory fallback) — use it, never raw `localStorage`.
- Text auto-fit uses a binary search on font size inside `fitText()`; every text change must go through `render()` so refitting happens.
