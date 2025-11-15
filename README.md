# XRaptor 

  <h2>🚀 What is XRaptor?</h2>
  <p>
    XRaptor is a lightning‑fast, real‑time SSH brute‑force protection daemon.
    It monitors SSH logs, detects attackers, blocks malicious IPs, auto‑unblocks after expiry, and supports Telegram + Discord alerts.
    Built in pure Bash — no dependencies.
  </p>
</div>

<div class="section">
  <h2>✨ Features</h2>
  <ul>
    <li>Real‑time SSH log monitoring</li>
    <li>Auto‑block repeated login failures</li>
    <li>Auto‑unblock after expiration</li>
    <li>Whitelist supported</li>
    <li>Telegram + Discord alerts</li>
    <li>Runs as a systemd daemon</li>
    <li>Lightweight — pure Bash</li>
  </ul>
</div>

<div class="section">
  <h2>📦 Installation</h2>
  <pre><code>sudo chmod +x install_xraptor.sh

sudo ./install_xraptor.sh</code></pre> </div>

<div class="section">
  <h2>⚙️ Configuration</h2>
  <pre><code>/etc/xraptor/xraptor.conf</code></pre>
  <p>Includes:</p>
  <ul>
    <li>THRESHOLD</li>
    <li>BAN_TIME</li>
    <li>Whitelist</li>
    <li>Telegram / Discord keys</li>
    DON'T UNDERSTAND ?
    - https://fiozxr.github.io/xraptor/understand.html
  </ul>
</div>

<div class="section">
  <h2>🛠 Commands</h2>
  <pre><code>sudo systemctl status xraptor

sudo systemctl restart xraptor sudo journalctl -u xraptor -f</code></pre> </div>

<div class="section">
  <h2>🌐 Alerts</h2>
  <p>XRaptor supports:</p>
  <ul>
    <li>Telegram Bot Alerts</li>
    <li>Discord Webhook Alerts</li>
  </ul>
</div>

--
 https://instagram.com/@fiozxr
---

📌 Contributing 

Pull requests are welcome! Feel free to open issues for bugs, ideas, or improvements.

⭐ Support

If you find XRaptor useful, please give the repository a star on GitHub — it helps a lot!

📢 Social

You can share XRaptor, fork it, modify it, and build on top of it freely.
