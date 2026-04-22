# USER GUIDE

> Atlas is a comprehensive personal content ingestion, processing, and search system designed to help you capture, organize, and discover insights from 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas User Guide

Atlas is a comprehensive personal content ingestion, processing, and search system designed to help you capture, organize, and discover insights from various content sources including articles, podcasts, documents, and more.

## Table of Contents

1. [Quick Start](#quick-start)
2. [System Overview](#system-overview)
3. [Content Processing](#content-processing)
4. [Search & Discovery](#search--discovery)
5. [Analytics Dashboard](#analytics-dashboard)
6. [API Usage](#api-usage)
7. [Configuration](#configuration)
8. [Troubleshooting](#troubleshooting)

## Quick Start

### Prerequisites
- Python 3.8+
- 4GB+ RAM recommended
- 10GB+ storage space

### Installation
1. Clone the repository and navigate to the Atlas directory
2. Copy `env.template` to `.env` and configure your settings
3. Install dependencies: `pip install -r requirements.txt`
4. Start the system: `./start_work.sh`

### First Steps
1. **Add content**: Place URLs in `inputs/articles.txt` or upload documents to `inputs/`
2. **Start processing**: The background service automatically processes new content every 30 minutes
3. **Access dashboard**: Open `https://atlas.khamel.com/api/v1/dashboard/` in your browser
4. **Search content**: Use the search API or dashboard interface

## System Overview

### Architecture Components

Atlas consists of several integrated components:

- **Content Ingestors**: Process articles, documents, podcasts, YouTube videos
- **Search Engine**: Full-text search with ranking and filtering
- **Analytics Engine**: Content consumption patterns and insights
- **API Framework**: RESTful API for all system operations
- **Dashboard**: Web interface for monitoring and interaction
- **Background Service**: Automated content processing and maintenance

### Content Types Supported

- **Articles**: Web articles, blog posts, news content
- **Documents**: PDF, TXT, Markdown files
- **Podcasts**: RSS feeds with transcript extraction
- **YouTube**: Videos with automatic transcript d

*[truncated — see source for full prompt]*