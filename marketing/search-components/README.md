# Search Components

> ## Overview

A comprehensive search system for YouAndINotAI that enables users to discover community members, events, groups, and content through intu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Search Components Specification

## Overview

A comprehensive search system for YouAndINotAI that enables users to discover community members, events, groups, and content through intuitive, accessible, and privacy-respecting search functionality.

## Component Structure

### SearchBar

Primary input for search queries with autocomplete suggestions

### SearchResults

Container for displaying search results with categorization

### SearchResultItem

Individual search result display with contextual information

### SearchFilters

Advanced filtering controls for refining search results

### SearchHistory

Storage and display of recent search queries

### SearchSuggestions

Intelligent query suggestions based on input

## Component Specifications

### SearchBar

#### Props

| Prop          | Type                  | Required | Description                       |
| ------------- | --------------------- | -------- | --------------------------------- |
| placeholder   | String                | No       | Placeholder text for search input |
| initialValue  | String                | No       | Initial search query value        |
| onSearch      | Function              | Yes      | Callback when search is submitted |
| onInputChange | Function              | No       | Callback when input changes       |
| onClear       | Function              | No       | Callback when search is cleared   |
| autoFocus     | Boolean               | No       | Whether to auto-focus on mount    |
| disabled      | Boolean               | No       | Whether search is disabled        |
| categories    | Array<SearchCategory> | No       | Available search categories       |

#### SearchCategory Interface

```typescript
interface SearchCategory {
  id: string;
  name: string;
  icon: string;
  placeholder: string;
}
```

#### Behavior

- Real-time autocomplete suggestions as user types
- Keyboard navigation support (arrow keys, enter)
- Search history integration
- Category-specific placeholders 

*[truncated — see source for full prompt]*