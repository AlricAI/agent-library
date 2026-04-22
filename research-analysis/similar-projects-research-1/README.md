# SIMILAR PROJECTS RESEARCH

> ## Overview

This document summarizes research into similar projects and identifies enhancement opportunities for Atlas based on proven solutions in t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Similar Projects Research & Enhancement Opportunities

## Overview

This document summarizes research into similar projects and identifies enhancement opportunities for Atlas based on proven solutions in the knowledge management and content ingestion space.

## Projects Analyzed

### 1. Wallabag - Read-it-later Service
**Repository**: https://github.com/wallabag/wallabag
**Key Strength**: Superior article extraction and content parsing

#### Current Atlas Gap
- Basic readability extraction often fails on complex sites
- No paywall detection or handling
- Limited site-specific extraction rules

#### Wallabag Solutions
- **Multi-stage extraction pipeline** with fallback methods
- **Site-specific XPath configurations** for custom extraction rules
- **Paywall detection** using phrase patterns and HTML elements
- **Content quality validation** with length and ratio checks

### 2. Miniflux - Minimalist Feed Reader
**Repository**: https://github.com/miniflux/v2
**Key Strength**: Intelligent duplicate detection and content management

#### Current Atlas Gap
- No duplicate detection across sources
- Content may be processed multiple times
- No URL normalization

#### Miniflux Solutions
- **Multi-level duplicate detection**: URL hash, content hash, title similarity
- **URL normalization**: Remove tracking parameters, normalize domains
- **Efficient storage**: Prevent duplicate content storage

### 3. FreshRSS - Self-hosted RSS Feed Aggregator
**Repository**: https://github.com/FreshRSS/FreshRSS
**Key Strength**: Automatic content categorization

#### Current Atlas Gap
- Manual categorization only via AI classification
- No rule-based categorization system
- Limited content organization

#### FreshRSS Solutions
- **Multi-signal categorization**: URL patterns, keywords, content analysis
- **Configurable rules**: YAML-based category definitions
- **Scoring system**: Multi-dimensional category scoring

### 4. RSS-Bridge - Website to RSS Converter
**Repository**: https://github.

*[truncated — see source for full prompt]*