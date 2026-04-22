---
name: Ui Ux
description: [← Back to Index](./index.
model: claude-sonnet-4-5
---
# Tech Invoice Forge - UI/UX Design

[← Back to Index](./index.md) | [Master Plan](./master-plan.md) | [Branding](./branding.md)

---

## Design Philosophy

### Core Principles

1. **Functional Minimalism** - Every element serves a purpose
2. **Professional Aesthetics** - Mature, trustworthy appearance
3. **Speed** - Minimal clicks to complete tasks
4. **Mobile-First** - Responsive design from the ground up
5. **Accessibility** - WCAG 2.1 AA compliance

### Visual Language

- **No gradients** - Flat, solid colors only
- **Subtle shadows** - For depth and hierarchy
- **Generous spacing** - Breathable, not cramped
- **Consistent radius** - 8px (var(--radius)) everywhere

---

## Layout Structure

### Main Application Layout

```
┌─────────────────────────────────────────────────────────────────┐
│ Header: Logo | Theme Toggle | Export | Settings                 │
├────────────────────────────────┬────────────────────────────────┤
│                                │                                │
│       Invoice Form             │       Preview Panel            │
│       (Scrollable)             │       (Fixed/Sticky)           │
│                                │                                │
│   ┌──────────────────────┐    │   ┌────────────────────────┐   │
│   │ Sender Section       │    │   │                        │   │
│   └──────────────────────┘    │   │                        │   │
│   ┌──────────────────────┐    │   │    PDF Preview         │   │
│   │ Client Section       │    │   │    (Live Update)       │   │
│   └──────────────────────┘    │   │                        │   │
│   ┌──────────────────────┐    │   │                        │   │
│   │ Invoice Details      │    │   │                        │   │
│   └──────────────────────┘    │   │                        │   │
│   ┌──────────────────────┐    │   └────────────────────────┘   │
│   │ Line Items           │    │                                │
│   └──────────────────────┘    │   ┌────────────────────────┐   │
│   ┌──────────────────────┐    │   │ Template | Download    │   │
│   │ Totals               │    │   └────────────────────────┘   │
│   └──────────────────────┘    │                                │
│   ┌──────────────────────┐    │                                │
│   │ Notes & Terms        │    │                                │
│   └──────────────────────┘    │                                │
│                                │                                │
└────────────────────────────────┴────────────────────────────────┘
```

### Mobile Layout (< 768px)

```
┌─────────────────────────────────┐
│ Header                          │
├─────────────────────────────────┤
│                                 │
│       Invoice Form              │
│       (Full Width)              │
│                                 │
│   ┌───────────────────────┐    │
│   │ Sender Section        │    │
│   └───────────────────────┘    │
│   ┌───────────────────────┐    │
│   │ Client Section        │    │
│   └───────────────────────┘    │
│   ...                           │
│                                 │
├─────────────────────────────────┤
│ ┌─────────────────────────────┐ │
│ │ Preview | Download          │ │ ← Sticky bottom bar
│ └─────────────────────────────┘ │
└─────────────────────────────────┘
```

---

## Component Specifications

### shadcn-svelte Components Used

| Component              | Usage                               |
| :--------------------- | :---------------------------------- |
| `Button`               | Actions, CTAs                       |
| `Input`                | Text inputs, numbers                |
| `Textarea`             | Multi-line text (address, notes)    |
| `Select`               | Dropdowns (currency, payment terms) |
| `Popover` + `Calendar` | Date picker                         |
| `Card`                 | Section containers                  |
| `Dialog`               | Modals (add client, settings)       |
| `Tabs`                 | Settings sections                   |
| `Table`                | Invoice history                     |
| `Tooltip`              | Help text, hints                    |
| `Badge`                | Status indicators                   |
| `Separator`            | Visual dividers                     |
| `ScrollArea`           | Scrollable containers               |
| `Sheet`                | Mobile slide-in panels              |

---

### Section Card Component

Wrapper for each form section (Sender, Client, etc.).

```html
<!-- SectionCard.svelte -->
<script lang="ts">
	interface Props {
		title: string;
		description?: string;
		collapsible?: boolean;
	}
	let { title, description, collapsible = false, children } = $props<Props>();
	let isOpen = $state(true);
</script>

<div class="rounded-lg border border-slate-700 bg-slate-800/50">
	<button class="flex w-full items-center justify-between p-4" onclick="{()" ="">
		collapsible && (isOpen = !isOpen)} >
		<div>
			<h2 class="text-lg font-semibold text-slate-50">{title}</h2>
			{#if description}
			<p class="text-sm text-slate-400">{description}</p>
			{/if}
		</div>
		{#if collapsible}
		<ChevronDown class="h-5 w-5 text-slate-400 transition-transform" class:rotate-180="{!isOpen}" />
		{/if}
	</button>

	{#if isOpen}
	<div class="border-t border-slate-700 p-4">{@render children?.()}</div>
	{/if}
</div>
```

---

### Form Field Layout

Two-column grid on desktop, single column on mobile.

```html
<!-- FormGrid.svelte -->
<div class="grid gap-4 sm:grid-cols-2">
	<slot />
</div>
```

**Field Structure:**

```html
<Form.Field {form} name="businessName">
	<Form.Control let:attrs>
		<Form.Label class="text-sm font-medium text-slate-300">
			Business Name
			<span class="text-red-400">*</span>
		</Form.Label>
		<input {...attrs} placeholder="Your business name" />
		<Form.FieldErrors class="text-sm text-red-400" />
	</Form.Control>
</Form.Field>
```

---

### Line Items Table

**Desktop View:**

```
┌──────────────────────────────────────────────────────────────┐
│ Description       │ Qty │ Unit │ Rate   │ Tax  │ Amount    │
├──────────────────────────────────────────────────────────────┤
│ Frontend Dev      │ 40  │ hour │ $75.00 │ 10%  │ $3,000.00 │
│ [x]               │     │      │        │      │           │
├──────────────────────────────────────────────────────────────┤
│ API Integration   │ 8   │ hour │ $85.00 │ 10%  │ $680.00   │
│ [x]               │     │      │        │      │           │
├──────────────────────────────────────────────────────────────┤
│ [ + Add Item ]                                               │
└──────────────────────────────────────────────────────────────┘
```

**Mobile View (Stacked Cards):**

```
┌────────────────────────────────┐
│ Frontend Development           │
│                               │
│ Qty: 40 hours @ $75.00        │
│ Tax: 10%                      │
│                               │
│ Amount: $3,000.00     [Edit] [x] │
└────────────────────────────────┘
```

---

### Totals Section

```
                           ┌─────────────────────┐
                           │ Subtotal   $3,680.00 │
                           │ Tax         $368.00 │
                           │ Discount     -$50.00 │
                           │─────────────────────│
                           │ Total Due  $3,998.00 │
                           └─────────────────────┘
```

**Implementation:**

```html
<div class="flex justify-end">
	<div class="w-64 space-y-2">
		<div class="flex justify-between text-slate-300">
			<span>Subtotal</span>
			<span class="font-mono">{formatCurrency(subtotal, currency)}</span>
		</div>
		{#if taxTotal > 0}
		<div class="flex justify-between text-slate-300">
			<span>Tax</span>
			<span class="font-mono">{formatCurrency(taxTotal, currency)}</span>
		</div>
		{/if} {#if discountAmount > 0}
		<div class="flex justify-between text-emerald-400">
			<span>Discount</span>
			<span class="font-mono">-{formatCurrency(discountAmount, currency)}</span>
		</div>
		{/if}
		<Separator />
		<div class="flex justify-between text-lg font-bold text-slate-50">
			<span>Total Due</span>
			<span class="font-mono">{formatCurrency(total, currency)}</span>
		</div>
	</div>
</div>
```

---

### Preview Panel

**Features:**

- PDF rendered in iframe
- Zoom controls
- Template switcher
- Action buttons

```html
<div class="sticky top-4 flex flex-col gap-4">
	<!-- Toolbar -->
	<div class="flex items-center justify-between">
		<select onValueChange="{setTemplate}">
			<SelectTrigger class="w-40">
				<SelectValue placeholder="Template" />
			</SelectTrigger>
			<SelectContent>
				<SelectItem value="modern">Modern</SelectItem>
				<SelectItem value="classic">Classic</SelectItem>
				<SelectItem value="tech">Tech</SelectItem>
				<SelectItem value="compact">Compact</SelectItem>
			</SelectContent>
		</select>

		<div class="flex items-center gap-2">
			<button variant="outline" size="icon" onclick="{zoomOut}">
				<ZoomOut class="h-4 w-4" />
			</button>
			<span class="text-sm text-slate-400">{zoom}%</span>
			<button variant="outline" size="icon" onclick="{zoomIn}">
				<ZoomIn class="h-4 w-4" />
			</button>
		</div>
	</div>

	<!-- Preview Frame -->
	<div
		class="overflow-hidden rounded-lg border border-slate-700 bg-white"
		style="height: calc(100vh - 200px);"
	>
		<iframe
			src="{previewUrl}"
			title="Invoice Preview"
			class="h-full w-full"
			style="transform: scale({zoom / 100}); transform-origin: top left;"
		/>
	</div>

	<!-- Actions -->
	<div class="flex gap-2">
		<button variant="outline" class="flex-1" onclick="{saveDraft}">
			<Save class="mr-2 h-4 w-4" />
			Save Draft
		</button>
		<button class="flex-1 bg-indigo-600 hover:bg-indigo-700" onclick="{downloadPDF}">
			<Download class="mr-2 h-4 w-4" />
			Download PDF
		</button>
	</div>
</div>
```

---

## Page Designs

### 1. Main Invoice Page

**Route:** `/`

**Layout:**

- Two-column on desktop (form + preview)
- Single column on mobile (form only, preview in bottom sheet)

**Key Elements:**

- Header with logo and actions
- Collapsible form sections
- Sticky preview panel
- Floating action buttons on mobile

---

### 2. Invoice History Page

**Route:** `/history`

**Layout:**

```
┌─────────────────────────────────────────────────────────────────┐
│ Invoice History                             [Search] [Filter ▼] │
├─────────────────────────────────────────────────────────────────┤
│ Invoice #    │ Client       │ Date       │ Total    │ Status   │
├─────────────────────────────────────────────────────────────────┤
│ INV-2026-001 │ Acme Corp    │ Feb 1, 26  │ $3,998   │ ● Draft  │
│ INV-2026-002 │ TechStart    │ Jan 28, 26 │ $1,250   │ ● Paid   │
│ INV-2026-003 │ WebAgency    │ Jan 15, 26 │ $5,400   │ ● Overdue│
├─────────────────────────────────────────────────────────────────┤
│ < Prev                                   Page 1 of 3      Next >│
└─────────────────────────────────────────────────────────────────┘
```

**Status Badges:**

- **Draft**: `bg-slate-600 text-slate-200`
- **Sent**: `bg-blue-600 text-blue-100`
- **Paid**: `bg-emerald-600 text-emerald-100`
- **Overdue**: `bg-red-600 text-red-100`

---

### 3. Settings Page

**Route:** `/settings`

**Layout:**

```
┌─────────────────────────────────────────────────────────────────┐
│ Settings                                                        │
├─────────────────────────────────────────────────────────────────┤
│ [Defaults] [Appearance] [Data]                                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ Invoice Defaults                                                │
│                                                                 │
│ Default Currency          [USD ▼]                               │
│ Default Payment Terms     [Net 30 ▼]                            │
│ Default Tax Rate          [10]%                                 │
│ Invoice Number Prefix     [INV]                                 │
│                                                                 │
│ [Save Changes]                                                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Interactive States

### Button States

| State    | Background   | Text        | Border | Shadow |
| :------- | :----------- | :---------- | :----- | :----- |
| Default  | `indigo-600` | `white`     | none   | sm     |
| Hover    | `indigo-700` | `white`     | none   | md     |
| Active   | `indigo-800` | `white`     | none   | none   |
| Disabled | `slate-600`  | `slate-400` | none   | none   |
| Loading  | `indigo-600` | spinner     | none   | sm     |

### Input States

| State    | Background  | Border       | Shadow   |
| :------- | :---------- | :----------- | :------- |
| Default  | `slate-900` | `slate-700`  | none     |
| Focus    | `slate-900` | `indigo-500` | ring     |
| Error    | `slate-900` | `red-500`    | ring-red |
| Disabled | `slate-800` | `slate-700`  | none     |

---

## Animations & Transitions

### Standard Transitions

```css
/* All interactive elements */
transition: all 150ms ease-in-out;
```

### Specific Animations

| Element            | Animation         | Duration   |
| :----------------- | :---------------- | :--------- |
| Page transitions   | Fade              | 200ms      |
| Modal open         | Scale + Fade      | 200ms      |
| Modal close        | Fade              | 150ms      |
| Collapsible expand | Height            | 200ms      |
| Toast appear       | Slide up + Fade   | 300ms      |
| Toast dismiss      | Slide down + Fade | 200ms      |
| Button loading     | Spin              | continuous |

**No jarring animations** - Smooth and professional.

---

## Responsive Breakpoints

```css
/* Tailwind defaults */
--sm: 640px; /* Small tablets */
--md: 768px; /* Tablets */
--lg: 1024px; /* Laptops */
--xl: 1280px; /* Desktops */
--2xl: 1536px; /* Large screens */
```

### Layout Adaptations

| Breakpoint | Form/Preview         | Columns | Font Size |
| :--------- | :------------------- | :------ | :-------- |
| < 768px    | Single column        | 1       | Base      |
| 768-1024px | Side by side (50/50) | 2       | Base      |
| > 1024px   | Side by side (55/45) | 2       | Base      |

---

## Empty States

### No Invoices Yet

```
┌────────────────────────────────────────┐
│                                        │
│        📄                              │
│                                        │
│   No invoices yet                      │
│                                        │
│   Create your first invoice in         │
│   seconds and start getting paid.      │
│                                        │
│   [Create Invoice]                     │
│                                        │
└────────────────────────────────────────┘
```

### No Saved Clients

```
┌────────────────────────────────────────┐
│                                        │
│   No saved clients                     │
│                                        │
│   Save a client to quickly fill        │
│   their details next time.             │
│                                        │
│   [Add Client]                         │
│                                        │
└────────────────────────────────────────┘
```

---

## Error States

### Form Validation Error

```html
<Form.Field {form} name="email">
	<Form.Control let:attrs>
		<Form.Label>Email</Form.Label>
		<input {...attrs} class="border-red-500 focus:ring-red-500" />
		<Form.FieldErrors class="mt-1 text-sm text-red-400">
			Please enter a valid email address
		</Form.FieldErrors>
	</Form.Control>
</Form.Field>
```

### PDF Generation Error

```html
<Alert variant="destructive">
	<AlertCircle class="h-4 w-4" />
	<AlertTitle>Error generating PDF</AlertTitle>
	<AlertDescription>
		There was a problem creating your invoice. Please check all required fields are filled and try
		again.
	</AlertDescription>
</Alert>
```

---

## Loading States

### PDF Preview Loading

```html
<div class="flex h-full items-center justify-center bg-slate-900">
	<div class="text-center">
		<Loader2 class="mx-auto h-8 w-8 animate-spin text-indigo-500" />
		<p class="mt-2 text-sm text-slate-400">Generating preview...</p>
	</div>
</div>
```

### Page Loading (SvelteKit)

```html
<!-- +layout.svelte -->
<script>
	import { navigating } from '$app/stores';
</script>

{#if $navigating}
<div class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/80">
	<Loader2 class="h-12 w-12 animate-spin text-indigo-500" />
</div>
{/if}
```

---

## Accessibility Considerations

### ARIA Labels

```html
<button aria-label="Download invoice as PDF">
	<Download class="h-4 w-4" />
</button>

<input aria-label="Invoice number" aria-describedby="invoice-number-help" />
<p id="invoice-number-help" class="sr-only">Format: INV-YEAR-SEQUENCE, e.g., INV-2026-0001</p>
```

### Focus Management

- Visible focus rings on all interactive elements
- Skip to main content link
- Modal focus trap
- Return focus to trigger after modal close

### Screen Reader Support

- Proper heading hierarchy (h1 → h2 → h3)
- Descriptive link text
- Alt text for images/icons
- Live regions for dynamic updates

---

## Related Documents

- [Branding](./branding.md) - Colors and typography
- [Features](./features.md) - Feature specifications
- [Architecture](./architecture.md) - Component structure