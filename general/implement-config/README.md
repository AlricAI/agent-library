# IMPLEMENT CONFIG

> This is a significant architectural upgrade.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
This is a significant architectural upgrade. By moving to a KV-backed configuration, you’re turning a static worker into a dynamic, self-managed platform.

Following your **Codex Senior Engineer** standards, I’ve designed the frontend using **Astro**, **React**, and **Shadcn UI** (Default Dark). The UI features a persistent sticky header with a settings trigger and a sidebar-driven configuration layout that maps directly to your URL structure.

### 1. The Architecture Visualized

### 2. Frontend: Configuration Layout & Sidebar

`src/layouts/ConfigLayout.astro` & `src/components/config/Sidebar.tsx`

```tsx
// src/components/config/ConfigSidebar.tsx
import React from "react";
import { cn } from "@/lib/utils";
import { Button } from "@/components/ui/button";
import { Settings, Shield, Cpu, Github, Activity } from "lucide-react";

const categories = [
  { name: "General", icon: Settings, href: "/config/general" },
  { name: "AI Models", icon: Cpu, href: "/config/ai" },
  { name: "Security", icon: Shield, href: "/config/security" },
  { name: "Integrations", icon: Github, href: "/config/integrations" },
  { name: "System", icon: Activity, href: "/config/system" },
];

export function ConfigSidebar({ activeCategory }: { activeCategory: string }) {
  return (
    <nav className="flex flex-col space-y-1 w-64 p-4 border-r bg-background/50 h-[calc(100vh-64px)]">
      {categories.map((item) => (
        <Button
          key={item.name}
          variant={
            activeCategory === item.name.toLowerCase() ? "secondary" : "ghost"
          }
          className={cn(
            "justify-start gap-2 w-full",
            activeCategory === item.name.toLowerCase() && "bg-secondary",
          )}
          asChild
        >
          <a href={item.href}>
            <item.icon className="h-4 w-4" />
            {item.name}
          </a>
        </Button>
      ))}
    </nav>
  );
}
```

### 3. Persistent Sticky Header

`src/components/layout/Header.tsx`

```tsx
import React 

*[truncated — see source for full prompt]*