# Spec Backend Api 005

> **Priority**: HIGH | **Timeline**: Week 5-6 | **Team**: 1 Developer (Backend Focus)

---

## Objective

Create Laravel API endpoints that return mock 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Spec: Backend API with Mock Data (spec-backend-api-005)

**Priority**: HIGH | **Timeline**: Week 5-6 | **Team**: 1 Developer (Backend Focus)

---

## Objective

Create Laravel API endpoints that return mock data for all UI pages (HomePage, MapSearch, PropertyDetail). These endpoints will be consumed by React components via Inertia.js. Mock data will be replaced with real database queries in future iterations.

---

## Requirements

### Functional Requirements

1. **Property Endpoints**
   - `GET /api/properties` - List all properties (featured, paginated)
   - `GET /api/properties/{id}` - Get single property detail
   - `GET /api/properties/search` - Search properties with filters
   - `GET /api/amenities` - List all amenities
   - `GET /api/reviews` - List reviews for a property

2. **Search & Filter Functionality**
   - Filter by location (text search)
   - Filter by price range (min-max)
   - Filter by date availability
   - Filter by number of guests
   - Filter by property type
   - Filter by amenities
   - Sort by price, rating, newest

3. **Mock Data Structure**
   - 50+ mock properties with realistic data
   - Mock amenities (WiFi, Pool, Kitchen, etc.)
   - Mock reviews with ratings and comments
   - Mock host information
   - Mock images (use placeholder service)

4. **Response Format**
   - Consistent JSON response structure
   - Include pagination metadata
   - Include error messages for invalid requests
   - Include data validation

### Technical Requirements

- **Framework**: Laravel 12 with Inertia.js
- **API Format**: JSON responses
- **Mock Data**: Seeders and factories for generating data
- **Validation**: Form request validation for search parameters
- **Testing**: Feature tests for all endpoints
- **Documentation**: API endpoint documentation

---

## Design & Architecture

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/properties` | List featured properties (paginated) |
| GET | `/api/pr

*[truncated — see source for full prompt]*