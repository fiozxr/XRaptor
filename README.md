# XRaptor

XRaptor is a lightweight, real‑time, automatic intrusion‑prevention tool designed to monitor SSH logs, detect brute‑force attempts, auto‑block attackers, auto‑unblock after expiry, and send optional notifications. It works as a full daemon + installer script.

---

# GITHUB PAGE

https://fiozxr.github.io/XRaptor/

---

✨ Features

Real‑time log monitoring (tail‑F based)

Detect failed SSH login attempts

Auto‑block suspicious IPs using iptables

Auto‑unblock after configurable time

Whitelist support

Persistent state tracking

Discord Webhook alerts (optional)

Telegram alerts (optional)

Simple Installer with auto‑service creation

Runs as a systemd service

Lightweight & fast — pure Bash



---

📦 Installation

1️⃣ Create installer file

Copy the installer script from the "Xraptor - Installer And Daemon" file. Save as:

sudo nano install_xraptor.sh

Paste → Save → Exit.

2️⃣ Make installer executable

sudo chmod +x install-fiozxrr.sh

3️⃣ Run installer

sudo ./install-xraptor.sh

The installer will:

Install XRaptor daemon

Create /usr/local/bin/xraptor.sh

Create systemd service xraptor.service

Enable & start service



---

⚙️ Configuration

After installation, config file is located at:

/etc/xraptor/xraptor.conf

Editable settings

THRESHOLD=5            # Max attempts before block
BAN_TIME=3600          # Seconds (1 hr default)
LOG_FILE="/var/log/auth.log"
STATE_FILE="/var/run/xraptor-state.txt"
WHITELIST="/etc/xraptor/whitelist.txt"

ENABLE_TELEGRAM="no"
TELEGRAM_BOT_TOKEN=""
TELEGRAM_CHAT_ID=""

ENABLE_DISCORD="no"
DISCORD_WEBHOOK=""

After editing config:

sudo systemctl restart xraptor


---

🚀 Usage

Check XRaptor status

sudo systemctl status xraptor

Start / Stop / Restart

sudo systemctl start xraptor
sudo systemctl stop xraptor
sudo systemctl restart xraptor

View logs

sudo journalctl -u xraptor -f

View blocked IPs

cat /var/run/xraptor-state.txt

Whitelist an IP

echo "1.2.3.4" | sudo tee -a /etc/xraptor/whitelist.txt
sudo systemctl restart xraptor

Whitelist prevents blocking.


---

🔧 How It Works (Internals)

XRaptor monitors SSH logs via tail -Fn0 /var/log/auth.log.

On each "Failed password" entry:

Extracts attacking IP

Counts attempts in log

If count ≥ threshold → IP is blocked


Blocked IP is stored in STATE_FILE with timestamp

Every cycle checks expired bans & unblocks IP

Alert hooks send notifications (if enabled)



---

🔔 Notifications

Enable Telegram Alerts

Edit config:

ENABLE_TELEGRAM="yes"
TELEGRAM_BOT_TOKEN="<your-bot-token>"
TELEGRAM_CHAT_ID="<your-chat-id>"

Restart:

sudo systemctl restart xraptor

Enable Discord Webhook Alerts

ENABLE_DISCORD="yes"
DISCORD_WEBHOOK="https://discord.com/api/webhooks/..."

Restart.


---

🗑 Uninstall

sudo systemctl stop xraptor
sudo systemctl disable xraptor
sudo rm /etc/systemd/system/xraptor.service
sudo rm -rf /etc/xraptor
sudo rm /usr/local/bin/xraptor.sh
sudo rm /usr/local/bin/install_xraptor.sh
sudo systemctl daemon-reload


---

🛡 Recommended Security Setup

Change default SSH port

Disable password auth → use SSH keys

Configure Fail2Ban (can run alongside XRaptor)

Use UFW firewall



---

📜 License

MIT — free to modify, distribute, and use.


---

👤 Author
![https://www.github.com/fiozxr] FIOZXR
