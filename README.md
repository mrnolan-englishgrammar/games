# games

Interactive English grammar games for ELL students.

## Game gallery (hover-preview page for Google Sites)

`gallery/index.html` is a self-contained hover-preview gallery, matching the
"thumbnail → short preview clip on hover → click to play" pattern used by
sites like CrazyGames. It's plain HTML/CSS/JS with no build step.

### Why this exists

Google Sites' built-in grid/gallery blocks (image + title + text) can't run
custom JavaScript, so they can't do hover-video previews. The only way to get
that behavior on Sites is to build the whole gallery as one HTML page and
drop it in via **Insert → Embed → Embed code** (Sites runs it in a sandboxed
iframe, where your own CSS/JS is allowed).

### 1. Add your assets

- `gallery/assets/thumbnails/` – one static image per game (jpg/png/webp).
- `gallery/assets/previews/` – optional 3–6s muted looping clip per game
  (mp4 or webm, no audio needed, keep each under ~1–2MB for fast hover start).
  Skip this and the card just gets a subtle hover/zoom effect instead.
- `gallery/assets/games/<game>/index.html` – your existing playable HTML
  games (or link out to wherever they're already hosted).

### 2. Edit the game list

Open `gallery/index.html` and edit the `GAMES` array near the top of the
`<script>` block — one object per game with `title`, `description`,
`thumbnail`, `preview` (optional), and `url`.

### 3. Host it

Pick one:

- **Paste directly into Sites:** Insert → Embed → Embed code, paste the
  full contents of `gallery/index.html`. Simplest, but thumbnails/previews
  must be public URLs (upload the images to a Sites image block to get a
  URL, or use Drive/Imgur/etc.) since Embed Code can't carry side files.
- **GitHub Pages (recommended once you have more than a few games):**
  enable Pages for this repo (Settings → Pages → serve from a branch),
  then in Sites use Insert → Embed → **By URL** and point it at
  `https://<user>.github.io/<repo>/gallery/`. Keep everything —
  thumbnails, previews, and the games themselves — in this repo so one
  push updates the whole gallery.

### 4. Mobile behavior

There's no "hover" on touch screens, so on phones/tablets the preview clip
plays on tap and a second tap (or the existing click handler) opens the
game in the inline lightbox. No extra setup needed — it's handled by the
same click/tap event.
