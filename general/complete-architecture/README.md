# Complete Architecture

> Music recommendation system built with Apache Airflow 3.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# System Architecture

Music recommendation system built with Apache Airflow 3.0, processing Last.fm listening history through a medallion architecture to generate personalized recommendations.

The system avoids recommendation feedback loops by using exponential decay scoring with per-user half-life values, ensuring a balance between music discovery and forgotten favorites.

## Data Layers

**Bronze**: Raw JSON from Last.fm API

- User play history (daily per user)
- Track metadata (on-demand for new tracks)
- Artist metadata (on-demand for new tracks)

**Silver**: Structured Delta tables (GCS)

- Normalized plays (partitioned by user)
- Track and artist dimensions
- User profiles with computed half-life values
- Four types of recommendation candidates

**Gold**: Firestore (low-latency serving)

- Play counts with recency scores
- Unified track candidates ready for recommendations
- User exclusions (blocked tracks/artists)

## Data Pipeline

```mermaid
graph TB
    subgraph "External APIs"
        API[Last.fm API]
        YT[YouTube API]
    end

    subgraph "Bronze Layer"
        B1[plays JSON<br/>daily per user]
        B2[tracks JSON<br/>on-demand]
        B3[artists JSON<br/>on-demand]
    end

    subgraph "Silver Layer (GCS Delta)"
        S1[plays Delta<br/>partitioned by user]
        S2[tracks Delta<br/>dimension]
        S3[artists Delta<br/>dimension]
        S4[dim_users Delta<br/>profiles]
        S5[candidate_* Delta<br/>4 types per user]
    end

    subgraph "Gold Layer (Firestore)"
        G1[artist_play_count<br/>with recency]
        G2[track_play_count<br/>with recency]
        G3[track_candidates<br/>unified]
        G4[user exclusions<br/>tracks & artists]
    end

    subgraph "Application"
        APP[Streamlit UI]
    end

    API --> B1
    B1 --> S1

    S1 --> S5
    S2 --> S5
    S3 --> S5
    G2 --> S5

    S5 --> G3

    G3 --> API
    API --> B2
    API --> B3
    B2 --> S2
    B3 --> S3

    S1 --> S4

    S2 --> G1
    S3 --> G1
 

*[truncated — see source for full prompt]*