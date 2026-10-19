# Channel 9 YouTube Cloud Automation â€” Kristin Marin

Fully cloud-based, autonomous YouTube upload pipeline and engagement system running entirely on GitHub Actions.

## System Configuration
- **Channel Name:** Kristin Marin
- **Channel ID:** `UCddVQFPVaoey0we1vXHEqvg`
- **Google Account:** `khanmuhammadarsalan911@gmail.com`
- **GitHub Username:** `khanmuhammadarsalan911-hash`
- **Repository:** `khanmuhammadarsalan911-hash/multipost9` (Private)
- **Drive Inbox Folder ID:** `1xbYGkaG8Cg8-IrYXFh4ooj6JYiZYvDAX` (453 inbox videos)
- **Drive Uploaded Folder ID:** `1E_NiUNd_1IsAGuIHJoB4XijalnTKEWgc`
- **Architecture:** Single-Token Architecture (`token.json` holds all 5 scopes)
- **Execution Mode:** Runs 100% on GitHub Actions runners with user PC turned off

## Automated Schedules (UTC & PKT)
1. **Daily Uploads:** 3 times daily
   - **Cron:** `20 3,9,15 * * *`
   - **Pakistan Time (PKT):** 08:20, 14:20, 20:20 PKT
   - **Action:** Fetches oldest unuploaded video from Google Drive, normalizes format, generates AI metadata via Gemini based on visual content, uploads to YouTube as Public Short, updates state, and moves video to `Uploaded/` folder.
2. **Comment Auto-Replies:** Once daily
   - **Cron:** `20 17 * * *`
   - **Pakistan Time (PKT):** 22:20 PKT
   - **Action:** Scans recent comments on channel videos, generates contextual positive responses via Gemini, posts replies, and records state.
3. **Weekly Analytics:** Weekly on Sunday
   - **Cron:** `20 18 * * 0`
   - **Pakistan Time (PKT):** Sunday 23:20 PKT
   - **Action:** Fetches 7-day metrics (views, watch time, subscribers, engagement) via YouTube Analytics API and commits markdown summary to `reports/`.

## Security & Secrets
All API credentials and keys are stored in encrypted repository secrets:
- `YT_CLIENT_ID`
- `YT_CLIENT_SECRET`
- `YT_REFRESH_TOKEN`
- `DRIVE_FOLDER_ID`
- `GEMINI_API_KEY`