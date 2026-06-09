# Next Services

The best next path is not to install everything. The order should protect the
existing Home Assistant and storage foundation first.

## 1. Uptime Kuma

- Need now: yes.
- Exposure: private or LAN-only.
- Data touched: availability history.
- Backup: monitor configuration.
- Home Assistant integration: possible summary sensor or notification.
- Reason to delay: only if no container or service runtime is chosen yet.

## 2. Netdata Or Glances

- Need now: useful after Uptime Kuma.
- Exposure: private only.
- Data touched: host metrics.
- Backup: minimal configuration.
- Home Assistant integration: optional summary.
- Reason to delay: avoid another always-on service until availability
  monitoring is in place.

## 3. Backup Verification Scripts

- Need now: yes.
- Exposure: private scripts, public docs only.
- Data touched: backup archives and metadata.
- Backup: script templates and docs, not backup archives.
- Home Assistant integration: backup age and warning sensors.
- Reason to delay: none; keep the first version simple.

## 4. External Storage Power Documentation

- Need now: yes.
- Exposure: public pattern, private implementation.
- Data touched: external storage state.
- Backup: private helper scripts.
- Home Assistant integration: guarded buttons and status sensors.
- Reason to delay: none.

## 5. Immich

- Need now: after backup verification.
- Exposure: private preferred.
- Data touched: photos, database, thumbnails.
- Backup: library and database both required.
- Home Assistant integration: optional.
- Reason to delay: photo libraries become important data quickly.

## 6. Plex Or Jellyfin

- Need now: after storage and backup are stable.
- Exposure: LAN/private preferred.
- Data touched: media library and metadata.
- Backup: metadata optional, media library required.
- Home Assistant integration: media status and scenes.
- Reason to delay: account claim, transcoding, and storage choices.

## 7. Paperless-ngx

- Need now: after backup strategy is proven.
- Exposure: private only.
- Data touched: documents, receipts, manuals, contracts.
- Backup: database, documents, consume/archive folders.
- Home Assistant integration: optional notifications.
- Reason to delay: contains sensitive documents.

## 8. n8n

- Need now: later.
- Exposure: private only unless heavily secured.
- Data touched: workflow credentials and logs.
- Backup: database and credential store.
- Home Assistant integration: notifications and read-only summaries first.
- Reason to delay: automation credentials can become sensitive.

## 9. Open WebUI And Ollama

- Need now: later.
- Exposure: private only.
- Data touched: prompts, model cache, optional documents.
- Backup: configuration and selected data.
- Home Assistant integration: read-only summary first.
- Reason to delay: resource use can affect server reliability.

## 10. Vector DB

- Need now: only after document ingestion is clear.
- Exposure: private only.
- Data touched: embeddings and document metadata.
- Backup: index can often be rebuilt, source documents matter more.
- Home Assistant integration: read-only knowledge search.
- Reason to delay: RAG is not useful until sources and backup policy are clear.

