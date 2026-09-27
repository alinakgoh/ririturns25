# 25 for 25

Riazul's birthday site: a click-through intro (with a back arrow and a
skip button), a wall of 25 friend polaroids, a surprise bonus section of 5
family polaroids further down, and a popup for each person with their
memory, a song, and a voice note.

It's a single static HTML file. No build step, no server, no dependencies
to install.

## Files

```
index.html      the whole site
photos/         two photos per person — see "Photos" below
voice/          one voice note per person (optional) — see "Voice notes"
```

## Editing the content

Open `index.html` in any text editor (or GitHub's own web editor) and look
for the block marked:

```
✏️ YOUR CONTENT GOES HERE
```

- **`BIRTHDAY_NAME`** — the birthday person's name. The hero subtext
  ("happy birthday ___!") is built from this automatically.
- **`FRIENDS`** — one `{ name, memory, song, trackNote, voice }` entry per polaroid in
  the main 25-person wall.
- **`FAMILY`** — same format, for the 5 bonus polaroids that appear in the
  surprise section further down the page.

For each entry:
  - `name` — the person's name. This is what everything else connects to —
    see Photos and Voice notes below.
  - `memory` — their memory, as plain text.
  - `song` — a Spotify or YouTube link, or `""` if none.
  - `trackNote` — an optional short note that appears between "a meaningful
    track:" and the song. Leave it out or set it to `""` to show only the
    heading and song.
  - `voice` — leave this as `""`. It's found automatically (see Voice
    notes). Only fill it in if you want to link an external audio URL for
    that one person instead of uploading a file.

There's a second editable block further down marked
`✏️ EDIT THE OPENING SEQUENCE HERE` — that's the intro slideshow text, one
line per screen. People can step through it with taps, the back arrow, or
the "skip to end" button in the corner.

### Photos — two per person

Each polaroid uses **two** photos, both built automatically from `name` —
you never write a filename directly. For someone named `"Priya"`:

```
photos/Priya1.jpg   →  FRONT photo — fills the whole polaroid in the wall
photos/Priya2.jpg   →  BACK photo — shown centered, just below her name,
                        when the polaroid is tapped open
```

Put both browser-compatible images in a folder called `photos` next to
`index.html`, named **exactly** like the matching `name` field plus `1` or
`2` — same spelling, same capital letters. Capitalization matters once this
is live on GitHub Pages, even if it doesn't matter on your own computer.
`.jpeg`, `.png`, and `.webp` all work too, not just `.jpg`. Export HEIC
photos as JPEG before uploading: renaming a `.heic` file to `.jpeg` does not
convert it and browsers will not display it.

- Missing **front** photo → that polaroid shows a soft placeholder with
  the person's initial instead of a broken image.
- Missing **back** photo → that part of the popup just doesn't appear.
  It's a bonus, not a requirement — totally fine to only have one photo
  for someone.

### Voice notes

Same idea as photos, but **all lowercase**. For `"Priya"`, the page
automatically looks for:

```
voice/priya.mp3
```

It also tries `.m4a`, `.wav`, and `.ogg`, so whatever format your
recordings are already in should just work. Put the files in a folder
called `voice` next to `index.html`, named in lowercase after each
person's `name`.

If someone doesn't have a voice note, just don't add a file for them —
nothing breaks, the audio player simply won't appear for that polaroid.
No Google Drive links or URL conversion needed.

## Putting it on GitHub Pages

1. Create a repo and upload `index.html`, the `photos` folder, and the
   `voice` folder to it (keep them all at the same level — don't nest
   `index.html` inside another folder).
2. Go to **Settings → Pages**.
3. Under "Build and deployment," set the source to deploy from a branch,
   pick `main` (or whichever branch you uploaded to) and the `/ (root)`
   folder.
4. Save. GitHub will give you a URL that looks like:
   ```
   https://yourusername.github.io/reponame/
   ```
   That's the link to send.

Changes usually go live within a minute or two of pushing — refresh if it
looks stale.
