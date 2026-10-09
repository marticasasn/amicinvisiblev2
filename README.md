# Amic Invisible

A tiny Secret Santa web app in plain HTML. Available in Catalan (`index.html`) and Spanish (`es.html`). "Amic invisible" means "secret friend".

<!-- TODO: add a screenshot or GIF here, e.g. ![Screenshot](docs/screenshot.png) -->

<!-- TODO: add live demo link here, e.g. **Live demo:** https://... -->

## How it works

1. The organizer opens the page and types one name per line.
2. The app draws a random assignment where nobody gets themselves.
3. It generates one personal link per participant, ready to copy and send over WhatsApp, Telegram, etc.
4. Each participant opens their link, presses a button and sees who they have to buy a gift for.

Everything runs in the browser. There is no backend, no database and no account. Nothing is saved anywhere: each result lives only inside its own link.

### What a link contains

A participant link looks like this:

```
index.html?n=Anna&r=THVpcw%3D%3D
```

- `n` is the participant's name.
- `r` is the name of the person they give a gift to, encoded in base64.

Each link carries only that person's result, never the full draw, so one participant cannot find out who the others got.

Two things to keep in mind:

- **Base64 is not encryption.** It only keeps the name from being readable at a glance. Anyone who decodes `r` sees that one result, which is the person the link was meant for anyway.
- **The organizer can see the whole draw.** All links are generated on the organizer's screen, so whoever runs the draw could decode every one of them. If the organizer also takes part, ask them not to peek.

## Features

- Random draw with no self-assignments
- One personal link per participant, containing only their own result
- Warns about duplicate names before drawing
- Copy-to-clipboard button for each link
- Result can be viewed again after closing it
- Catalan and Spanish versions, with a language switch
- Supports accents and non-ASCII names
- Mobile-friendly layout
- Zero dependencies

## Stack

Plain HTML, CSS and vanilla JavaScript. No build step, no frameworks.

## Usage

Open `index.html` (Catalan) or `es.html` (Spanish) in any modern browser, or serve the folder with any static host (GitHub Pages works out of the box).

To run it locally with a server:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

Links only work for other people if the page is hosted at a public URL.

## License

[MIT](LICENSE)
