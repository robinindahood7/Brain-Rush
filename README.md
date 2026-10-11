# Brain Rush

Brain Rush is a single-file HTML/CSS/JavaScript party and board-game collection that runs on GitHub Pages.

## Play online

Open <https://robinindahood7.github.io/Brain-Rush/>.

1. The host chooses **Host** for the TV/phones party games, or **Boards → Online with friends** for a board/card game.
2. Share the QR code or invite link.
3. Friends open the link, enter a display name, and join without an account.
4. Start when 2–10 people are present. Individual board/card games may have smaller limits dictated by their rules.

Players reconnect automatically after refreshing the page. New rooms use six-letter private room codes; older four-letter invite links remain compatible.

## Multiplayer architecture

The GitHub Pages build uses PeerJS/WebRTC with a host-authoritative star topology. The host owns the canonical game state and players send only their actions. WebRTC provides encrypted transport; games with hidden hands additionally encrypt each player's private state in the browser with ECDH P-256 and AES-GCM.

There are no API keys, passwords, or server secrets in this repository. The current setup uses the public PeerJS signaling service and is intended for private games with friends and lightweight testing. Keep the host tab open during a game.

## Deployment

GitHub Pages should publish the `main` branch from the repository root. `index.html` is the Pages entry point and forwards to the existing self-contained `index_1.html` while preserving invite links.

After pushing to `main`, allow GitHub Pages a minute or two to publish, then verify the root URL and test with two separate browsers or devices.
