# Wavyzon

## From their [GitLab](https://gitlab.com/ihrz/wavyzon)

Standalone audio node for Discord bots, written in Rust. It joins voice channels, streams and mixes music, and reports exactly when each frame reached Discord (the "wire clock"). It speaks the Lavalink v4 protocol, so existing Lavalink clients work unchanged, and has its own `/v1` API for two-deck mixing, crossfades and audio analysis. DAVE end-to-end encryption is implemented in Rust, so no native library is needed at runtime.

## Server Ports

| Port    | Default | Description |
|---------|---------|-------------|
| Wavyzon | 2333    | REST + WebSocket API (Lavalink v4 and `/v1`), assign as primary |

Voice traffic to Discord is outbound UDP only: no extra port is needed.

## Installation

The install builds Wavyzon from source (`WAVYZON_REF`, default `main`) in the stock Debian installer image, with a minimal Rust toolchain from rustup and CMake for the bundled libopus. The toolchain and build files are removed afterwards; only the `wavyzon` binary stays.

* A release build takes a few minutes and needs about **1.5 GB of RAM per build job**. `Build jobs` (default 2) limits parallelism; lower it if the install is killed for lack of memory.
* To update, change `Branch or tag` if needed and **reinstall** the server. The data directory, audio cache and state file are kept.

## First start

Set `Password` (8+ characters, `youshallnotpass` is refused) before starting: clients send it in the `Authorization` header, as with Lavalink. Point your bot at `host:port` with that password.

The server is marked as started on the `wavyzon listening` log line. Stopping sends `^C`, which saves the sessions to the state file so they resume after a restart.

## Notes

* Every setting is a panel variable and maps 1:1 to the variables documented in the [configuration reference](https://gitlab.com/ihrz/wavyzon/-/blob/main/docs/src/configuration.md).
* Spotify and Apple Music are metadata only: their tracks are matched by ISRC or title to the playback sources.
* `HTTP: private addresses` stays `false` unless every client of the node is trusted.
* Lyrics come from Genius first, then lyrics.ovh when Genius has none. Set `Genius access token` (a Client Access Token from [genius.com/api-clients](https://genius.com/api-clients)) for reliable Genius searches; without it Genius often refuses servers and lyrics.ovh answers.
