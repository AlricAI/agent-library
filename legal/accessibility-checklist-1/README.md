# Accessibility Checklist

> ## Overview

This checklist ensures all UI components and features meet WCAG 2.1 AA compliance standards and our commitment to inclusive design. It sh

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# YouAndINotAI Accessibility Compliance Checklist

## Overview

This checklist ensures all UI components and features meet WCAG 2.1 AA compliance standards and our commitment to inclusive design. It should be referenced during design, development, and QA processes.

## Visual Design Compliance

### Color Contrast

- [x] All text has minimum 4.5:1 contrast ratio against background
- [x] Large text (18pt+) has minimum 3:1 contrast ratio
- [x] UI controls have minimum 3:1 contrast ratio against adjacent colors
- [x] Hover and focus states maintain adequate contrast
- [x] Images of text meet contrast requirements

### Color Usage

- [x] Information is not conveyed through color alone
- [x] Custom focus indicators provided where default is removed
- [x] Sufficient color options for users with color blindness
- [ ] High contrast mode support tested
- [x] Meaningful iconography with text labels where necessary

### Typography

- [x] Minimum 16px base font size on mobile devices
- [x] Adequate line spacing (1.5x font height minimum)
- [ ] Clear visual hierarchy with heading levels
- [x] Appropriate font weights for readability
- [ ] Text resize support up to 200% without loss of functionality

## Interaction Design Compliance

### Keyboard Navigation

- [x] All interactive elements reachable via keyboard
- [~] Logical tab order follows visual layout
- [~] Visible focus indicators on all interactive elements
- [x] Keyboard traps avoided in modal dialogs
- [ ] Skip links provided for complex layouts

### Touch Targets

- [x] Minimum 48px touch target size for all interactive elements
- [x] Adequate spacing between touch targets (8px minimum)
- [x] Thumb-friendly placement for primary actions
- [x] Gestural alternatives for complex interactions
- [x] Clear visual affordances for touch interactions

### Forms and Inputs

- [x] All form fields have associated labels
- [x] Error messages provided for invalid inputs
- [x] Required field indicators clearly marked
- [ ] Instructions

*[truncated — see source for full prompt]*