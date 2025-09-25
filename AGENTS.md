# Spotify Pauser — Agent Guide

This repository contains a single-page browser app that controls Spotify playback to insert configurable pauses between tracks. The code lives entirely in `index.html` (HTML + CSS + JS) and executes in the user's browser; there is no backend.

## Project Snapshot

- **Primary entry point:** `index.html`
- **Local dev server:** `npm install` then `npm run serve` (serves via `http-server` at `http://127.0.0.1:8888/`).
- **Assets:** `spotify.svg` for branding, no build pipeline.
- **Dependencies:** Only `http-server` for local hosting; runtime logic uses browser APIs and Spotify Web API.

## Spotify Auth & Usage

- Users must supply their own Spotify Client ID because Spotify limits app publishing.
- Redirect URI must match the hosting origin (update it in the Spotify Developer dashboard when self-hosting).
- App requests scopes: `user-read-playback-state`, `user-modify-playback-state`, `user-read-currently-playing`.
- Tokens and user preferences persist in `localStorage`; session data for PKCE exchange is stored in `sessionStorage`.

## Core Behavior

- Polls `/me/player` to track playback, schedules a pause near track end, then resumes after a user-defined delay.
- Fetches `/me/player/queue` to show the upcoming track during pauses.
- Handles edge cases like track changes happening before the scheduled pause and suppresses duplicate pauses when resuming a track tail.

## Development Notes

- JavaScript is embedded in `index.html`; keep edits ASCII and add comments sparingly (useful only for non-obvious logic).
- No automated tests; rely on manual testing by simulating end-of-track pauses and observing console logs/UI updates.
- When modifying polling or pause logic, ensure `schedulePauseIfNeeded`, `resumePlaybackNow`, and `pollOnce` stay in sync.

## Gotchas

- Spotify API responses may lag; code already tolerates brief stale states—maintain that resilience when editing.
- Avoid breaking the pause scheduling windows (typically within the last 15 s of a track and ~1 s before track end).
