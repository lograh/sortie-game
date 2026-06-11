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

## Known issues / brainstorm

- **Combined thrust + turn touch control feels weird.** On a single virtual stick, turning and thrusting are coupled — you can't gently steer while coasting, and you can't thrust straight without committing to a heading from the stick angle. Some directions to consider:
  - Split into two zones: left half = turn-only (rotate to where you drag), right side already has fire/boost — could add a dedicated thrust button.
  - Tilt-to-steer (DeviceOrientation) for turn, on-screen button for thrust.
  - Tap-to-aim: tap anywhere in the play area to set a target heading; hold to thrust toward it.
  - "Lunar Lander" style: separate small thrust pedal + rotate buttons (less elegant but unambiguous).
  - Keep the joystick but decouple magnitude: any deflection = full thrust, angle = turn target (so light touches still steer hard).

## License

[MIT](LICENSE).
