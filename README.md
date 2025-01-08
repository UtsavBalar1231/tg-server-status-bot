# Telegram Server Status Bot

Server Status Bot is a Python script that monitors server metrics and sends status updates to a specified Telegram channel. It provides information such as CPU usage, RAM usage, disk usage, active user, and private IPs.

## Features

- Monitors and reports:
  - CPU usage
  - RAM usage
  - Disk usage
  - Active user
  - Hostname
  - Private IP addresses
  - Server load

- Sends updates to a specified Telegram channel at regular intervals using a systemd timer.

## Requirements

- Python 3
- `psutil` library
- `requests` library
- A Telegram bot token and chat ID

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/UtsavBalar1231/tg-server-status-bot.git
cd tg-server-status-bot
```

### 2. Install Dependencies

Install the required Python libraries:

```bash
pip install psutil requests
```

### 3. Configure Environment Variables

Create an environment file at `/etc/server-status.env`:

```bash
sudo touch /etc/server-status.env
sudo nano /etc/server-status.env
```

Add the following lines, replacing with your actual values:

```bash
TOKEN="your-telegram-bot-token"
CHAT_ID="your-chat-id"
```

### 4. Install the Service and Timer

Run the `install` script:

```bash
sudo ./install
```

This script will:
- Copy the main script (`serverstatus`) to `/usr/local/bin/`.
- Copy the systemd service and timer files to `/etc/systemd/system/`.
- Enable and start the timer.

## Usage

The bot sends server status updates to the configured Telegram channel every 10 minutes. You can modify the interval by editing the `OnCalendar` directive in the `server-status.timer` file.

### Checking Status

To check the status of the service and timer, use:

```bash
sudo systemctl status server-status.service
sudo systemctl status server-status.timer
```

### Logs

To view the logs, use:

```bash
journalctl -u server-status.service
```

## Uninstallation

To uninstall the bot, run the `uninstall` script:

```bash
sudo ./uninstall
```

This script will:
- Stop and disable the systemd timer.
- Remove the systemd service and timer files.
- Optionally remove the main script and environment file.

## Contributing

Feel free to fork the project and submit pull requests. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- This project uses the [psutil](https://github.com/giampaolo/psutil) library for system information.
- Inspired by various server monitoring tools and scripts available in the open-source community.

---
