# ClipFlow

ClipFlow turns Twitch and Kick clips into vertical, captioned short videos and automatically publishes them to TikTok, YouTube Shorts, and Instagram Reels.

Primary market: United States.
Primary language: English.
Secondary language: Spanish.

Twitch is the primary automated source: ClipFlow detects and processes new Twitch clips automatically.
Kick is supported as a manual clip-input source: the creator pastes a Kick clip URL for processing.

## Product goal

Automatically convert Twitch and Kick clips into ready-to-post 9:16 videos with accurate captions, then publish them to selected social platforms.

## Core flow

1. Creator creates a Twitch or Kick clip.
2. For Twitch, ClipFlow automatically detects new clips by Clip ID.
3. For Kick, the creator pastes the Kick clip URL into ClipFlow.
4. ClipFlow identifies the platform and downloads only the selected short clip.
5. It transcribes the speech and creates English captions.
6. It renders a vertical 9:16 MP4 with burned-in captions using FFmpeg.
7. The creator reviews and approves the final clip on mobile.
8. ClipFlow uploads the approved clip to YouTube Shorts.
9. It prevents duplicate publishing using a platform-specific unique clip ID.
10. Spanish captions and Spanish UI are added in a later phase.

## MVP scope

- Twitch OAuth connection
- Detection of new Twitch clips
- Kick clip URL input
- Kick clip download or capture workflow
- Kick clip metadata extraction
- Platform detection: Twitch or Kick
- Clip download
- Audio extraction
- English transcription
- Caption generation
- 9:16 rendering
- Mobile review and approval
- YouTube Shorts upload
- Duplicate prevention
- Error handling and retry logic

## Recommended stack

| Layer | Recommendation |
|---|---|
| Mobile | PWA first, Android app later |
| Backend | Railway, Render, Fly.io, or VPS |
| Database | PostgreSQL or Supabase |
| Twitch | Twitch Helix API + OAuth |
| Kick | Kick clip URL ingestion; official Kick API for account connection where applicable |
| Transcription | faster-whisper or WhisperX |
| Video | FFmpeg |
| YouTube | YouTube Data API videos.insert |
| TikTok | TikTok Content Posting API, later phase |
| Secrets | Environment variables or secret manager |

## Security rules

- Never store API keys or OAuth tokens in source code.
- Use environment variables or a secret manager.
- Store only the minimum necessary Twitch scopes.
- Encrypt refresh tokens at rest.
- Use a composite unique key of source_platform and source_clip_id to prevent duplicate publishing.
- Log errors without exposing tokens or personal data.
- Do not rely on unofficial Kick scraping for the core product.

## Development roadmap

1. Create product specification and repository.
2. Build Twitch OAuth and clip detection.
3. Build clip download and audio extraction.
4. Add transcription and English captions.
5. Add FFmpeg 9:16 rendering with burned-in captions.
6. Build mobile review and approval screen.
7. Implement YouTube Shorts upload.
8. Add duplicate prevention and error handling.
9. Add Kick clip URL ingestion and processing.
10. Add TikTok publishing after API approval.
11. Add Spanish captions and Spanish UI.
12. Enable fully automatic publishing mode.

## First five tasks

1. Create GitHub repository and project structure.
2. Create ClipFlow product specification and database schema.
3. Implement Twitch OAuth connection.
4. Implement new-clip detection using Get Clips.
5. Build a basic clip-processing queue with status tracking.

## Success metric

A creator can connect Twitch, create a clip, approve the generated 9:16 captioned video on mobile, and have it automatically uploaded to YouTube Shorts without duplicate publishing. A creator can also paste a Kick clip URL and receive the same captioned, vertical, ready-to-publish output.
