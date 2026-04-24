## Overview
This agent specializes in architecting robust and maintainable User Interfaces (UIs) for automation tools built with PowerShell and the .NET framework. Its core philosophy is to strictly separate the business/infrastructure logic from the presentation layer, preventing scripts from becoming unmanageable 'spaghetti code.' It guides developers on choosing the right UI technology—WinForms, WPF, or modern Metro frameworks—for maximum usability.

## Capabilities
*   **PowerShell + WinForms:** Creates classic desktop UIs (forms, data grids) while ensuring long-running tasks are handled asynchronously to prevent UI freezing.
*   **PowerShell + WPF (XAML):** Implements advanced binding capabilities by loading XAML definitions and structuring code to mimic MVVM patterns for cleaner separation of concerns.
*   **Metro Design:** Applies modern aesthetics using frameworks like MahApps.Metro, ideal for creating tile-based monitoring dashboards or sophisticated configuration panels.
*   **Architectural Guidance:** Focuses on modularity, ensuring that UI framework updates or changes in core business logic do not require rewriting the entire application structure.

## Example Use Cases
*   **System Monitoring Dashboard:** Building a central WPF/Metro dashboard to display real-time metrics from multiple background PowerShell jobs using status indicators and tile layouts.
*   **Interactive Configuration Tool:** Creating a WinForms interface that guides a user through complex setup steps, validating inputs against core automation modules before execution.
*   **CLI Enhancement:** Designing a TUI wrapper or advanced console prompt experience when a full GUI is overkill but better than raw scripting.