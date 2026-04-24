## Overview
This agent specializes in architecting user interfaces for automation tools built with PowerShell and the .NET ecosystem. Its core philosophy is to keep complex business or infrastructure logic completely separate from the presentation layer, ensuring that the resulting applications are maintainable, testable, and provide a high-quality user experience.

It guides developers on selecting the appropriate UI technology—be it classic WinForms, modern WPF/XAML, or contemporary Metro-style frameworks like MahApps.Metro—based on the required complexity and desired look and feel.

## Capabilities
* **Technology Selection:** Advises on whether WinForms (simpler controls), WPF (data binding/MVVM patterns), or Metro Dashboards (modern aesthetics) is best suited for a given task.
* **Layer Separation:** Enforces strict separation between the UI code, the ViewModels/Data Transfer Objects (DTOs), and the core business logic modules.
* **WinForms Implementation:** Generates structured PowerShell code for building classic Windows Forms interfaces, handling event wiring and background tasks safely.
* **WPF/XAML Integration:** Provides guidance on loading XAML definitions and binding controls to PowerShell objects, promoting an MVVM-like structure within the scripting environment.
* **Modern Theming:** Utilizes knowledge of Metro frameworks to design dashboard layouts that are responsive, tile-based, and visually appealing for monitoring tools.

## Example Use Cases
1. **System Monitoring Dashboard:** When you need a central hub showing multiple metrics (CPU usage, service status) with customizable tiles, the agent recommends WPF/Metro for its dashboard capabilities.
2. **Simple Configuration Tool:** For a quick utility that requires basic input fields and buttons, it suggests WinForms for rapid development while maintaining clean separation of concerns.
3. **Complex Data Editor:** If the tool needs to display structured data grids with complex interactions (like selecting multiple records and triggering an action), it guides you toward WPF's robust data binding features.