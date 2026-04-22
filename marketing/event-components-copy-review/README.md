# Event Components Copy Review

> ## Overview

Copy elements for review in the new event discovery components.

## Components with Copy Elements

### CommunityEventCard (`design-specs/

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Event Components Copy Review

## Overview

Copy elements for review in the new event discovery components.

## Components with Copy Elements

### CommunityEventCard (`design-specs/community-event-card-component.md`)

#### UI Text Labels

- "Going" / "Maybe" / "Not Going" (RSVP actions)
- "{count} friends attending" / "You and {count} others" / "Just you"
- "{category} event" (category label)
- "Accessibility: {features}" (accessibility info)
- "Safety: {guidelines}" (safety info)
- "Virtual event" / "In-person event"
- "{current}/{max} spots filled"

#### Empty States

- No image: "{eventTitle} event image"
- Loading: "Loading event details..."
- Error: "Event details unavailable"

### RSVPButtonGroup (`design-specs/rsvp-button-group-component.md`)

#### Button Labels

| Status    | Label (Full) | Label (Compact) |
| --------- | ------------ | --------------- |
| Going     | "I'm Going"  | "✓"             |
| Maybe     | "Maybe"      | "?"             |
| Not Going | "Can't Go"   | "✕"             |

#### Status Messages

| Message | Text                                |
| ------- | ----------------------------------- |
| Loading | "Updating your RSVP..."             |
| Success | "RSVP updated successfully!"        |
| Error   | "Failed to update RSVP. Try again?" |
| Retry   | "Retry"                             |

#### Empty States

- No selection: "Select your attendance"
- Loading initial: "Loading RSVP status..."

### Event Discovery Flow (`design-specs/event-discovery-flow.md`)

#### Navigation and Section Headers

- "Upcoming Events Near You"
- "View All Events"
- "Events"
- "Filter"

#### Filter Options

- "Today", "This Weekend", "Tomorrow", "Next Week"
- "Meetups", "Workshops", "Volunteering", "Social Events", "Outdoors", "Learning"
- "Within 5 miles", "Within 10 miles"
- "Wheelchair Access", "ASL Interpretation", "Captioning", "Service Animals Welcome"
- "Reset", "Apply Filters"

#### Detail View Elements

- "Add to Calendar", "Share Event"
- "Discussi

*[truncated — see source for full prompt]*