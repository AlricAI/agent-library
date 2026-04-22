---
name: Design System
description: > **Version**: 1.0.0
> **Style**: Vibrant Fitness Energy
> **Last Updated**: 2024-12-24

---

## Table of Contents

1. [Design Philosophy](#1-design-p
model: claude-sonnet-4-5
---
# Cal AI Design System

> **Version**: 1.0.0
> **Style**: Vibrant Fitness Energy
> **Last Updated**: 2024-12-24

---

## Table of Contents

1. [Design Philosophy](#1-design-philosophy)
2. [Color System](#2-color-system)
3. [Typography](#3-typography)
4. [Spacing System](#4-spacing-system)
5. [Grid & Layout](#5-grid--layout)
6. [Border Radius](#6-border-radius)
7. [Shadows & Elevation](#7-shadows--elevation)
8. [Components](#8-components)
9. [Motion & Animation](#9-motion--animation)
10. [Responsive Design](#10-responsive-design)
11. [Iconography](#11-iconography)
12. [Imagery & Illustrations](#12-imagery--illustrations)
13. [Accessibility](#13-accessibility)
14. [Voice & Tone](#14-voice--tone)

---

## 1. Design Philosophy

### 1.1 Core Principles

| Principle | Description |
|-----------|-------------|
| **Energetic** | 활기차고 동기부여를 주는 비주얼. 사용자가 운동과 건강 관리에 열정을 느끼도록 |
| **Bold** | 대담한 타이포그래피와 선명한 컬러로 강렬한 첫인상 전달 |
| **Modern** | 최신 디자인 트렌드 (그라데이션, 글래스모피즘) 적극 활용 |
| **Intuitive** | 복잡한 영양 데이터를 직관적이고 이해하기 쉽게 시각화 |
| **Motivating** | 목표 달성과 진행 상황을 축하하고 격려하는 UX |

### 1.2 Brand Personality

```
- 활동적 (Active)
- 자신감 (Confident)
- 친근함 (Approachable)
- 혁신적 (Innovative)
- 신뢰성 (Trustworthy)
```

### 1.3 Design Keywords

```
Dynamic | Gradient | Bold | Energetic | Premium Dark | Fitness | Progress | Achievement
```

---

## 2. Color System

### 2.1 Core Palette

#### Primary Colors

| Name | HEX | RGB | Usage |
|------|-----|-----|-------|
| **Primary** | `#FF6B35` | `rgb(255, 107, 53)` | 주요 CTA, 강조 요소, 프로그레스 |
| **Primary Light** | `#FF8F5E` | `rgb(255, 143, 94)` | 호버 상태, 밝은 강조 |
| **Primary Dark** | `#E55A2B` | `rgb(229, 90, 43)` | 액티브 상태, 어두운 강조 |

#### Secondary Colors

| Name | HEX | RGB | Usage |
|------|-----|-----|-------|
| **Secondary** | `#F7C94B` | `rgb(247, 201, 75)` | 보조 강조, 성취 배지, 알림 |
| **Accent** | `#FF3366` | `rgb(255, 51, 102)` | 긴급 알림, 에너지 강조, 그라데이션 |

#### Background Colors

| Name | HEX | RGB | Usage |
|------|-----|-----|-------|
| **Background Dark** | `#1A1A2E` | `rgb(26, 26, 46)` | 메인 배경 |
| **Background Darker** | `#0F0F1A` | `rgb(15, 15, 26)` | 깊은 배경, 카드 내부 |
| **Surface** | `#252541` | `rgb(37, 37, 65)` | 카드, 모달, 오버레이 |
| **Surface Light** | `#2D2D4A` | `rgb(45, 45, 74)` | 호버 상태 배경 |

#### Text Colors

| Name | HEX | RGB | Usage |
|------|-----|-----|-------|
| **Text Primary** | `#FFFFFF` | `rgb(255, 255, 255)` | 주요 텍스트 |
| **Text Secondary** | `#A0A0B8` | `rgb(160, 160, 184)` | 보조 텍스트, 설명 |
| **Text Tertiary** | `#6B6B80` | `rgb(107, 107, 128)` | 비활성 텍스트, 힌트 |
| **Text Disabled** | `#4A4A5A` | `rgb(74, 74, 90)` | 비활성 상태 |

### 2.2 Semantic Colors

| Name | HEX | Usage |
|------|-----|-------|
| **Success** | `#22C55E` | 성공, 목표 달성, 완료 |
| **Warning** | `#F7C94B` | 경고, 주의 필요 |
| **Error** | `#EF4444` | 오류, 실패, 삭제 |
| **Info** | `#3B82F6` | 정보, 도움말 |

### 2.3 Macro Colors (영양소별)

| Macro | HEX | Usage |
|-------|-----|-------|
| **Protein** | `#FF6B35` | 단백질 표시 |
| **Carbs** | `#F7C94B` | 탄수화물 표시 |
| **Fat** | `#FF3366` | 지방 표시 |
| **Calories** | `#FFFFFF` | 칼로리 (그라데이션 배경에) |

### 2.4 Gradients

```css
/* Primary Gradient - 주요 버튼, 강조 요소 */
--gradient-primary: linear-gradient(135deg, #FF6B35, #FF3366);

/* Secondary Gradient - 보조 강조 */
--gradient-secondary: linear-gradient(135deg, #FF6B35, #F7C94B);

/* Full Spectrum - 특별 강조, 로고 */
--gradient-spectrum: linear-gradient(135deg, #FF6B35, #F7C94B, #FF3366);

/* Surface Gradient - 카드 배경 */
--gradient-surface: linear-gradient(135deg, #252541, #0F0F1A);

/* Glow Gradient - 배경 효과 */
--gradient-glow-primary: radial-gradient(circle, rgba(255, 107, 53, 0.15) 0%, transparent 50%);
--gradient-glow-accent: radial-gradient(circle, rgba(255, 51, 102, 0.15) 0%, transparent 50%);
```

### 2.5 CSS Variables

```css
:root {
  /* Primary */
  --color-primary: #FF6B35;
  --color-primary-light: #FF8F5E;
  --color-primary-dark: #E55A2B;

  /* Secondary */
  --color-secondary: #F7C94B;
  --color-accent: #FF3366;

  /* Background */
  --color-bg-dark: #1A1A2E;
  --color-bg-darker: #0F0F1A;
  --color-surface: #252541;
  --color-surface-light: #2D2D4A;

  /* Text */
  --color-text: #FFFFFF;
  --color-text-secondary: #A0A0B8;
  --color-text-tertiary: #6B6B80;
  --color-text-disabled: #4A4A5A;

  /* Semantic */
  --color-success: #22C55E;
  --color-warning: #F7C94B;
  --color-error: #EF4444;
  --color-info: #3B82F6;

  /* Border */
  --color-border: rgba(255, 255, 255, 0.05);
  --color-border-light: rgba(255, 255, 255, 0.1);
  --color-border-primary: rgba(255, 107, 53, 0.3);
}
```

---

## 3. Typography

### 3.1 Font Family

```css
/* Primary Font - Headlines & Body */
--font-primary: 'Outfit', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;

/* Mono Font - Numbers, Data, Code */
--font-mono: 'JetBrains Mono', 'SF Mono', 'Consolas', monospace;
```

**Font Loading:**
```html
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

### 3.2 Type Scale

| Name | Size | Line Height | Weight | Usage |
|------|------|-------------|--------|-------|
| **Display** | `4.5rem` (72px) | 1.1 | 900 | Hero 헤드라인 |
| **H1** | `3rem` (48px) | 1.2 | 800 | 섹션 타이틀 |
| **H2** | `2.25rem` (36px) | 1.25 | 700 | 서브섹션 타이틀 |
| **H3** | `1.5rem` (24px) | 1.3 | 700 | 카드 타이틀 |
| **H4** | `1.25rem` (20px) | 1.4 | 600 | 소제목 |
| **Body Large** | `1.25rem` (20px) | 1.6 | 400 | 리드 텍스트 |
| **Body** | `1rem` (16px) | 1.6 | 400 | 본문 |
| **Body Small** | `0.875rem` (14px) | 1.5 | 400 | 보조 텍스트 |
| **Caption** | `0.75rem` (12px) | 1.4 | 500 | 캡션, 라벨 |
| **Overline** | `0.75rem` (12px) | 1.4 | 600 | 뱃지, 태그 |

### 3.3 Font Weights

| Weight | Value | Usage |
|--------|-------|-------|
| Regular | 400 | 본문 텍스트 |
| Medium | 500 | 강조 본문 |
| SemiBold | 600 | 서브헤딩, 버튼 |
| Bold | 700 | 카드 타이틀, 중요 정보 |
| ExtraBold | 800 | 섹션 타이틀 |
| Black | 900 | Hero 타이틀, 숫자 강조 |

### 3.4 Text Styles

```css
/* Display - Hero Headlines */
.text-display {
  font-size: 4.5rem;
  font-weight: 900;
  line-height: 1.1;
  text-transform: uppercase;
  letter-spacing: -0.02em;
}

/* Gradient Text */
.text-gradient {
  background: linear-gradient(135deg, #FF6B35, #F7C94B, #FF3366);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Stats Number */
.text-stat {
  font-family: var(--font-primary);
  font-size: 3rem;
  font-weight: 900;
  background: linear-gradient(135deg, #FF6B35, #F7C94B);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* Label / Overline */
.text-label {
  font-size: 0.875rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 2px;
  color: var(--color-text-secondary);
}

/* Data Display (Mono) */
.text-data {
  font-family: var(--font-mono);
  font-weight: 600;
}
```

---

## 4. Spacing System

### 4.1 Base Unit

**Base**: `4px`

모든 간격은 4px 단위의 배수로 구성됩니다.

### 4.2 Spacing Scale

| Token | Value | Pixels | Usage |
|-------|-------|--------|-------|
| `--space-0` | 0 | 0px | 없음 |
| `--space-1` | 0.25rem | 4px | 아이콘-텍스트 간격 |
| `--space-2` | 0.5rem | 8px | 인라인 요소 간격 |
| `--space-3` | 0.75rem | 12px | 작은 컴포넌트 내부 |
| `--space-4` | 1rem | 16px | 기본 패딩 |
| `--space-5` | 1.25rem | 20px | 카드 내부 간격 |
| `--space-6` | 1.5rem | 24px | 섹션 내 그룹 간격 |
| `--space-8` | 2rem | 32px | 컴포넌트 사이 |
| `--space-10` | 2.5rem | 40px | 큰 요소 간격 |
| `--space-12` | 3rem | 48px | 섹션 내부 패딩 |
| `--space-16` | 4rem | 64px | 섹션 간격 |
| `--space-20` | 5rem | 80px | 큰 섹션 간격 |
| `--space-24` | 6rem | 96px | 페이지 섹션 패딩 |
| `--space-32` | 8rem | 128px | 히어로 섹션 패딩 |

### 4.3 Component Spacing

```css
/* Card Padding */
--card-padding-sm: var(--space-4);    /* 16px */
--card-padding-md: var(--space-6);    /* 24px */
--card-padding-lg: var(--space-8);    /* 32px */

/* Button Padding */
--btn-padding-sm: 0.5rem 1rem;        /* 8px 16px */
--btn-padding-md: 0.875rem 2rem;      /* 14px 32px */
--btn-padding-lg: 1rem 2.5rem;        /* 16px 40px */

/* Input Padding */
--input-padding: 0.875rem 1rem;       /* 14px 16px */

/* Section Padding */
--section-padding-y: var(--space-24); /* 96px */
--section-padding-x: var(--space-8);  /* 32px */
```

---

## 5. Grid & Layout

### 5.1 Container

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--space-8);
}

.container-sm {
  max-width: 800px;
}

.container-lg {
  max-width: 1400px;
}
```

### 5.2 Grid System

**12-Column Grid**

```css
.grid {
  display: grid;
  gap: var(--space-8);
}

/* Common Layouts */
.grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
.grid-cols-3 { grid-template-columns: repeat(3, 1fr); }
.grid-cols-4 { grid-template-columns: repeat(4, 1fr); }

/* Feature Cards Grid */
.features-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

/* Stats Grid */
.stats-grid {
  display: flex;
  justify-content: center;
  gap: 4rem;
}
```

### 5.3 Flex Utilities

```css
.flex { display: flex; }
.flex-col { flex-direction: column; }
.items-center { align-items: center; }
.justify-center { justify-content: center; }
.justify-between { justify-content: space-between; }
.gap-2 { gap: var(--space-2); }
.gap-4 { gap: var(--space-4); }
.gap-8 { gap: var(--space-8); }
```

---

## 6. Border Radius

### 6.1 Radius Scale

| Token | Value | Usage |
|-------|-------|-------|
| `--radius-none` | 0 | 각진 요소 |
| `--radius-sm` | 8px | 작은 버튼, 뱃지 |
| `--radius-md` | 12px | 입력 필드, 작은 카드 |
| `--radius-lg` | 16px | 드롭다운, 모달 |
| `--radius-xl` | 24px | 카드 |
| `--radius-2xl` | 32px | 큰 카드, CTA 박스 |
| `--radius-3xl` | 36px | 폰 목업 |
| `--radius-full` | 9999px | 버튼 (pill), 뱃지, 아바타 |

### 6.2 Usage Guidelines

```css
/* Buttons - Pill Style */
.btn {
  border-radius: var(--radius-full);
}

/* Cards */
.card {
  border-radius: var(--radius-xl);
}

/* Input Fields */
.input {
  border-radius: var(--radius-md);
}

/* Badges */
.badge {
  border-radius: var(--radius-full);
}

/* Modal */
.modal {
  border-radius: var(--radius-2xl);
}
```

---

## 7. Shadows & Elevation

### 7.1 Shadow Scale

```css
/* Subtle - 미세한 깊이감 */
--shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.15);

/* Default - 카드, 드롭다운 */
--shadow-md: 0 8px 24px rgba(0, 0, 0, 0.2);

/* Elevated - 모달, 팝오버 */
--shadow-lg: 0 20px 60px rgba(0, 0, 0, 0.4);

/* High - 폰 목업, 메인 비주얼 */
--shadow-xl: 0 40px 80px rgba(0, 0, 0, 0.5);
```

### 7.2 Glow Shadows (Brand)

```css
/* Primary Glow - CTA 버튼 */
--shadow-glow-primary: 0 8px 32px rgba(255, 107, 53, 0.4);
--shadow-glow-primary-hover: 0 12px 40px rgba(255, 107, 53, 0.5);

/* Accent Glow */
--shadow-glow-accent: 0 8px 32px rgba(255, 51, 102, 0.4);

/* Card Hover Glow */
--shadow-card-hover: 0 20px 60px rgba(255, 107, 53, 0.2);
```

### 7.3 Usage

```css
/* Primary Button */
.btn-primary {
  box-shadow: var(--shadow-glow-primary);
}

.btn-primary:hover {
  box-shadow: var(--shadow-glow-primary-hover);
}

/* Card */
.card {
  box-shadow: var(--shadow-md);
}

.card:hover {
  box-shadow: var(--shadow-card-hover);
}
```

---

## 8. Components

### 8.1 Buttons

#### Variants

| Variant | Usage |
|---------|-------|
| **Primary** | 주요 CTA, 폼 제출 |
| **Ghost** | 보조 액션, 취소 |
| **Secondary** | 중요도 낮은 액션 |
| **Danger** | 삭제, 위험한 액션 |

#### Primary Button

```css
.btn-primary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.875rem 2rem;
  background: linear-gradient(135deg, var(--color-primary), var(--color-accent));
  color: white;
  font-family: var(--font-primary);
  font-size: 0.875rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  border: none;
  border-radius: var(--radius-full);
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: var(--shadow-glow-primary);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-glow-primary-hover);
}

.btn-primary:active {
  transform: translateY(0);
}

.btn-primary:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
}
```

#### Ghost Button

```css
.btn-ghost {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.875rem 2rem;
  background: transparent;
  color: var(--color-text);
  font-family: var(--font-primary);
  font-size: 0.875rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: var(--radius-full);
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-ghost:hover {
  border-color: var(--color-primary);
  color: var(--color-primary);
}
```

#### Button Sizes

```css
.btn-sm {
  padding: 0.5rem 1rem;
  font-size: 0.75rem;
}

.btn-md {
  padding: 0.875rem 2rem;
  font-size: 0.875rem;
}

.btn-lg {
  padding: 1rem 2.5rem;
  font-size: 1rem;
}
```

### 8.2 Cards

#### Base Card

```css
.card {
  background: linear-gradient(135deg, var(--color-surface), var(--color-bg-darker));
  border: 1px solid var(--color-border);
  border-radius: var(--radius-xl);
  padding: var(--space-6);
  position: relative;
  overflow: hidden;
  transition: all 0.4s ease;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-card-hover);
}

/* Top Accent Bar (on hover) */
.card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(90deg, var(--color-primary), var(--color-accent));
  opacity: 0;
  transition: opacity 0.3s ease;
}

.card:hover::before {
  opacity: 1;
}
```

#### Feature Card

```css
.feature-card {
  composes: card;
  text-align: left;
}

.feature-card__icon {
  font-size: 3rem;
  margin-bottom: var(--space-6);
}

.feature-card__title {
  font-size: 1.375rem;
  font-weight: 700;
  margin-bottom: var(--space-3);
  color: var(--color-text);
}

.feature-card__description {
  color: var(--color-text-secondary);
  line-height: 1.6;
}
```

#### Stat Card (Macro Pill)

```css
.macro-pill {
  background: var(--color-surface);
  border-radius: var(--radius-md);
  padding: var(--space-3);
  text-align: center;
  flex: 1;
  min-width: 60px;
}

.macro-pill__icon {
  font-size: 1.25rem;
  margin-bottom: var(--space-1);
}

.macro-pill__value {
  font-weight: 700;
  font-size: 0.875rem;
  color: var(--color-text);
}

.macro-pill__label {
  font-size: 0.625rem;
  color: var(--color-text-secondary);
  text-transform: uppercase;
  letter-spacing: 1px;
}
```

### 8.3 Inputs

```css
.input {
  width: 100%;
  padding: 0.875rem 1rem;
  background: var(--color-bg-darker);
  border: 2px solid var(--color-border-light);
  border-radius: var(--radius-md);
  color: var(--color-text);
  font-family: var(--font-primary);
  font-size: 1rem;
  transition: all 0.3s ease;
}

.input::placeholder {
  color: var(--color-text-tertiary);
}

.input:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 4px rgba(255, 107, 53, 0.1);
}

.input:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

/* Input with error */
.input--error {
  border-color: var(--color-error);
}

.input--error:focus {
  box-shadow: 0 0 0 4px rgba(239, 68, 68, 0.1);
}
```

### 8.4 Badges

```css
.badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1.25rem;
  background: rgba(255, 107, 53, 0.2);
  border: 1px solid rgba(255, 107, 53, 0.3);
  border-radius: var(--radius-full);
  font-size: 0.875rem;
  font-weight: 600;
  color: var(--color-primary);
}

/* Badge Variants */
.badge--success {
  background: rgba(34, 197, 94, 0.2);
  border-color: rgba(34, 197, 94, 0.3);
  color: var(--color-success);
}

.badge--warning {
  background: rgba(247, 201, 75, 0.2);
  border-color: rgba(247, 201, 75, 0.3);
  color: var(--color-warning);
}

.badge--error {
  background: rgba(239, 68, 68, 0.2);
  border-color: rgba(239, 68, 68, 0.3);
  color: var(--color-error);
}
```

### 8.5 Progress Components

#### Progress Ring (Circular)

```css
.progress-ring {
  position: relative;
  width: 150px;
  height: 150px;
}

.progress-ring svg {
  transform: rotate(-90deg);
}

.progress-ring__bg {
  fill: none;
  stroke: var(--color-surface);
  stroke-width: 10;
}

.progress-ring__fill {
  fill: none;
  stroke: url(#gradient-primary);
  stroke-width: 10;
  stroke-linecap: round;
  stroke-dasharray: 408; /* 2 * PI * radius */
  transition: stroke-dashoffset 0.5s ease;
}

.progress-ring__center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

.progress-ring__value {
  font-size: 2rem;
  font-weight: 800;
  color: var(--color-text);
}

.progress-ring__label {
  font-size: 0.75rem;
  color: var(--color-text-secondary);
}
```

#### Progress Bar (Linear)

```css
.progress-bar {
  width: 100%;
  height: 8px;
  background: var(--color-bg-darker);
  border-radius: var(--radius-full);
  overflow: hidden;
}

.progress-bar__fill {
  height: 100%;
  background: linear-gradient(90deg, var(--color-primary), var(--color-accent));
  border-radius: var(--radius-full);
  transition: width 0.5s ease;
}

/* Macro-specific colors */
.progress-bar__fill--protein {
  background: var(--color-primary);
}

.progress-bar__fill--carbs {
  background: var(--color-secondary);
}

.progress-bar__fill--fat {
  background: var(--color-accent);
}
```

### 8.6 Navigation

#### Header

```css
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: rgba(26, 26, 46, 0.9);
  backdrop-filter: blur(20px);
  padding: 1rem 2rem;
}

.header__nav {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header__logo {
  font-size: 1.75rem;
  font-weight: 900;
  background: linear-gradient(135deg, var(--color-primary), var(--color-accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.header__links {
  display: flex;
  gap: 2rem;
  list-style: none;
}

.header__link {
  color: var(--color-text-secondary);
  font-weight: 600;
  text-decoration: none;
  transition: color 0.3s ease;
}

.header__link:hover {
  color: var(--color-primary);
}
```

#### Bottom Navigation (Mobile)

```css
.bottom-nav {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: var(--color-surface);
  border-top: 1px solid var(--color-border);
  padding: 0.75rem 1rem;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.bottom-nav__item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.25rem;
  color: var(--color-text-secondary);
  text-decoration: none;
  font-size: 0.625rem;
  transition: color 0.3s ease;
}

.bottom-nav__item--active {
  color: var(--color-primary);
}

.bottom-nav__icon {
  font-size: 1.5rem;
}
```

### 8.7 Modal

```css
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(15, 15, 26, 0.8);
  backdrop-filter: blur(8px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 200;
}

.modal {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-2xl);
  padding: var(--space-8);
  max-width: 500px;
  width: 90%;
  max-height: 90vh;
  overflow-y: auto;
  box-shadow: var(--shadow-xl);
}

.modal__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: var(--space-6);
}

.modal__title {
  font-size: 1.5rem;
  font-weight: 700;
}

.modal__close {
  background: none;
  border: none;
  color: var(--color-text-secondary);
  font-size: 1.5rem;
  cursor: pointer;
  transition: color 0.3s ease;
}

.modal__close:hover {
  color: var(--color-text);
}
```

---

## 9. Motion & Animation

### 9.1 Timing Functions

```css
--ease-default: cubic-bezier(0.4, 0, 0.2, 1);
--ease-in: cubic-bezier(0.4, 0, 1, 1);
--ease-out: cubic-bezier(0, 0, 0.2, 1);
--ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
--ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
```

### 9.2 Duration

| Token | Value | Usage |
|-------|-------|-------|
| `--duration-fast` | 150ms | 즉각적인 피드백 (호버) |
| `--duration-normal` | 300ms | 기본 트랜지션 |
| `--duration-slow` | 500ms | 복잡한 애니메이션 |
| `--duration-slower` | 800ms | 페이지 전환 |

### 9.3 Common Animations

```css
/* Fade In */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* Fade In Up */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Scale In */
@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

/* Pulse (for loading indicators) */
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

/* Shimmer (for skeleton loaders) */
@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

/* Float (for decorative elements) */
@keyframes float {
  0%, 100% { transform: translate(0, 0); }
  50% { transform: translate(30px, -30px); }
}
```

### 9.4 Transition Classes

```css
.transition-all {
  transition: all var(--duration-normal) var(--ease-default);
}

.transition-colors {
  transition: color var(--duration-normal) var(--ease-default),
              background-color var(--duration-normal) var(--ease-default),
              border-color var(--duration-normal) var(--ease-default);
}

.transition-transform {
  transition: transform var(--duration-normal) var(--ease-default);
}

.transition-opacity {
  transition: opacity var(--duration-normal) var(--ease-default);
}
```

### 9.5 Hover Effects

```css
/* Lift on hover */
.hover-lift {
  transition: transform var(--duration-normal) var(--ease-default),
              box-shadow var(--duration-normal) var(--ease-default);
}

.hover-lift:hover {
  transform: translateY(-8px);
}

/* Scale on hover */
.hover-scale {
  transition: transform var(--duration-normal) var(--ease-default);
}

.hover-scale:hover {
  transform: scale(1.05);
}

/* Glow on hover */
.hover-glow:hover {
  box-shadow: var(--shadow-glow-primary);
}
```

---

## 10. Responsive Design

### 10.1 Breakpoints

| Name | Min Width | Max Width | Target |
|------|-----------|-----------|--------|
| **xs** | 0 | 479px | 소형 모바일 |
| **sm** | 480px | 639px | 모바일 |
| **md** | 640px | 767px | 대형 모바일 |
| **lg** | 768px | 1023px | 태블릿 |
| **xl** | 1024px | 1279px | 소형 데스크톱 |
| **2xl** | 1280px | ∞ | 대형 데스크톱 |

### 10.2 CSS Variables for Breakpoints

```css
/* Mobile First Approach */
--breakpoint-sm: 480px;
--breakpoint-md: 640px;
--breakpoint-lg: 768px;
--breakpoint-xl: 1024px;
--breakpoint-2xl: 1280px;
```

### 10.3 Media Query Mixins (SCSS)

```scss
@mixin mobile {
  @media (max-width: 639px) { @content; }
}

@mixin tablet {
  @media (min-width: 640px) and (max-width: 1023px) { @content; }
}

@mixin desktop {
  @media (min-width: 1024px) { @content; }
}

@mixin responsive($breakpoint) {
  @media (min-width: $breakpoint) { @content; }
}
```

### 10.4 Responsive Typography

```css
/* Mobile (default) */
.text-display {
  font-size: 2.5rem;
}

/* Tablet */
@media (min-width: 768px) {
  .text-display {
    font-size: 3.5rem;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .text-display {
    font-size: 4.5rem;
  }
}
```

### 10.5 Responsive Grid

```css
.features-grid {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: 1fr;
}

@media (min-width: 640px) {
  .features-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .features-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
  }
}
```

---

## 11. Iconography

### 11.1 Icon Style

- **Style**: Filled 또는 Outlined (일관성 유지)
- **Size**: 24px (기본), 20px (작은), 32px (큰)
- **Color**: 컨텍스트에 맞는 색상 사용

### 11.2 Recommended Icon Libraries

1. **Lucide Icons** (Recommended) - `npm install lucide-react`
2. **Heroicons** - `npm install @heroicons/react`
3. **Phosphor Icons** - `npm install phosphor-react`

### 11.3 Icon Sizes

| Size | Pixels | Usage |
|------|--------|-------|
| `xs` | 16px | 인라인 아이콘, 뱃지 |
| `sm` | 20px | 버튼 내 아이콘 |
| `md` | 24px | 기본 아이콘 |
| `lg` | 32px | 강조 아이콘 |
| `xl` | 48px | 피처 아이콘 |

### 11.4 Feature Icons (Emoji)

현재 디자인에서는 피처 카드에 이모지를 사용합니다:

| Feature | Emoji | Usage |
|---------|-------|-------|
| Camera/Photo | 📸 | 사진 촬영, 음식 스캔 |
| Target | 🎯 | 목표, 정확성 |
| Muscle | 💪 | 운동, 피트니스 |
| Chart | 📊 | 통계, 분석 |
| Fire | 🔥 | 칼로리, 에너지 |
| Trophy | 🏆 | 성취, 목표 달성 |
| Food | 🥩🍚🥑 | 매크로 영양소 |

---

## 12. Imagery & Illustrations

### 12.1 Photography Style

- **톤**: 밝고 에너지 넘치는
- **주제**: 건강한 음식, 활동적인 라이프스타일
- **조명**: 자연광 또는 밝은 스튜디오 조명
- **색감**: 채도가 높고 선명한

### 12.2 Image Treatment

```css
/* 이미지 컨테이너 */
.image-container {
  border-radius: var(--radius-lg);
  overflow: hidden;
}

/* 그라데이션 오버레이 */
.image-overlay {
  background: linear-gradient(
    to bottom,
    transparent 0%,
    rgba(15, 15, 26, 0.8) 100%
  );
}
```

### 12.3 Background Effects

```css
/* Glow Background Pattern */
.bg-pattern {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background:
    radial-gradient(circle at 20% 80%, rgba(255, 107, 53, 0.15) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(255, 51, 102, 0.15) 0%, transparent 50%);
  pointer-events: none;
  z-index: 0;
}
```

---

## 13. Accessibility

### 13.1 Color Contrast

모든 텍스트는 WCAG 2.1 AA 기준을 충족해야 합니다:
- **일반 텍스트**: 최소 4.5:1 대비율
- **큰 텍스트 (18px+ bold, 24px+)**: 최소 3:1 대비율

| Foreground | Background | Ratio | Pass |
|------------|------------|-------|------|
| `#FFFFFF` | `#1A1A2E` | 13.5:1 | AAA |
| `#A0A0B8` | `#1A1A2E` | 6.2:1 | AA |
| `#FF6B35` | `#1A1A2E` | 4.8:1 | AA |

### 13.2 Focus States

```css
/* Focus Ring */
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

/* Button Focus */
.btn:focus-visible {
  box-shadow:
    var(--shadow-glow-primary),
    0 0 0 4px rgba(255, 107, 53, 0.3);
}

/* Input Focus */
.input:focus-visible {
  border-color: var(--color-primary);
  box-shadow: 0 0 0 4px rgba(255, 107, 53, 0.1);
}
```

### 13.3 Touch Targets

- **최소 터치 영역**: 44px x 44px
- **버튼 간 간격**: 최소 8px

### 13.4 Screen Reader

```html
<!-- Skip Link -->
<a href="#main-content" class="sr-only focus:not-sr-only">
  Skip to main content
</a>

<!-- ARIA Labels -->
<button aria-label="Open menu">
  <MenuIcon />
</button>

<!-- Progress Announcements -->
<div role="progressbar" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100">
  75% complete
</div>
```

### 13.5 Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 14. Voice & Tone

### 14.1 Brand Voice

| Attribute | Description | Example |
|-----------|-------------|---------|
| **Energetic** | 활기차고 동기부여하는 | "Fuel Your Gains!" |
| **Direct** | 간결하고 명확한 | "Snap. Analyze. Conquer." |
| **Encouraging** | 격려하고 지지하는 | "You're crushing it!" |
| **Confident** | 자신감 있는 | "The smartest way to track" |

### 14.2 Microcopy Examples

| Context | Copy |
|---------|------|
| **CTA Button** | "Start Free Trial", "Get Started" |
| **Empty State** | "Ready to track your first meal?" |
| **Success** | "Awesome! Meal logged successfully" |
| **Error** | "Oops! Something went wrong. Try again." |
| **Loading** | "Analyzing your meal..." |
| **Goal Met** | "You crushed your protein goal!" |

### 14.3 Capitalization

- **Headlines**: UPPERCASE 또는 Title Case
- **Buttons**: UPPERCASE
- **Body**: Sentence case
- **Labels**: UPPERCASE (작은 크기)

---

## Quick Reference

### CSS Variables 전체 목록

```css
:root {
  /* Colors */
  --color-primary: #FF6B35;
  --color-primary-light: #FF8F5E;
  --color-primary-dark: #E55A2B;
  --color-secondary: #F7C94B;
  --color-accent: #FF3366;
  --color-bg-dark: #1A1A2E;
  --color-bg-darker: #0F0F1A;
  --color-surface: #252541;
  --color-surface-light: #2D2D4A;
  --color-text: #FFFFFF;
  --color-text-secondary: #A0A0B8;
  --color-text-tertiary: #6B6B80;
  --color-text-disabled: #4A4A5A;
  --color-success: #22C55E;
  --color-warning: #F7C94B;
  --color-error: #EF4444;
  --color-info: #3B82F6;
  --color-border: rgba(255, 255, 255, 0.05);
  --color-border-light: rgba(255, 255, 255, 0.1);
  --color-border-primary: rgba(255, 107, 53, 0.3);

  /* Typography */
  --font-primary: 'Outfit', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;

  /* Spacing */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-5: 1.25rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-10: 2.5rem;
  --space-12: 3rem;
  --space-16: 4rem;
  --space-20: 5rem;
  --space-24: 6rem;
  --space-32: 8rem;

  /* Border Radius */
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  --radius-2xl: 32px;
  --radius-3xl: 36px;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.15);
  --shadow-md: 0 8px 24px rgba(0, 0, 0, 0.2);
  --shadow-lg: 0 20px 60px rgba(0, 0, 0, 0.4);
  --shadow-xl: 0 40px 80px rgba(0, 0, 0, 0.5);
  --shadow-glow-primary: 0 8px 32px rgba(255, 107, 53, 0.4);
  --shadow-glow-primary-hover: 0 12px 40px rgba(255, 107, 53, 0.5);

  /* Animation */
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 500ms;
  --ease-default: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);

  /* Breakpoints */
  --breakpoint-sm: 480px;
  --breakpoint-md: 640px;
  --breakpoint-lg: 768px;
  --breakpoint-xl: 1024px;
  --breakpoint-2xl: 1280px;
}
```

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2024-12-24 | Initial design system based on Vibrant Fitness Energy style |

---

*This design system is a living document and will be updated as the Cal AI product evolves.*