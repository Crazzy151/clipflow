# ClipFlow Database Schema

## users

| Column | Type | Notes |
|---|---|---|
| id | UUID | Primary key |
| email | text | Unique |
| created_at | timestamptz | Not null |
| updated_at | timestamptz | Not null |

## connected_accounts

| Column | Type | Notes |
|---|---|---|
| id | UUID | Primary key |
| user_id | UUID | References users.id |
| platform | text | twitch, youtube, tiktok, instagram |
| external_account_id | text | Platform-specific account ID |
| display_name | text | Account display name |
| access_token_encrypted | text | Encrypted access token |
| refresh_token_encrypted | text | Encrypted refresh token |
| token_expires_at | timestamptz | Nullable |
| scopes | text[] | Granted scopes |
| created_at | timestamptz | Not null |
| updated_at | timestamptz | Not null |

## clips

| Column | Type | Notes |
|---|---|---|
| id | UUID | Primary key |
| user_id | UUID | References users.id |
| source_platform | text | twitch or kick |
| source_clip_id | text | Platform-specific clip ID |
| source_clip_url | text | Original clip URL |
| title | text | Clip title |
| thumbnail_url | text | Clip thumbnail URL |
| duration_seconds | integer | Clip duration |
| created_at | timestamptz | Source clip creation time |
| detected_at | timestamptz | When ClipFlow found the clip |
| status | text | detected, downloading, transcribing, rendering, awaiting_approval, approved, uploading, published, failed |
| error_message | text | Nullable |

Unique constraint:

```sql
UNIQUE (source_platform, source_clip_id)
```

## processed_clips

| Column | Type | Notes |
|---|---|---|
| id | UUID | Primary key |
| clip_id | UUID | References clips.id |
| transcript | text | Full transcript |
| captions_json | jsonb | Timed caption segments |
| rendered_video_url | text | Final 9:16 MP4 URL |
| approved_at | timestamptz | Nullable |
| created_at | timestamptz | Not null |

## publications

| Column | Type | Notes |
|---|---|---|
| id | UUID | Primary key |
| clip_id | UUID | References clips.id |
| platform | text | youtube, tiktok, instagram |
| external_post_id | text | Platform-specific post ID |
| external_post_url | text | Public post URL |
| status | text | pending, uploading, published, failed |
| error_message | text | Nullable |
| published_at | timestamptz | Nullable |
| created_at | timestamptz | Not null |
| updated_at | timestamptz | Not null |

Unique constraint:

```sql
UNIQUE (clip_id, platform)
```
