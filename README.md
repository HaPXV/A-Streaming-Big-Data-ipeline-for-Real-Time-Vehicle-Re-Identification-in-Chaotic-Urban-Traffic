# RIVF_2025___Object_ReID___Vinh_Ha
A Streaming Big-Data Pipeline for Real-Time Vehicle Re-Identification in Chaotic Urban Traffic

We present a deployment-ready, real-time
vehicle re-identification (Re-ID) pipeline designed for
motorcycle-dominated, non-lane urban traffic. The system
integrates Apache Kafka and Spark Structured Streaming
with modern detection, tracking, and embedding models,
enabling city-scale streaming operation with temporal-
gated FAISS retrieval and persistent metadata for analysis.
To support evaluation under realistic conditions, we re-
lease a new multi-camera dataset from Ho Chi Minh City
that captures dense occlusions and irregular flows often
missing in existing benchmarks. Our work contributes (i) a
scalable big-data Re-ID pipeline, (ii) a motorcycle-centric
dataset with reproducible evaluation, and (iii) a foundation
for practical intelligent transportation and urban security
applications in developing cities.

<img width="1232" height="697" alt="image" src="https://github.com/user-attachments/assets/25720f9b-3cfe-48a5-be5f-3abec48ce8b3" />

Overview

This repository contains a deployment-ready streaming Re-ID pipeline for chaotic urban traffic:

Ingestion: Multi-camera producer GUI publishes base64 frames to Kafka.

Streaming compute (Spark):
YOLO detection + ByteTrack (per-camera local IDs) → crop → OSNet embeddings (512-D) → FAISS cosine search with time gating (10–30s) → cross-camera Re-ID → (optional) speed estimation using inter-camera distances.

Storage: Each detection is persisted to MongoDB with full metadata (embedding, bbox, sim, pass@{0.65,0.75,0.85}, segment, speed…).

Evaluation: Reproducible scripts for mAP/CMC, ROC/PR, and threshold tables, plus LaTeX-ready tables/figures.




