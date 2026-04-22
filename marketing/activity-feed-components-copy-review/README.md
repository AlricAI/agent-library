# Activity Feed Components Copy Review

> ## Overview

Copy elements for review in the new activity feed components for YouAndINotAI.

## Components with Copy Elements

### ActivityFeed (`desi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Activity Feed Components Copy Review

## Overview

Copy elements for review in the new activity feed components for YouAndINotAI.

## Components with Copy Elements

### ActivityFeed (`design-specs/activity-feed-components.md`)

#### UI Text Labels

- "Activity Feed" (section header)
- "New Activity" (composer button)
- "Refresh Feed" (refresh button)
- "Load More Activities" (load more button)
- "No activities to show" (empty state)
- "Check back later for updates" (empty state suggestion)

#### Loading States

- "Loading activities..." (initial load)
- "Loading more activities..." (pagination)
- "Refreshing feed..." (manual refresh)
- "Failed to load activities" (error state)

#### Error Messages

- "Unable to connect to activity feed" (connection error)
- "Please check your internet connection" (network error)
- "Something went wrong. Try refreshing?" (generic error)
- "Content blocked by privacy settings" (privacy error)

### ActivityItem (`design-specs/activity-feed-components.md`)

#### Activity Types & Templates

- "{username} created a new event: {eventname}"
- "{username} attended {eventname}"
- "{username1} and {username2} are now connected"
- "{username} completed {volunteerhours} hours of volunteering"
- "{username} shared: {postcontent}"
- "{username} unlocked the {achievementname} achievement"

#### Metadata Labels

- "Posted {timeago}" (timestamp)
- "via Mobile App" / "via Web" (posting method)
- "{groupanme} Group" (group context)
- "{location}" (location context)
- "Private Activity" (privacy indicator)

#### Engagement Metrics

- "{count} likes" (like count)
- "{count} comments" (comment count)
- "{count} shares" (share count)
- "You and {count} others liked this" (personalized like)
- "{username} and {count} others commented" (comment highlights)

### ActivityComposer (`design-specs/activity-feed-components.md`)

#### Placeholder Text

- "Share what's happening in your community..." (general)
- "What event are you planning?" (event context)
- "Te

*[truncated — see source for full prompt]*