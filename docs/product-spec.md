# ClipFlow Product Specification

## Overview

ClipFlow is a creator automation product for the United States market. It converts Twitch and Kick clips into vertical short videos with accurate English captions and publishes approved clips to YouTube Shorts.

## Primary market

United States.

## Primary language

English.

## Secondary language

Spanish.

## Target user

A Twitch or Kick streamer who wants to repurpose short highlights into TikTok, YouTube Shorts, and Instagram Reels without manually editing videos or writing captions.

## Core value proposition

Turn a short Twitch or Kick clip into a ready-to-post 9:16 video with burned-in English captions in minutes.

## Core user flow

1. The creator connects a Twitch account.
2. ClipFlow detects new Twitch clips automatically.
3. For Kick, the creator pastes a Kick clip URL.
4. ClipFlow downloads only the selected short clip.
5. It transcribes the speech and creates English captions.
6. It renders a 9:16 MP4 with burned-in captions.
7. The creator reviews and approves the final video on mobile.
8. ClipFlow uploads the approved video to YouTube Shorts.
9. ClipFlow prevents duplicate publishing using the source platform and clip ID.

## MVP scope

- Twitch OAuth connection
- New Twitch clip detection
- Kick clip URL ingestion
- Platform detection
- Clip download
- Audio extraction
- English transcription
- Caption generation
- 9:16 rendering
- Mobile review and approval
- YouTube Shorts upload
- Duplicate prevention
- Error handling and retry logic

## Out of scope for MVP

- Automatic Kick clip detection
- TikTok publishing
- Instagram Reels publishing
- Spanish captions
- Spanish UI
- Team accounts
- Advanced video editing
- Analytics dashboards
- Scheduling

## Success metric

A creator can connect Twitch, create a clip, approve the generated 9:16 captioned video on mobile, and have it automatically uploaded to YouTube Shorts without duplicate publishing.
