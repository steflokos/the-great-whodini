# 🎩 The Great Whodini

*Pick a secret. Crack theirs.*

A guessing game for two, in the spirit of the classic board game. You each secretly pick a character, then take turns asking yes/no questions until one of you works out who the other is hiding.

It runs entirely in the browser. There's no account to make and no server to set up, and the whole game is a single HTML file.

## How to play

1. One of you clicks **Create a room** and sends the room code (or invite link) to the other.
2. The other person pastes the code under **Join a game**.
3. You each pick a character and lock it in.
4. Take turns asking yes/no questions in the chat. Tap characters to flip them down as you rule them out.
5. When you think you know, hit **Final guess**. Get it right and you win the round. Get it wrong and your opponent does.

After a round you can look back over the board and keep chatting, or start another one. The score carries over, and you take turns going first.

## Running it

Open `index.html` in a recent browser and you're set.

If you'd like invite links, or you don't want to send the file around, put it on any static host (GitHub Pages and Netlify both work). Opened straight from your computer, you'll share the room code instead. You both need to be on the same version of the file.

## Your own characters

Click **Cast** at the top to change who's on the board. You can rename characters, pick a color and emoji, or give them a photo or a GIF. Friends, family and pets all work well.

- **Uploaded GIFs** keep moving if they're under about 200 KB. Anything bigger is saved as a still image, and the game tells you when that happens.
- **Linked GIFs** have no size limit. Paste a link to the image (Giphy page links work as they are), and your opponent gets asked before it loads.
- You can export your cast to a file and import it later, and whoever hosts decides which cast you both play with.

## How it works

You and your opponent connect directly to each other using WebRTC, through [PeerJS](https://peerjs.com). The free PeerJS server only introduces your two browsers. Your chat and game moves never go through it.

Your secret pick is locked in as a hash when you choose it and revealed at the end, so nobody can change their mind and nobody can fake a result.

## If it won't connect

Strict firewalls and VPNs are the usual cause. Try a different network first (a phone hotspot works well). If that doesn't help, two settings near the top of the script can:

- `PEER_SERVER` points the game at your own PeerJS server instead of the free one. Add its address to `connect-src` in the page's Content-Security-Policy too.
- `CUSTOM_ICE_SERVERS` lets you add a TURN relay for networks that block direct connections.
