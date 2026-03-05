# GeniusMusic Bot — A Telegram bot for searching and downloading music on demand.
[![DOI](https://zenodo.org/badge/1173921951.svg)](https://doi.org/10.5281/zenodo.18882714)

## Overview

I built this to give Telegram users a seamless way to find and download songs without
leaving the app. You type an artist or song name, get a ranked list of results, tap a
link, and receive the audio file, cover art, and full lyrics — all inside one chat
window. It removes the friction of jumping between apps just to grab a track.

## Tech Stack

- PHP 7.x
- Telegram Bot API (webhook-based)
- cURL for HTTP requests
- External music API (`/api2/search`, `/api2/mp3` endpoints)

## Project Structure

```
geniusmusic_bot/
├── geniusbot-noapi.php   # Core bot logic — handles all webhook events and API calls
├── codemeta.json         # Project metadata
└── LICENSE
```

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/Stayuptildawn/geniusmusic_bot.git
   cd geniusmusic_bot
   ```

2. Open `geniusbot-noapi.php` and set your credentials:
   ```php
   define('API_KEY', 'YOUR_TELEGRAM_BOT_TOKEN');
   $channelID = "@YourChannelUsername";
   ```

3. Replace the obfuscated music API URLs with your own endpoints that return:
   - **Search**: `{ mp3s: [{ id, title, downloads }] }`
   - **Track**: `{ title, link, photo, plays, lyric, likes, dislikes, downloads }`

4. Upload `geniusbot-noapi.php` to an HTTPS-enabled server.

5. Register the webhook:
   ```
   https://api.telegram.org/bot<YOUR_TOKEN>/setWebhook?url=https://yourdomain.com/geniusbot-noapi.php
   ```

6. Open your bot on Telegram, send `/start`, and search for any artist by name in English.

## Key Output

Each successful search returns up to 20 results. Selecting one delivers the MP3 file,
album artwork with play/download/like stats, and the full song lyrics — all as separate
Telegram messages in sequence.

## Author

**Mohammad Soleimani Roudi**
[GitHub](https://github.com/Stayuptildawn/geniusmusic_bot)
