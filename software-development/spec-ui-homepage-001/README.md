# Spec Ui Homepage 001

> **Priority**: HIGH | **Timeline**: Week 1-2 | **Team**: 1 Developer (Frontend Focus)

---

## Objective

Convert the HomePage mock HTML design (`mocks

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Spec: HomePage UI Implementation (spec-ui-homepage-001)

**Priority**: HIGH | **Timeline**: Week 1-2 | **Team**: 1 Developer (Frontend Focus)

---

## Objective

Convert the HomePage mock HTML design (`mocks/homepage/code.html`) into a fully functional, production-ready React component using TypeScript, Tailwind CSS 4, and Inertia.js. The component follows an Airbnb-style listings page design with sticky header, category filters, and responsive property grid.

---

## Requirements

### Functional Requirements

The HomePage must include the following sections:

1. **Sticky Header**
   - Logo/branding (StayHub with Leaf icon)
   - Search pill with "Anywhere | Any week | Add guests" sections
   - "Switch to hosting" button (desktop)
   - Language selector (Globe icon)
   - User menu with authentication state indicator

2. **Category Bar**
   - Horizontal scrollable category tabs with icons (Treehouses, Cabins, Beachfront, etc.)
   - Active state styling with primary color border
   - Filters button with sliders icon
   - Hidden scrollbar with smooth scrolling

3. **Property Listings Grid**
   - Responsive grid (1 col mobile, 2 cols tablet, 3 cols medium, 4 cols desktop)
   - Each card displays: image, location, title, dates, price per night, rating
   - Hover effects: image zoom, pagination dots visibility
   - Favorite button with heart icon
   - Lazy loaded images

4. **Floating Map Button**
   - Fixed position at bottom center
   - Dark background with "Show map" text and Map icon
   - Hover scale effect

5. **Footer**
   - 4-column layout (Support, Hosting, StayHub, Eco-Luxe)
   - Language/currency selectors
   - Social media icons (Facebook, Twitter, Instagram)
   - Copyright and legal links

### Technical Requirements

- **Framework**: React 19 with TypeScript
- **Styling**: Tailwind CSS 4 (utility-first, no custom CSS unless necessary)
- **Routing**: Inertia.js Link components for navigation
- **Data**: Mock data service (no real API calls yet)
- **Responsiven

*[truncated — see source for full prompt]*