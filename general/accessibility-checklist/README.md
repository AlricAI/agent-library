# Accessibility Checklist

> This checklist defines minimum accessibility requirements (WCAG 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Accessibility Checklist (WCAG for Mobile Apps)

This checklist defines minimum accessibility requirements (WCAG 2.2 A + AA) for mobile applications.

All UI features must pass this checklist before release.

---

## 1. Touch Targets

### Requirements

- [ ] All interactive elements are at least **24×24 px minimum** (WCAG 2.2 AA).
- [ ] Recommended target size: **48×48 px** for mobile usability.
- [ ] Interactive controls have at least **8px spacing** between targets.
- [ ] Icons inside tap targets remain visually centered.
- [ ] Buttons near screen edges have **>=16px margin from edges**.

### Applies to

- Buttons
- Toggles
- Tabs
- List items
- Icon buttons

---

## 2. Gesture Accessibility

### Requirements

- [ ] Any gesture requiring **drag or swipe** has a **tap alternative**.
- [ ] Multi-finger gestures are not required for core functionality.
- [ ] Path-based gestures (drawing shapes/swipes) have simple alternatives.

### Examples

Bad:

```
Swipe only to delete
```

Good:

```
Swipe OR tap delete button
```

---

## 3. Keyboard and External Input Support

### Requirements

- [ ] App is operable using **external keyboard navigation**.
- [ ] Logical **focus order** matches visual layout.
- [ ] Focus indicator is clearly visible.
- [ ] Focus is never hidden behind sticky headers or overlays.

### Test

- Navigate app using **Tab / arrow keys**.
- Verify all interactive elements are reachable.

---

## 4. Screen Reader Compatibility

### Requirements

- [ ] All interactive controls have **accessible names**.
- [ ] Inputs have **programmatic labels**.
- [ ] Icon-only buttons include accessible labels.
- [ ] Screen reader reading order matches visual order.

### Examples

Bad:

```
Icon button with no label
```

Good:

```
aria-label="Delete message"
```

---

## 5. Text and Readability

### Requirements

- [ ] Body text contrast ratio >= **4.5:1**.
- [ ] Large text contrast >= **3:1**.
- [ ] Text remains readable when system font size increases.
- [ ] Layout s

*[truncated — see source for full prompt]*