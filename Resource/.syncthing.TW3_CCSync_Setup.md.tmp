---
id: TW3_CCSync_Setup
aliases: []
tags:
  - resource
  - tipjar
date: Friday October 31st 2025
---

# TW3 Mobile: CCSync front-end for Taskchampion — quick setup

**Date:** 2025-10-28 03:59:05 UTC

---

## Overview

The new **Taskwarrior Flutter app** requires the **CCSync API** as a front end to a Taskchampion sync server.  
Your desktop Taskwarrior 3 (TW3) continues to sync directly with `taskchampion-sync-server`, while the mobile app talks to **CCSync**, which then communicates with that server.

---

## 1. Deploy CCSync

Here’s a minimal Docker Compose setup:

```yaml
version: "3.8"
services:
  ccsync:
    image: ghcr.io/ccextractor/ccsync:latest
    environment:
      CC_JWT_SECRET: "change-me"
      CC_SYNC_SERVER_URL: "http://sync:8080"  # or your existing external URL
    ports:
      - "8000:8000"
    depends_on:
      - sync

  sync:
    image: ghcr.io/gothenburgbitfactory/taskchampion-sync-server:latest
    ports:
      - "8080:8080"
    volumes:
      - syncdata:/data

volumes:
  syncdata:
```

If you already have a sync-server running, remove the `sync:` block and set:

```yaml
CC_SYNC_SERVER_URL: "https://your-existing-sync.example.com"
```

---

## 2. Add HTTPS

Put CCSync behind **NGINX**, **Caddy**, or **Traefik**.  
Expose it on port 443 with a valid TLS certificate.  
The Flutter app will reject plain HTTP over the internet.

---

## 3. Configure the Flutter App

In the mobile app:

1. Open **Settings → Taskchampion Sync**  
2. Choose **CCSync Credentials**  
3. Paste your CCSync API URL and token  
4. Save and test sync

---

## 4. Keep Desktop TW3 as-is

TW3 configuration stays the same:

```bash
task config sync.server.url https://your-sync.example.com
task config sync.server.client_id <your_client_id>
task config sync.encryption_secret "<same secret>"
task sync
```

Each device needs its own `client_id`, but the same `encryption_secret`.

---

## 5. Sanity Checklist

- [x] `docker ps` shows `ccsync` healthy  
- [x] Reverse proxy serves `https://ccsync.example.com`  
- [x] Mobile app syncs successfully  
- [x] Desktop `task sync` works  
- [x] Tasks sync both directions

---

## Gotchas

- `CC_SYNC_SERVER_URL` must be reachable from the **CCSync container**, not your laptop.  
- Always use HTTPS publicly.  
- Avoid copying TaskChampion data files manually; use the sync protocol.  
- Keep your JWT secret and encryption secret private.

---

**Author:** ChatGPT — generated for Marty@dabuke.com  
**Timestamp:** 2025-10-28T03:59:05.184423
