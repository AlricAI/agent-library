# Reolink

> You have access to two WiFi cameras on the local network.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Home Cameras — Agent Instructions

You have access to two WiFi cameras on the local network. You can grab snapshots, record video, and control the indoor camera's pan/tilt/zoom.

**Credentials** are stored in `sms-bot/.env.local` (gitignored):
- `REOLINK_IP`, `REOLINK_USER`, `REOLINK_PASS` — Reolink E1 Zoom
- `TAPO_IP`, `TAPO_USER`, `TAPO_PASS` — Tapo C560WS

---

## Camera 1: Tapo C560WS (Outdoor)

- **IP:** `$TAPO_IP`
- **Credentials:** `$TAPO_USER` / `$TAPO_PASS`

**Grab a snapshot:**
```bash
ffmpeg -rtsp_transport tcp \
  -i "rtsp://${TAPO_USER//@/%40}:${TAPO_PASS}@${TAPO_IP}:554/stream1" \
  -frames:v 1 -update 1 -y /tmp/outdoor.jpg
```

That's it for this camera — it has no pan/tilt/zoom.

---

## Camera 2: Reolink E1 Zoom (Living Room — Indoor PTZ)

- **IP:** `$REOLINK_IP`
- **Credentials:** `$REOLINK_USER` / `$REOLINK_PASS`
- **Resolution:** 4K (3840x2160)
- **Firmware:** v3.2.0.4741_2503281992
- **Capabilities:** Pan, tilt, 5x optical zoom, autofocus, 32 presets, audio, SD card recording

### Enabled Ports

| Port | Protocol | Purpose |
|------|----------|---------|
| 554 | RTSP | Video streaming |
| 443 | HTTPS | Web API (PTZ control, snapshots, config) |
| 8000 | ONVIF | Alternative control protocol |
| 9000 | Reolink | Proprietary protocol (app/client use) |

### Grab a Snapshot (simple — ffmpeg)

```bash
ffmpeg -rtsp_transport tcp \
  -i "rtsp://$REOLINK_USER:$REOLINK_PASS@$REOLINK_IP:554/h264Preview_01_main" \
  -frames:v 1 -update 1 -y /tmp/livingroom.jpg
```

### Grab a 4K Snapshot via HTTPS API

```bash
TOKEN=$(curl -sk -X POST "https://$REOLINK_IP:443/cgi-bin/api.cgi?cmd=Login" \
  -H "Content-Type: application/json" \
  -d "[{\"cmd\":\"Login\",\"action\":0,\"param\":{\"User\":{\"userName\":\"$REOLINK_USER\",\"password\":\"$REOLINK_PASS\"}}}]" \
  | python3 -c "import sys,json; print(json.load(sys.stdin)[0]['value']['Token']['name'])")

curl -sk -o /tmp/livingroom.jpg \
  "https://$REOLINK_IP:443/cgi-bin/api.cgi?cmd=Snap&channel=0&token=$TOKEN"
`

*[truncated — see source for full prompt]*