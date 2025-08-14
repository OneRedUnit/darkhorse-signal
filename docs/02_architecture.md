# Архитектура

```mermaid
flowchart LR
    A[STREAM: ingest] -->|market, news, social, tick| B[Normalize & Cache]
    B --> P[PULSE]
    B --> T[PATTERN]
    B --> V[VOICE]
    B --> W[WAVES]
    P & T & V & W --> F[Fusion & Scoring]
    F --> N[NEXUS: Reports & Actions]
    N --> O1[Artifacts MD/HTML/JSON]
    N --> O2[Alerts/Chat/Pages]
