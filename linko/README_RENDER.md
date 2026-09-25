# Deploy Linko on Render

This version is prepared for a single Render Web Service with a Persistent Disk.

## Recommended deployment

1. Put the `linko` folder in a GitHub repository (or use this folder as the repository root).
2. In Render, choose **New > Blueprint** and select the repository.
3. Render will read `render.yaml` and create the Web Service plus a 1 GB Persistent Disk.
4. `SECRET_KEY` is generated automatically.
5. SQLite (`chat.db`) and uploaded files are stored under `/var/data` so they survive normal deploys/restarts.

## Important

- The included setup is intended for one web instance. Do not scale it horizontally while using the in-memory presence tracking and SQLite database.
- For a larger production deployment, move the database to PostgreSQL, uploads to object storage, and Socket.IO coordination to Redis.
- If you already have important data in `backend/chat.db`, copy it to the Persistent Disk before using the service, or migrate it separately. A fresh deployment starts with a new database.
