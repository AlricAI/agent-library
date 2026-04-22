---
name: Component Design Decision Tree (Electron Desktop)
description: description: Component design decision tree for Electron desktop UI components globs: - "packages/**/components/**/*"
---
---
description: Component design decision tree for Electron desktop UI components
globs:
  - "packages/**/components/**/*"
  - "packages/**/ui/**/*"
  - "apps/*/src/components/**/*"
scopes:
  - react
  - frontend
  - ui
  - components
  - architecture
  - electron
alwaysApply: false
---

# Component Design Decision Tree (Electron Desktop)

## 🎯 Purpose
This rule provides a clear decision-making framework for choosing component patterns in the **Electron desktop renderer**. Since this is a desktop-only application, mobile/responsive patterns are not applicable.

---

## 📊 Decision Flow

### Step 1: Is this a third-party component wrapper?

**YES** → Create wrapper component
- Wrap Mantine or other library components with project-specific defaults
- Place in appropriate directory (`src/ui/` or `components/`)
- Create Storybook stories to document variants
- Example: Custom Button wrapping `@mantine/core` Button with PM Agent theme

**NO** → Continue to Step 2

---

### Step 2: Is this a new reusable component (not a page)?

**YES** → Follow **Storybook-First Development**
- Build component in isolation first
- Create `.stories.tsx` with all variants and states
- Test component independently before integration
- Document props and usage patterns

**NO** → Continue to Step 3

---

### Step 3: Is this a complex feature component?

**YES** → Use **Bulletproof Pattern**
- Follow `react-bulletproof-component-pattern.rules.mdc`
- Separate concerns: component, styles, types, tests
- Use co-location for related files
- Ensure proper error boundaries

**NO** → Simple component, use basic React patterns

---

## 🔄 Common Patterns for PM Agent

### Pattern 1: Wrapped UI Library Component (Storybook)
**Use for:** Buttons, Inputs, Cards from Mantine
```
src/ui/Button/
├── Button.tsx         # Wrapper with PM Agent defaults
├── Button.stories.tsx # All variants
└── Button.test.tsx    # Component tests
```

### Pattern 2: Custom Reusable Component (Bulletproof + Storybook)
**Use for:** ProjectCard, MetricDisplay, TodoList
```
components/ProjectCard/
├── ProjectCard.tsx         # Main component
├── ProjectCard.styles.ts   # Styled components
├── ProjectCard.types.ts    # TypeScript types
├── ProjectCard.stories.tsx # Storybook stories
└── ProjectCard.test.tsx    # Tests
```

### Pattern 3: Feature Component (Bulletproof)
**Use for:** MotivationDashboard, ProjectViewer, QualityScorePanel
```
features/MotivationDashboard/
├── MotivationDashboard.tsx
├── components/            # Feature-specific sub-components
├── hooks/                 # Custom hooks
├── MotivationDashboard.stories.tsx
└── MotivationDashboard.test.tsx
```

### Pattern 4: Page Component (Simple)
**Use for:** SettingsPage, AboutPage
```
pages/SettingsPage/
├── SettingsPage.tsx      # Simple page component
└── SettingsPage.test.tsx
```

---

## 📋 Quick Reference Chart

| Scenario | Patterns to Apply |
|----------|------------------|
| Wrapping Mantine Button | Wrapper + Storybook |
| Project Card (reusable) | Bulletproof + Storybook |
| Motivation Dashboard (complex) | Bulletproof + Feature pattern |
| Quality Score Display | Bulletproof + Storybook |
| Settings Page | Simple React component |
| Todo List Item | Bulletproof |
| Screenshot Gallery | Bulletproof + Storybook |

---

## ⚠️ Desktop-Specific Considerations

### Window Sizing
- Design for **minimum window size**: 1024x768
- Support **maximum window size**: unbounded (user preference)
- Test at common resolutions: 1920x1080, 2560x1440, 3840x2160 (4K)

### Native Feel
- Use desktop UI patterns (no hamburger menus, proper right-click context menus)
- Support keyboard navigation (tab, arrows, shortcuts)
- Implement proper focus management
- Use native-feeling scrollbars and controls

### Performance
- Desktop allows for richer interactions (animations, transitions)
- No mobile performance constraints
- Can use larger assets and heavier libraries
- Still optimize for smooth 60fps rendering

---

## 🔗 Related Rules

- `react-bulletproof-component-pattern.rules.mdc` - Component structure and testing
- `monorepo-node-electron-express-hexagonal-architecture.rules.mdc` - IPC communication patterns
- `brain-monitor-validation.rules.mdc` - Testing and validation

---

## 💡 Examples

### Example 1: Wrapping Mantine Button

**Decision Path:**
1. Third-party wrapper? **YES** → Create wrapper
2. Reusable component? **YES** → Add Storybook

**Implementation:**
```tsx
// src/ui/Button/Button.tsx
import { Button as MantineButton, ButtonProps } from '@mantine/core';
import styled from '@emotion/styled';

export const Button = styled(MantineButton)<ButtonProps>`
  font-family: 'Inter', sans-serif;
  transition: all 0.2s ease;

  &:hover {
    transform: translateY(-1px);
  }
`;

// src/ui/Button/Button.stories.tsx
import type { Meta, StoryObj } from '@storybook/react';
import { Button } from './Button';

const meta: Meta<typeof Button> = {
  title: 'UI/Button',
  component: Button,
};

export default meta;
type Story = StoryObj<typeof Button>;

export const Primary: Story = {
  args: { children: 'Click me', variant: 'filled' },
};

export const Secondary: Story = {
  args: { children: 'Secondary', variant: 'outline' },
};
```

---

### Example 2: Project Card Component

**Decision Path:**
1. Third-party wrapper? **NO**
2. Reusable component? **YES** → Bulletproof + Storybook
3. Complex feature? **YES** → Full bulletproof pattern

**Implementation:**
```tsx
// components/ProjectCard/ProjectCard.tsx
import { Card } from '@mantine/core';
import type { ProjectCardProps } from './ProjectCard.types';
import { useProjectCard } from './useProjectCard';

export const ProjectCard: React.FC<ProjectCardProps> = ({ project }) => {
  const { qualityScore, badges, handleClick } = useProjectCard(project);

  return (
    <Card onClick={handleClick} shadow="sm" padding="lg">
      <h3>{project.name}</h3>
      <div>Quality: {qualityScore}/100</div>
      <div>{badges.map(badge => badge)}</div>
    </Card>
  );
};

// components/ProjectCard/ProjectCard.types.ts
export interface ProjectCardProps {
  project: Project;
  onSelect?: (project: Project) => void;
}

// components/ProjectCard/ProjectCard.stories.tsx
export default {
  title: 'Components/ProjectCard',
  component: ProjectCard,
};

export const HighQuality: Story = {
  args: {
    project: {
      name: 'cannabis-codex',
      qualityScore: 94,
      // ...
    },
  },
};
```

---

## 🎓 Learning Path

**For New Developers:**
1. Start with `react-bulletproof-component-pattern.rules.mdc` for structure
2. Use Storybook for all reusable components
3. Focus on desktop UX patterns (no mobile considerations)
4. Integrate with Electron IPC for data (see hexagonal architecture)

**For AI Agents:**
Follow this decision tree **before** creating any new React component. Desktop-only means simpler patterns without responsive complexity.

---

## 🖥️ Desktop-Only Reminder

**This Electron renderer is desktop-only:**
- ❌ No mobile breakpoints needed
- ❌ No touch gesture handling (use click/keyboard)
- ❌ No responsive layout switching
- ✅ Design for minimum 1024x768 window
- ✅ Support keyboard shortcuts
- ✅ Use desktop UI conventions
- ✅ Rich interactions and animations welcome