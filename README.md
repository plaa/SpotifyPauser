# Spotify Pauser

Spotify Pauser allows you to pause a Spotify playlist for a desired amount of time between songs. Useful for example for dance playlists. You need a Spotify Premium account to use the app.

Live app: https://plaa.github.io/SpotifyPauser/

**Important:** Follow the instructions below to create your own Spotify Client ID to use this app. Spotify restricts publishing apps broadly, so you must create an app in your own Spotify Developer account and add your Spotify user as a test user. You can add 25 test users to one app.

## Quick start (hosted app)

Creating a Spotify Client ID:

1. Log in to Spotify Developer account at https://developer.spotify.com/
2. Go to Dashboard and Create a new app. Provide a name and description and add a Redirect URI with the value `https://plaa.github.io/SpotifyPauser/`.
3. Go to User Management and add your Spotify account email as a Test User and save.
4. Go to https://plaa.github.io/SpotifyPauser/
5. Enter your Client ID and click “Connect to Spotify” and allow.

## Self‑hosting

You can host `index.html` anywhere, including serving it locally. Run `npm install` and `npm run serve` to host it locally at http://127.0.0.1:8888/. Set the Redirect URI in your Spotify app to the exact URL where `index.html` is served (in case of localhost use `http://127.0.0.1:8888/`).

## Privacy

- Runs entirely in your browser; no data is sent to any server other than Spotify.
- Tokens and settings are stored locally and cleared when you sign out.

## Credits & License

Copyright Sampo Juustila. Made using ChatGPT / Codex. Licensed under the MIT License.
