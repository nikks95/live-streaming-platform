# 🎬 Live Streaming Platform — Architecture (Phase 0)

This document describes the **high-level architecture** of the live streaming platform.  
At this stage (Phase 0), it’s a placeholder for what will evolve in later phases.

---

## 📐 High-Level System Design

```mermaid
flowchart LR
  subgraph Ingest
    Admin[Admin - Select Video] -->|Local File / FFmpeg push| IngestServer[nginx-rtmp / FFmpeg]
  end

  subgraph Transcoding
    IngestServer --> FFmpegWorker1[FFmpeg Worker - 720p]
    IngestServer --> FFmpegWorker2[FFmpeg Worker - 480p]
    IngestServer --> FFmpegWorker3[FFmpeg Worker - 360p]
    FFmpegWorker1 --> MinIO[(MinIO - Object Storage)]
    FFmpegWorker2 --> MinIO
    FFmpegWorker3 --> MinIO
  end

  subgraph Storage_and_CDN
    MinIO --> Origin[nginx Origin Server]
    Origin --> CDNProxy[nginx CDN Proxy (cache)]
  end

  subgraph Playback
    Frontend[React + hls.js Player] -->|HLS Playlist / Segments| CDNProxy
  end

  subgraph ControlPlane
    AdminUI[Admin UI] --> Backend[Backend API (NestJS/Node)]
    Frontend --> Backend
    Backend --> Postgres[(PostgreSQL)]
    Backend --> Redis[(Redis)]
    Backend --> Kafka[(Kafka - Events)]
  end

  subgraph Observability
    AllServices[All Services] --> Prometheus[(Prometheus Metrics)]
    AllServices --> Loki[(Loki Logs)]
    Prometheus --> Grafana[(Grafana Dashboards)]
  end
