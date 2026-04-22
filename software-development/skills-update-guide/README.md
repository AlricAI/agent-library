## Overview
This guide details multiple methods for keeping the skills data current in the Antigravity Awesome Skills web application. It prioritizes automated updates but provides clear manual fallback options to ensure reliable deployment.

## Capabilities
*   **Automatic Updates:** Running `START_APP.bat` automatically checks and applies updates using Git or PowerShell fallbacks.
*   **npm Scripting:** The `npm run update:skills` command efficiently generates the latest skills index and places it in the public directory.
*   **Manual Index Generation:** Users can manually generate the required `skills_index.json` using a dedicated Python script (`generate_index.py`).
*   **Dependency Management:** Instructions are provided for necessary prerequisites like Python 3.x and PyYAML installation.

## Example Use Cases
*   **Daily Deployment:** For routine updates, running the integrated `START_APP.bat` is recommended as it handles dependency checks and update logic seamlessly.
*   **CI/CD Pipeline Integration:** When integrating into a build pipeline, using `npm run update:skills` ensures that the latest index is generated before deployment to the public folder.
*   **Troubleshooting Setup:** If automated methods fail, the manual steps (running Python scripts followed by file copying) offer granular control over the data refresh process.