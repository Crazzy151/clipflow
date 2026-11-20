# ClipFlow backend

This directory will contain the ClipFlow API, background workers, Twitch integration, transcription pipeline, FFmpeg rendering pipeline, and publishing integrations.

## Planned modules

- `app/` — FastAPI application
- `app/api/` — HTTP routes
- `app/services/` — Twitch, Kick, transcription, rendering, and publishing services
- `app/models/` — database models
- `app/workers/` — background processing jobs
- `tests/` — unit and integration tests

## Environment variables

Never commit real secrets. Use `.env.example` as a template.

```env
DATABASE_URL=
TWITCH_CLIENT_ID=
TWITCH_CLIENT_SECRET=
TWITCH_REDIRECT_URI=
YOUTUBE_CLIENT_ID=
YOUTUBE_CLIENT_SECRET=
YOUTUBE_REDIRECT_URI=
SECRET_KEY=
```
