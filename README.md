# Dubz Final

Clean video-only dubbing pipeline. No YouTube, no yt-dlp, no WARP, no lip-sync.

## How it works
1. Drop **video files** into the Drive inbox folder.
2. GitHub -> **Actions** tab -> **Dubz Final** -> **Run workflow**.
3. Every video is dubbed in parallel (max matrix fan-out) via the dubbing engine.
4. Dubbed files land in **Dubz/DubDone**. Originals move to `<inbox>/archive`.

## Folders
- Inbox: set per account (Dubz/DubInbox or Dubz/DubInbox2)
- Output: Dubz/DubDone (universal)

## Settings (Run workflow form)
- `src`, `target`: Languages (default: Hindi -> English)
- `genre`: Content type (default: monologue)
- `speakers`: Number of speakers
- `chunk`: Length of each piece (default: 300s, lower for faster/parallel)
- `workers`: Number of parallel jobs (default: all)
- `tries`: Number of retries per chunk (default: 6)

## Improvements in this version
- **Health Check**: Verifies API access before starting.
- **Browser Mimicry**: Reduced risk of bot detection.
- **Better Error Handling**: Detailed reporting and intelligent retries.
- **Robust Resume**: Seamlessly continue interrupted jobs.

## Secret required
- `RCLONE_CONF` - your rclone config (Google Drive remote named `gdrive`).

## ⚠️ Important Note
This project uses an unauthenticated internal API. It can break at any time if the provider adds security. See [FRAGILITY_NOTE.md](./FRAGILITY_NOTE.md) for more details.

No cron. Manual run only.
