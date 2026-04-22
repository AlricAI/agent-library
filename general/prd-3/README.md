# PRD

> ## 1. Project Overview
**Project Name**: Cal AI Web Clone
**Platform**: Web Application (Responsive Mobile-First Design)
**Description**: A comprehens

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Product Requirements Document (PRD) - Cal AI Web Clone

## 1. Project Overview
**Project Name**: Cal AI Web Clone
**Platform**: Web Application (Responsive Mobile-First Design)
**Description**: A comprehensive AI-powered nutrition tracker that simplifies calorie counting. Users upload photos of their food, and the system uses AI to analyze the image, identify the food, and provide a detailed nutritional report (calories, macros). Users can save these logs to track their daily intake.

## 2. Goals & Objectives
*   **Simplify Tracking**: Remove the friction of manual entry by using photo-based analysis.
*   **Accurate Reporting**: Provide estimated calories, protein, carbs, and fat for analyzed foods.
*   **History & Trends**: Allow users to view their daily consumption history.
*   **Web-First**: Deliver a native-app-like experience in a web browser.

## 3. Tech Stack
*   **Frontend Framework**: Next.js (App Router)
*   **Language**: TypeScript
*   **Styling**: TailwindCSS (with a premium, modern design aesthetic)
*   **State Management**: React Server Components / Server Actions
*   **Backend / API Strategy**:
    *   **Server Actions**: Primary method for data mutation and fetching from the client.
    *   **n8n Webhooks**: Used for heavy-lifting AI processing or complex backend workflows. The Next.js app will trigger n8n webhooks for image analysis.
*   **Database & Auth**: Supabase
    *   **Auth**: Email/Password, Social Login (Google/Apple - optional).
    *   **Database**: Postgres (managed by Supabase).
    *   **Storage**: Supabase Storage (for food images).

## 4. Key Features

### 4.1. Authentication
*   User Sign Up / Sign In using Supabase Auth.
*   Protected routes for Dashboard and Logging.

### 4.2. Food Analysis (Core Feature)
*   **Input**: User uploads an image (camera capture or gallery).
*   **Process**:
    1.  Image uploaded to Supabase Storage.
    2.  Server Action triggers an n8n webhook with the image URL/Binary.
    3.  n8n workflow proc

*[truncated — see source for full prompt]*