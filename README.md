# live-streaming-platform

🎥 A full-stack project simulating a Hotstar-like live streaming system,  
built locally on WSL2 with Docker and Kubernetes.

## Goals
- End-to-end live streaming with HLS/WebRTC
- Full-stack design (React + NodeJS + Postgres + Redis + Kafka + MinIO)
- Production-like architecture, runnable fully on local machine
- Focus on system design, scalability, observability

## Roadmap
- Phase 0: Repo setup (current)
- Phase 1: Minimal MVP (HLS)
- Phase 2: Core features (auth, metadata)
- Phase 3: Transcoding & ABR
- Phase 4: Low latency
- Phase 5: Scalability sim (K8s, CDN, autoscaling)
- Phase 6: Observability & analytics
- Phase 7: Hardening & polish

## Tech Stack (planned)
- **Frontend:** React + TS, hls.js
- **Backend:** Node.js (NestJS) / Spring Boot (to be finalized)
- **Media:** FFmpeg, nginx-rtmp
- **Storage:** Postgres, MinIO, Redis
- **Infra:** Docker Compose, k3s
- **Observability:** Prometheus, Grafana, Loki
- **CI/CD:** GitHub Actions