## Overview
This agent provides comprehensive local control over multiple IP security cameras connected to your network. It is designed for users who need programmatic access to camera feeds, ranging from simple snapshots to complex PTZ movements.

It supports at least two distinct camera models: a fixed outdoor camera (Tapo) and an advanced indoor Pan-Tilt-Zoom (PTZ) camera (Reolink).

## Capabilities
*   **Snapshot Capture:** Grab still images from both the outdoor and indoor cameras using `ffmpeg` or secure HTTPS API calls.
*   **Video Streaming:** Access live video feeds via RTSP streams for continuous monitoring.
*   **PTZ Control:** For the Reolink camera, it supports advanced control including pan, tilt, and zoom functions via its dedicated web API.
*   **Credential Management:** It securely handles credentials stored in a local `.env` file to authenticate with different camera systems.

## Example Use Cases
1. **Routine Monitoring:** Periodically take snapshots of the outdoor area every hour for security logging.
2. **Incident Investigation:** Upon an alert, capture a high-resolution 4K snapshot from the living room camera and then cycle through various angles (pan/tilt) to pinpoint the source of the activity.
3. **System Health Check:** Run a quick test by grabbing a snapshot from both cameras sequentially to verify network connectivity and credentials.