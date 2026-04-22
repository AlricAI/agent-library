# COLUMN EDITOR

> ## Overview

`ColumnEditor` is a globally reusable drag-and-drop column management component built with `@dnd-kit`. It provides:

- ✅ Drag-to-reorder 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ColumnEditor Component Documentation

## Overview

`ColumnEditor` is a globally reusable drag-and-drop column management component built with `@dnd-kit`. It provides:

- ✅ Drag-to-reorder columns
- ✅ Show/hide column toggles
- ✅ Visual feedback for hidden columns
- ✅ Accessible keyboard navigation
- ✅ Customizable grid layout
- ✅ Generic TypeScript typing for any column structure

## Installation

The component is located at:
```
src/components/column-editor.tsx
```

No additional dependencies beyond what's already in package.json (`@dnd-kit/core`, `@dnd-kit/sortable`, `@dnd-kit/utilities`).

## Basic Usage

```tsx
import { ColumnEditor, type ColumnItem } from "@/components/column-editor";

function MyColumnsManager() {
  const [columns, setColumns] = useState<ColumnItem[]>([
    { id: "name", label: "Name", isVisible: true },
    { id: "email", label: "Email", isVisible: true },
    { id: "status", label: "Status", isVisible: false },
  ]);

  return (
    <ColumnEditor
      columns={columns}
      onReorder={(reorderedColumns) => setColumns(reorderedColumns)}
      onToggleVisibility={(columnId) => {
        setColumns((prev) =>
          prev.map((col) =>
            col.id === columnId ? { ...col, isVisible: !col.isVisible } : col
          )
        );
      }}
      minVisibleColumns={1}
    />
  );
}
```

## Advanced Usage with Generic Types

For custom column structures that extend `ColumnItem`:

```tsx
type CustomColumn = ColumnItem & {
  dataType: "string" | "number" | "date";
  sortable: boolean;
};

function MyCustomColumnsManager() {
  const [columns, setColumns] = useState<CustomColumn[]>([
    { id: "name", label: "Name", isVisible: true, dataType: "string", sortable: true },
    { id: "salary", label: "Salary", isVisible: true, dataType: "number", sortable: true },
  ]);

  return (
    <ColumnEditor<CustomColumn>
      columns={columns}
      onReorder={setColumns}
      onToggleVisibility={(columnId) => {
        setColumns((prev) =>
          p

*[truncated — see source for full prompt]*