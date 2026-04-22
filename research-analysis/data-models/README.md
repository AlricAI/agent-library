# Data Models

> [← Back to Index](./index.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tech Invoice Forge - Data Models

[← Back to Index](./index.md) | [Master Plan](./master-plan.md) | [Architecture](./architecture.md)

---

## Overview

All data is stored locally in the browser using the native IndexedDB Web API. No data is sent to any server.

---

## TypeScript Type Definitions

### Sender

```typescript
// $lib/db/schema.ts

export interface Sender {
	id?: number;
	businessName: string;
	address: string;
	email: string;
	phone?: string;
	taxId?: string;
	logo?: Blob | null;
	isDefault: boolean;
	createdAt: Date;
	updatedAt: Date;
}

// Example
const sender: Sender = {
	id: 1,
	businessName: 'Acme Development LLC',
	address: '123 Tech Lane\nSan Francisco, CA 94105\nUSA',
	email: 'billing@acmedev.com',
	phone: '+1 (555) 123-4567',
	taxId: '12-3456789',
	logo: null,
	isDefault: true,
	createdAt: new Date('2026-01-15'),
	updatedAt: new Date('2026-02-01')
};
```

---

### Client

```typescript
export interface Client {
	id?: number;
	name: string;
	company?: string;
	address: string;
	email: string;
	phone?: string;
	notes?: string;
	createdAt: Date;
	updatedAt: Date;
}

// Example
const client: Client = {
	id: 1,
	name: 'John Smith',
	company: 'TechStartup Inc',
	address: '456 Innovation Blvd\nSuite 200\nNew York, NY 10001',
	email: 'john@techstartup.com',
	phone: '+1 (555) 987-6543',
	notes: 'Prefers invoices on the 1st of each month',
	createdAt: new Date('2026-01-20'),
	updatedAt: new Date('2026-01-20')
};
```

---

### Service Item

```typescript
export interface ServiceItem {
	id?: number;
	name: string;
	description: string;
	defaultRate: number;
	defaultUnit: Unit;
	taxRate: number;
	category?: string;
	createdAt: Date;
	updatedAt: Date;
}

export type Unit = 'hour' | 'day' | 'unit' | 'flat' | 'project' | 'month' | 'word' | 'page';

// Example
const service: ServiceItem = {
	id: 1,
	name: 'Frontend Development',
	description: 'React/Svelte component development and integration',
	defaultRate: 75.0,
	defaultUnit: 'hour',
	taxRate: 10,
	categ

*[truncated — see source for full prompt]*