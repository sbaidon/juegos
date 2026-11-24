# Juegos

Little web games to play with friends. Plain HTML, CSS and JavaScript. No build step, no backend.

## Games

- `madrazos/` Madrazos Patrios. Online platform fighter for 2 to 4 players with historical Mexican figures. Each player's live webcam becomes the face of their fighter.
- `labola/` La Bola. Hex map building and trading game set in the Mexican Revolution, for 2 to 6 players on one device, with optional computer players. Each player gets a character portrait for their oficio, and the board has small animations (the Cacique walks between tiles, resources pop out when the dice hit, ranchos smoke). Round events, a moving Cacique, and three optional expansions: El Tren (desert, train tracks, the Capital and a hidden map edge), Los Corridos (songs you trade for favors) and Generales y Dorados (town goods, town upgrades, Dorados and the federal army). Add `?bots=4&rapido&lago&pesca&senorios` to the URL to watch computer players play a fast game. The old `altepetl/` link redirects here.
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
