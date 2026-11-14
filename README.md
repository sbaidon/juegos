# Juegos

Little web games to play with friends. Plain HTML, CSS and JavaScript. No build step, no backend.

## Games

- `madrazos/` Madrazos Patrios. Online platform fighter for 2 to 4 players with historical Mexican figures. Each player's live webcam becomes the face of their fighter.
- `chilango/` ¿Quién es el Chilango? In-person bluffing game for 3 to 12 players on one shared phone.

## Hosting

Live at https://sbaidon.github.io/juegos/

GitHub Pages serves the `gh-pages` branch. Every push to `main` is copied onto it by `.github/workflows/deploy.yml`, so only ever edit `main`. `index.html` at the root is the landing page.

## How Madrazos goes online

- One player hosts a room and gets a 4 letter code. The others join with the code or the link.
- Players connect directly to the host with WebRTC through PeerJS (`madrazos/peerjs.min.js`, MIT license, see `madrazos/peerjs.LICENSE`). The free public PeerJS server is only used to introduce the players to each other.
- The host runs the game. Guests send their button presses and get the game state back 60 times a second.
- Webcam frames are sent small and at a low frame rate through the same connection. No video or audio is stored anywhere.

## Run it locally

```
python3 -m http.server 8000
```

Then open http://localhost:8000. The camera only works on `localhost` or over HTTPS.
