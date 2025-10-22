# TyperScene — Cinematic

[![Live demo](https://img.shields.io/badge/demo-live-brightgreen?style=for-the-badge)](https://T0ls.github.io/typerScene---Cinematic/index.html)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC--BY--4.0-0a66ff?style=for-the-badge)](https://creativecommons.org/licenses/by/4.0/)
[![One-file](https://img.shields.io/badge/one--file-index.html-39ff14?style=for-the-badge)](#)
[![Made with HTML/CSS/JS](https://img.shields.io/badge/made%20with-HTML%20%2F%20CSS%20%2F%20JS-1f6feb?style=for-the-badge)](#)

A **cinematic, code-themed typewriter**: press keys (even at random) and text appears on screen with a blinking cursor, incremental syntax highlight, keyclick sounds, terminal-style themes, and a *clean* fullscreen mode with optional *PC stats* overlay. The whole project lives in **one HTML file** — portable, offline-ready, zero build, zero dependencies.

> Just open `index.html` in a modern browser and start typing.

---

## Why a single file?

I wanted it to be **user‑friendly**: download and open — **that’s it**. No install, no config, no dependencies. It’s designed to be portable and immediate, even offline.

---

## Main features

- **One‑file app**: everything in `index.html` (HTML + CSS + JS) — open and it works.
- **Typing engine** with *chunk per key* and *micro‑typing bursts*; **Space** temporarily multiplies the chunk; **Fast mode** speeds everything up.
- **Rewind** (F8) with configurable speed and animation.
- **Incremental syntax highlighting** for multiple languages, optimized to reprocess only the “tail” of the text while you type.
- **Typing audio** (WebAudio): mute/unmute (F4), master volume, and custom sound upload.
- **Themes & background**: ready‑made presets, text tint, *scanlines* and *vignette* toggles.
- **Cursor** styles (bar, underscore, vintage, box, etc.) with optional blink and scaling with the font size.
- **Fonts**: built‑in selector (JetBrains Mono, Ubuntu Mono, etc.) + display set via Google Fonts (Orbitron, Pixelify Sans, Bungee, Audiowide, Iceland, Megrim, Syncopate).
- **Clean/Cinematic mode (F9)**: hides the UI, takes the preview fullscreen; optional *PC stats* overlay (F10).
- **Dynamic source**: internal editor, *Copy all*, *Generate random*, or load a local file (many extensions supported).

---

## Quick demo

1. **Clone or download** the repo.  
2. **Open** `index.html` in your browser (recent Chrome/Edge/Firefox recommended).  
3. **Type**: you’ll see text, cursor animation, and sound. Try **F9** for *Clean mode* and **F10** for *PC stats*.

> Note: browsers require user interaction before playing audio (click/keypress).

---

## Hotkeys / Controls

- **F2** — Auto‑type on/off  
- **F4** — Mute / Unmute  
- **F6** — *Generate random* on/off (disabled when a file is loaded)  
- **F7** — Fast typing on/off  
- **F8** — Rewind (animated reset)  
- **F9** — Clean mode (fullscreen coding)  
- **F10** — PC stats (Clean mode only)  
- **Backspace/Delete** — remove one char  
- **Esc** — clear the screen or exit Clean mode  

While typing: **Space** temporarily triples the active *chunk*. The “Chunk per key” and “Burst delay” sliders tune the micro‑typing.

---

## Panels & settings

**Source / Mode**  
Load files (`.js, .py, .java, .html, .css, .ts, .cpp, .go, .rs, .kt, .asm, …`) or type in the textarea. Pick a *Language* to load built‑in examples and enable highlighting. *Copy all* copies the current output.

**Typing**  
*Chunk per key*, *Burst delay*, *Rewind speed*, *Rewind animation* on/off.

**Audio Settings**  
*Sound On/Mute*, *Volume*, *Upload custom sound*, *Reset Audio*.

**Aspect**  
*Themes* (presets), *Text color* (optional monochrome), *Background* with *Scanlines* and *Vignette* toggles.

**Cursor Style**  
Variants (Default, Vintage, Bar, Underscore, Double, Empty Box) + *Blink*. The cursor inherits the text color and scales with the active font.

**Clean / Cinematic**  
Hides the control panels, requests fullscreen on the *Preview* pane, and preserves typing focus. *PC stats* can be toggled with **F10**.

---

## How it works (short version)

The engine keeps a pointer `ptr` into `rawText` and, on each input, advances by a configurable *chunk*. In *fast mode* the chunk is larger; pressing **Space** multiplies it. A timed “burst” simulates rapid micro‑strokes until the chunk is exhausted.  
Rendering is incremental: it reprocesses only the tail of the DOM starting from a safe boundary to avoid artifacts, and re‑anchors the caret with an invisible sentinel to keep auto‑scroll at the bottom.

---

## Run locally & hosting

- **Open the file**: double‑click `index.html`.
- **Static server (optional)**:
  ```bash
  # Python 3
  python -m http.server 8080
  # then open http://localhost:8080/index.html
  ```
- **GitHub Pages (optional)**:
  - Keep `index.html` or rename it to `index.html` for a cleaner URL.
  - In **Settings → Pages**, set *Deploy from a branch* → `main` / root.
  - You’ll get either:
    - `https://USERNAME.github.io/REPO/` (if you use `index.html`), or
    - `https://USERNAME.github.io/REPO/index.html`.

*Tip*: add a blank `.nojekyll` file at the repo root if you use folders/filenames with `_` and want to bypass Jekyll processing (not required, but harmless).

---

## Quick customization

- **Colors & style**: many options are exposed as CSS variables in `:root` (e.g., `--bg`, `--panel`, `--text`, `--accent`, `--mono`).  
- **Fonts**: display fonts (Orbitron, Pixelify Sans, Bungee, Audiowide, Iceland, Megrim, Syncopate) are loaded via Google Fonts; the selector offers both mono and display options.  
- **New themes**: add a case in the “Theme presets” handler and define your background (gradients/patterns).  
- **Languages & examples**: extend the `examples` object in the code with your snippets and modes.  
- **Footer tip** (clickable label without underline/blue):  
  ```html
  <span>© 2025 <a href="https://github.com/T0ls/typerScene---Cinematic" style="text-decoration:none;color:inherit">T0ls — TyperScene</a>. CC‑BY‑4.0.</span>
  ```

---

## FAQ / Notes

- **Autoplay**: audio starts after a user gesture (browser policy).  
- **Performance**: very long texts are still handled client‑side; rendering is incremental, but large DOMs can grow heavy.  
- **Compatibility**: tested on recent Chrome, Edge, and Firefox. Safari is supported, though some APIs may behave differently.

---

## Contributing

Bug reports and ideas are welcome via **Issues**. PRs are appreciated — focused, small PRs are easier to review.

---

## License

Released under **CC‑BY‑4.0**. See the `LICENSE` file or <https://creativecommons.org/licenses/by/4.0/>.

---

## Credits

**Author**: T0ls — TyperScene  
**Fonts**: Google Fonts (Orbitron, Pixelify Sans, Bungee, Audiowide, Iceland, Megrim, Syncopate; JetBrains Mono, etc.).

---

### Screenshot / GIF

_Add a screenshot or GIF of the Clean/Cinematic mode and the control panels (recommended for the repo)._
