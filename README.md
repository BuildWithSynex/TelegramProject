# Syncora

A lightweight background file sync and backup system using Telegram as storage. Built like a professional SaaS backend agent.

## Features
- **Background Sync Engine**: Monitors folders seamlessly with `watchdog`. Avoids CPU spikes with intelligent event debouncing.
- **Telegram Backend**: Zero-cost, unlimited storage utilizing the `telethon` API.
- **Smart Uploads**: Calculates SHA-256 hashes to prevent redundant uploads.
- **Tray App Integration**: Non-intrusive operations from the system tray using `pystray`. Includes a dynamic Tkinter dashboard for configurations.
- **Robustness**: Error-handling and rotating file logs keep operations transparent (`~/.syncora.log`).

## Prerequisites
- Python 3.8+
- Windows OS (Testing optimized for Windows)

## Setup
1. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   *(We highly recommend using a virtual environment: `python -m venv venv`)*

2. **Obtain Telegram API Credentials**
   - Head over to [my.telegram.org](https://my.telegram.org)
   - Log in and navigate to "API development tools" to get your `api_id` and `api_hash`.

3. **Get a Target Channel ID**
   - Create a private channel where backups will be stored. You can use its `-100...` ID or regular handle if public.

## Usage
1. Start the application:
   ```bash
   python app/main.py
   ```
2. Look for the **Syncora** icon in your system tray. Let it run in the background.
3. **First-time Configuration**:
   - Right-click the system tray icon -> **Dashboard**.
   - Input your `api_id`, `api_hash`, and `Target Channel ID`.
   - Add folders you wish to sync.
   - Click **Save Settings** and Restart Syncora.
4. When you start Syncora again with valid API credentials, it'll automatically connect and start syncing the files in the monitored folders.

## Architecture Highlights
- `core/`: Business logic, folder watching, hashing, uploader/downloader.
- `app/`: GUI (system tray, dashboard) and application entry point.
- `utils/`: Reusable components like JSON configuration manager and rotating file logger.

## Future Hooks Placeholder
The codebase is structured to easily support:
- Multi-device sync strategies.
- User authentication and premium plan restriction overlays.
