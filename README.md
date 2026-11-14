# I Giochi di Pietro 🎮

Browser games designed by Pietro (4 years old).

Play them at https://pietro.coorasse.com or open `index.html` in a browser and pick a game.

## Games

- **Alieni** 👽🚀 (`alieni/`): shoot the big aliens: each one splits into two small aliens, which you vacuum up.
  Watch out, aliens sometimes turn invisible. Defeat all of them to win a trophy 🏆.
- **Uni** 🦄 (`uni/`): a city at night, where monsters sit on the roofs and jump on you when you get close.
  Every time one lands on you, a heart flies away ❤️. The child follows the mouse, and a click shoots the magic
  torch 🔦. Defeat all the monsters to win a trophy 🏆.
- **Scoppia** 🎈📌 (`scoppia/`): an arena with a crowd, where a little man holding two pins pokes a standing
  inflatable until it explodes. Tap the inflatable and he runs to it and pokes it; tap again (or hold) to keep
  poking. Watch out, the inflatable sometimes disappears and pops up somewhere else. Pop all three to win a trophy 🏆.

## Adding a new game

1. Create a folder named after the game with an `index.html` inside (e.g. `razzi/index.html`).
2. Add a `<a id="home" href="../">🏠</a>` link so Pietro can go back to the menu.
3. Add a tile for it in the root `index.html`.
4. Add a `COPY` line for its folder in the `Dockerfile`.

## Static only

The games are plain HTML and JavaScript: no backend, no external scripts, no network requests.
They are served by an unprivileged nginx (`nginx.conf`) that only answers `GET`/`HEAD` and sends a
Content-Security-Policy with `connect-src 'none'`, so the pages cannot talk to any server.
On Dokku the container runs read-only, without Linux capabilities and with a memory limit.
Games must stay self-contained: everything inline in their `index.html`.
