# Database Schema

> ## 1. Overview
The RoomieHKU database is designed to provide a structured and efficient platform for HKU students to find housing and roommates. Built

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# RoomieHKU Database Schema Documentation

## 1. Overview
The RoomieHKU database is designed to provide a structured and efficient platform for HKU students to find housing and roommates. Built with **Django ORM** and backed by **SQLite**, the schema emphasizes relational integrity, social engagement (likes/comments), and high-performance listing discovery.

---

## 2. Entity Relationship Diagram (ERD)
The following diagram illustrates the core relationships between users, listings, and social interactions.

```mermaid
erDiagram
    USER ||--o{ POST : "publishes"
    USER ||--o{ COMMENT : "writes"
    USER ||--o{ LIKE : "clicks"
    USER ||--o{ SAVED_LISTING : "saves"
    
    POST ||--o{ COMMENT : "receives"
    POST ||--o{ LIKE : "tracked_by"
    POST ||--o{ SAVED_LISTING : "bookmarked_in"

    USER {
        int id PK
        string username UK "Unique"
        string email "Contact Email"
        string phone_number "Contact Phone (Optional)"
        text bio "User Introduction"
        string profile_photo "Uploaded image path"
        bool is_suspended "Staff moderation flag"
        datetime suspended_at "When suspension was applied"
    }

    POST {
        int id PK
        int author_id FK "References User"
        string title
        text description
        string image_url "Uploaded listing image path"
        string listing_type "Apartment / Dorm / Roommate"
        string location "HKU Vicinity (e.g., Kennedy Town)"
        decimal price "Monthly rent or budget"
        date move_in_date "Availability date"
        string gender_preference "M / F / N"
        text lifestyle_notes "For roommate matching"
        int likes_count "Denormalized for popularity sorting"
        int views_count "Denormalized listing page-view counter"
        bool is_hidden "Staff moderation visibility flag"
        datetime hidden_at "When listing was hidden"
        datetime created_at "Timestamp"
        datetime updated_at
    }

    COMMENT {
        int id PK
       

*[truncated — see source for full prompt]*