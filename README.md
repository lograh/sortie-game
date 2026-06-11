# Sortie

A browser-based asteroids-style space game. Single HTML file — no build step, no install.

**Play it:** open `index.html` in any modern browser, or visit the [hosted version](https://lograh.github.io/sortie-game/).

Works on desktop, phones, and iPads.

## Controls

**Desktop / keyboard**
- Thrust / steer — arrow keys or WASD
- Fire — space
- (other bindings shown in the in-game lobby)

**Touch (iPad / phone)**
- On-screen controls render automatically on touch devices.
- Add to Home Screen for a fullscreen, app-like experience.

## Running locally

Just open `index.html`. If your browser blocks some features over `file://`, serve the folder:

```powershell
# any of these will work from the project folder
python -m http.server 8000
# or
npx serve .
```

Then visit http://localhost:8000.

## Hosting on GitHub Pages

1. Push this repo to GitHub.
2. Repo **Settings → Pages → Source: Deploy from branch → `main` / `/ (root)`**.
3. After a minute the game is live at `https://<your-user>.github.io/sortie-game/`.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The entire game (HTML + CSS + JS, WebGL2 renderer). |
| `icon.svg` | App icon — the in-game ship on a black background. |
| `manifest.webmanifest` | PWA manifest so iPad/phone "Add to Home Screen" launches fullscreen. |
| `LICENSE` | MIT. |

### Optional: apple-touch-icon

iOS Safari prefers a PNG for the home-screen icon. To generate one from `icon.svg`:

```powershell
# with ImageMagick installed
magick icon.svg -resize 180x180 apple-touch-icon.png
```

Drop the resulting `apple-touch-icon.png` next to `index.html` and iOS will pick it up automatically (the `<link>` tag is already in the head).

## Touch controls

The left thumb summons a floating joystick wherever you first touch — the origin is your initial touch point, so you never lurch on contact. Stick behavior is two-band:

- Small deflection (just past the dead zone): **turn only.** Hold the stick lightly off-center to rotate toward that heading without thrusting.
- Pull past about half travel: **thrust ramps in.** Just past the line ≈ 10% thrust; full deflection = full thrust. Lets you cruise at low power if you stop pulling at the right point.

Right side has Fire and Boost buttons.

### Future touch ideas

If the dead-zone single-stick still doesn't feel right, alternatives worth trying:
- Turn-only stick on the left + dedicated thrust button on the right.
- Tap-to-aim: tap a spot in the play area to set a target heading; hold to thrust toward it.
- Decouple turn rate from stick magnitude entirely (any deflection = max turn rate toward heading).

## License

[MIT](LICENSE).
