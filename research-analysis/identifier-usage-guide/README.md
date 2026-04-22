# Identifier Usage Guide

> ## Overview

Identifiers in the theme system allow you to target specific components for theme overrides using the `data-id` attribute. This guide sho

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Using Identifiers in Custom Plugins

## Overview

Identifiers in the theme system allow you to target specific components for theme overrides using the `data-id` attribute. This guide shows how to use identifiers in your custom plugins.

## How Identifiers Work

### 1. Theme Definition
In your theme files, use the `#identifier` syntax:

```typescript
// app/theme/my-theme/theme.ts
export default defineTheme({
    name: 'my-theme',
    colors: {
        primary: '#3f8452',
        secondary: '#5a7b62',
        surface: '#f5faf5'
    },
    overrides: {
        // Global button style
        'button': { variant: 'solid' },
        
        // Context-specific button style
        'button.chat': { variant: 'ghost' },
        
        // Identifier-specific button style (most specific)
        'button#chat.send': { 
            variant: 'solid', 
            color: 'primary',
            size: 'md'
        },
        
        // Multiple identifiers for different actions
        'button#sidebar.new-chat': { variant: 'outline' },
        'button#sidebar.settings': { variant: 'ghost' },
        'input#chat.message': { 
            variant: 'outline',
            size: 'lg'
        }
    }
});
```

### 2. Component Usage
Use the `v-theme` directive with identifiers:

```vue
<template>
    <!-- Basic usage - auto-detects component type -->
    <UButton v-theme>Default Button</UButton>
    
    <!-- With identifier - adds data-id="chat.send" -->
    <UButton v-theme="'chat.send'">Send Message</UButton>
    
    <!-- Object syntax with full control -->
    <UButton v-theme="{ 
        identifier: 'chat.send', 
        theme: 'my-theme', 
        context: 'chat' 
    }">
        Send with Custom Theme
    </UButton>
    
    <!-- Input with identifier -->
    <UInput v-theme="'chat.message'" placeholder="Type a message..." />
    
    <!-- Custom component with identifier -->
    <MyCustomComponent v-theme="'my-plugin.action'" />
</template>
```

### 3. Custom Plugin Impleme

*[truncated — see source for full prompt]*