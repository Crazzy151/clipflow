# ClipFlow API Plan

## Twitch

Use the Twitch Helix API for OAuth, clip discovery, clip metadata, and clip downloads.

Required endpoints:

- `GET /helix/clips?broadcaster_id={id}` — discover clips for a broadcaster
- `GET /helix/clips?id={id}` — fetch a specific clip
- `GET /helix/clips/download` — obtain a download URL for a clip

Important fields:

- `id`
- `broadcaster_id`
- `created_at`
- `title`
- `thumbnail_url`
- `duration`
- `url`

## Kick

Kick is a manual clip-input source for the MVP.

The creator pastes a Kick clip URL. ClipFlow identifies the platform, extracts the clip ID, and processes only that selected clip.

Do not rely on unofficial Kick scraping for the core product. Use official Kick APIs where available and permitted.

## Transcription

Use faster-whisper or WhisperX to transcribe the clip audio.

Output:

- Full transcript
- Sentence-level captions
- Word-level timestamps where available

## Video rendering

Use FFmpeg to:

- Extract audio
- Render a 9:16 video
- Crop or reframe the source video
- Burn in captions
- Export MP4

## YouTube

Use the YouTube Data API `videos.insert` endpoint to upload approved MP4 files.

Required metadata:

- Title
- Description
- Tags
- Category
- Privacy status

## Duplicate prevention

Use a composite unique key:

```text
(source_platform, source_clip_id)
```

Before processing a clip, check whether the same source platform and clip ID already exists.

## Rate limits and risks

- Respect Twitch API rate limits and pagination.
- Handle token refresh and expired OAuth sessions.
- Retry failed downloads and uploads with backoff.
- Do not publish without user approval unless fully automatic mode is explicitly enabled.
- Verify current TikTok API approval and scope requirements before implementing publishing.
