# Spec Ui Mapsearch 002

> **Priority**: HIGH | **Timeline**: Week 2-3 | **Team**: 1 Developer (Frontend Focus)

---

## Objective

Convert the MapSearch mock HTML design (`mock

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Spec: MapSearch UI Implementation (spec-ui-mapsearch-002)

**Priority**: HIGH | **Timeline**: Week 2-3 | **Team**: 1 Developer (Frontend Focus)

---

## Objective

Convert the MapSearch mock HTML design (`mock/map_search/code.html`) into a fully functional React component with TypeScript, Tailwind CSS 4, and Inertia.js. The page must display an interactive map with property markers, a search filter panel, and a property list view. The design must match `mock/map_search/screen.png`.

---

## Requirements

### Functional Requirements

The MapSearch page must include:

1. **Search Filter Panel** (Left Sidebar or Top)
   - Location input with autocomplete
   - Check-in and check-out date pickers
   - Number of guests selector
   - Price range slider (min-max)
   - Property type filter (apartment, house, villa, etc.)
   - Amenities checkboxes (WiFi, Pool, Kitchen, etc.)
   - Apply/Reset filters buttons

2. **Interactive Map** (Center/Right)
   - Display map with property markers
   - Marker clustering for zoomed-out view
   - Click marker to show property preview
   - Map controls (zoom, pan, fullscreen)
   - Show property count on map

3. **Property List View** (Right Sidebar or Bottom)
   - List of properties matching filters
   - Each item shows: image, title, location, price, rating
   - Sort options (price: low-high, high-low, rating, newest)
   - Pagination or infinite scroll
   - Click to navigate to property detail page

4. **Responsive Layout**
   - Desktop: Filters (left) + Map (center) + List (right)
   - Tablet: Filters (top) + Map (full width) + List (collapsible)
   - Mobile: Filters (modal/drawer) + Map (full width) + List (below map)

### Technical Requirements

- **Framework**: React 19 with TypeScript
- **Styling**: Tailwind CSS 4
- **Routing**: Inertia.js for navigation
- **Map Integration**: Google Maps API (via proxy) or Mapbox
- **Data**: Mock data service with search/filter logic
- **Responsiveness**: Mobile-first, tested on all breakpoints
- **P

*[truncated — see source for full prompt]*