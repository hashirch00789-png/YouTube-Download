# YouTube Downloader Frontend

Responsive web frontend for YouTube video metadata lookup and downloads of media files the user owns or is authorized to distribute.

## Deployment

This repository is connected to the Render service `youtube-download-ivqt` and uses the included Dockerfile. Render deploys from `main`.

## Backend

The frontend calls the existing API service:

`https://youtube-downloader-backend-15cl.onrender.com/api/resolve`

The backend contract is defined in the separate `YouTube-Downloader-Backend` repository. It currently returns YouTube oEmbed metadata and an authorized download link only when an uploaded authorized file has been associated with that video ID. It does not extract arbitrary YouTube streams.

If the backend URL changes, edit `API_BASE` near the end of `public/index.html`, or set `window.YTD_CONFIG = { apiBase: "https://your-api.example.com" }` before the main script.

## Local run

```bash
npm install
npm start
```

Open http://localhost:10000.

## Health check

`GET /health` returns JSON status for the frontend service.

## Important

Do not place the backend `ADMIN_API_KEY` in browser code. Authorized media uploads must be performed through a secure server-side process. Use only media you own or have permission to distribute.