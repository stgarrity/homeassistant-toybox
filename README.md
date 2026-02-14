# ToyBox 3D Printer — Home Assistant Integration

[![HACS Custom](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

Custom Home Assistant integration for the [ToyBox 3D Printer](https://www.toybox.com/) via the [make.toys](https://www.make.toys) platform.

Uses the [`toybox-api`](https://github.com/sgarrity/toybox-api) Python library for Meteor DDP communication.

## Features

- **Printer status** — idle, printing, heating, paused, completed, cancelled, error
- **Current print name** — what's printing right now
- **Print progress** — percentage complete
- **Time remaining** — estimated time left (calculated from server timestamps)
- **Time elapsed** — how long the current print has been running
- **Last print** — name and status of the most recent completed print
- **Printer online** — connectivity status (binary sensor)
- **Printing active** — binary sensor for automations
- **Printer model** — hardware details as diagnostic attributes

### Dynamic Polling

- **5 minutes** when the printer is idle
- **30 seconds** when a print is actively running

## Installation

### HACS (Custom Repository)

1. Open HACS → Integrations → ⋮ → Custom repositories
2. Add: `https://github.com/sgarrity/homeassistant-toybox`
3. Category: Integration
4. Install from HACS
5. Restart Home Assistant
6. Go to Settings → Devices & Services → Add Integration → "ToyBox 3D Printer"
7. Enter your make.toys email and password

### Manual Installation

1. Copy `custom_components/toybox/` to your Home Assistant `config/custom_components/` directory
2. Restart Home Assistant
3. Add the integration via Settings → Devices & Services

## Architecture

This integration follows the two-project pattern:

| Repo | Purpose |
|------|---------|
| [`toybox-api`](https://github.com/sgarrity/toybox-api) | Standalone Python API client (Meteor DDP over WebSocket) |
| [`homeassistant-toybox`](https://github.com/sgarrity/homeassistant-toybox) | This repo — HA integration (HACS compatible) |

## License

MIT
