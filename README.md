# Ultimative Chat

Ultimative Chat is a Python application for real-time monitoring of TikTok livestreams. It displays chat messages, gifts, viewer entries, likes, and viewer avatars in a split-panel interface.

## Features

- **Chat messages** — real-time viewer comments
- **Gifts** — gift name, diamonds, and repeat count
- **Viewer entries** — notifications when users join the stream
- **Likes** — like counts and totals
- **Viewer avatars** — automatically loaded and cached
- **Badges** — Moderator, Fan Club (with name and level), and Subscriber badges next to usernames
- **Subscriber database** — subscribers are saved to a local SQLite database (`subscribers.db`) so they're recognized on future visits even if TikTok doesn't send their badge again
- **TTS (text-to-speech)** — voice chat readout via edge-tts with customizable voice, speed, and permissions (subscribers, moderators, fan club, or all)
- **Split panels** — left column for likes/joins, right column for chat/donations/subscriptions
- **Statistics** — counters for chat, gifts, likes, joins, and follows
- **Copy text** — context menu to copy any message
- **Settings saved** — all settings stored in `.env` and restored on restart

## Installation

1. Install Python 3.10+
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Copy `.env.example` to `.env` and edit it:
   ```bash
   cp .env.example .env
   ```
4. Edit `.env` and set `TIKTOK_USERNAME` to the streamer's TikTok username (without @)
5. Run:
   ```bash
   python main.py
   ```

Or use `запуск.bat` on Windows.

## Configuration (.env)

| Setting | Description | Default |
|---------|-------------|---------|
| `TIKTOK_USERNAME` | Streamer TikTok username (without @) | `streamer_username` |
| `LOG_TO_FILE` | Save log to file (1 = yes, 0 = no) | `0` |
| `UI_POLL_INTERVAL` | Queue poll interval (ms) | `100` |
| `MAX_EVENT_LINES` | Max rows in feed | `300` |
| `TTS_ENABLED` | Enable chat TTS (1 = yes, 0 = no) | `0` |
| `TTS_VOICE` | TTS voice | `ru-RU-SvetlanaNeural` |
| `TTS_RATE` | Speech rate (-50 to +50) | `0` |
| `TTS_SUBSCRIBERS` | Speak subscribers (1/0) | `1` |
| `TTS_MODERATORS` | Speak moderators (1/0) | `1` |
| `TTS_FANCLUB` | Speak fan club members (1/0) | `1` |
| `TTS_SPEAK_ALL` | Speak all messages regardless of status (1/0) | `0` |

## Dependencies

| Package | Version | License | Purpose |
|---------|---------|---------|---------|
| TikTokLive | >=7.0.0 | Modified AGPL-3.0 | Connect to TikTok LIVE via WebSocket |
| Pillow | >=10.0.0 | MIT-CMU | Image processing (avatars, gifts) |
| python-dotenv | >=1.0.0 | BSD-3-Clause | Read/write `.env` config |
| PyQt6 | >=6.5.0 | GPL-3.0 | GUI interface |
| edge-tts | >=7.3.0 | LGPLv3 | Text-to-speech |
| playsound | ==1.2.2 | MIT | Play MP3 audio |

## Important Notice

This is an unofficial application (reverse-engineered TikTok Webcast protocol). TikTok does not provide an official public API for live streams. TikTokLive is distributed under a **Modified AGPL-3.0** license, and PyQt6 under **GPL v3**. If you plan to distribute this project commercially, review the license terms of all dependencies.
