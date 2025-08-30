# RIVF_2025___Object_ReID___Vinh_Ha
A Streaming Big-Data Pipeline for Real-Time Vehicle Re-Identification in Chaotic Urban Traffic

Kafka → Spark Structured Streaming → YOLO + ByteTrack → OSNet + FAISS → MongoDB
Domain: Vietnam motorcycle-dominated traffic · Time gate: 10–30s · Cosine thresholds: 0.65 / 0.75 / 0.85

<img width="1232" height="697" alt="image" src="https://github.com/user-attachments/assets/25720f9b-3cfe-48a5-be5f-3abec48ce8b3" />

1) Overview

This repository contains a deployment-ready streaming Re-ID pipeline for chaotic urban traffic:

Ingestion: Multi-camera producer GUI publishes base64 frames to Kafka.

Streaming compute (Spark):
YOLO detection + ByteTrack (per-camera local IDs) → crop → OSNet embeddings (512-D) → FAISS cosine search with time gating (10–30s) → cross-camera Re-ID → (optional) speed estimation using inter-camera distances.

Storage: Each detection is persisted to MongoDB with full metadata (embedding, bbox, sim, pass@{0.65,0.75,0.85}, segment, speed…).

Evaluation: Reproducible scripts for mAP/CMC, ROC/PR, and threshold tables, plus LaTeX-ready tables/figures.

2) Key features

⚡ Real-time Spark Structured Streaming with GPU batch inference

🧭 Temporal gating (default 10–30 s) for physically plausible matches

🧠 OSNet (torchreid) embeddings + FAISS cosine search

🎯 Threshold study at 0.65 / 0.75 / 0.85 (operational θ=0.75)

🏍️ Motorcycle-centric; robust to dense occlusions

🧾 MongoDB documents keep full 512-D embeddings + metadata

📊 One-command evaluation → LaTeX tables + PDF plots

3) Repository structure

<img width="1286" height="674" alt="image" src="https://github.com/user-attachments/assets/a1fd9df9-6b3f-4036-ae22-52084fcc1cc1" />



