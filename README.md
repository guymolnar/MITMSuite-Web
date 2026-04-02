```
███╗   ███╗██╗████████╗███╗   ███╗    ███████╗██╗   ██╗██╗████████╗███████╗
████╗ ████║██║╚══██╔══╝████╗ ████║    ██╔════╝██║   ██║██║╚══██╔══╝██╔════╝
██╔████╔██║██║   ██║   ██╔████╔██║    ███████╗██║   ██║██║   ██║   █████╗
██║╚██╔╝██║██║   ██║   ██║╚██╔╝██║    ╚════██║██║   ██║██║   ██║   ██╔══╝
██║ ╚═╝ ██║██║   ██║   ██║ ╚═╝ ██║    ███████║╚██████╔╝██║   ██║   ███████╗
╚═╝     ╚═╝╚═╝   ╚═╝   ╚═╝     ╚═╝    ╚══════╝ ╚═════╝ ╚═╝   ╚═╝   ╚══════╝
```

> *See everything. Touch nothing.*

Position yourself between any device and the gateway. Watch their DNS traffic flow live through a sleek, real-time dashboard — every domain query, every device, every second.

> **For educational use only. Only run this on networks you own or have explicit permission to test.**

---

## What it does

MITM Suite poisons ARP caches to silently route traffic through your machine. It then forwards everything transparently — targets stay connected, none the wiser — while you watch their DNS queries roll in on a live dashboard.

- **ARP spoofing** — tricks devices into routing through you
- **Transparent forwarding** — no dropped connections, no suspicion
- **Live DNS feed** — see exactly what every device is reaching out to, in real time
- **Smart noise filtering** — CDNs, telemetry, OS background chatter are all stripped away, leaving only the interesting stuff
- **Auto-discovery** — continuously scans the subnet and picks up new devices as they join
- **Per-device filtering** — click any target in the sidebar to focus the feed on them
- **Blacklist** — exclude specific MACs from interception entirely

---

## Files

| File | What it does |
|------|-------------|
| `main.py` | Starts everything — scanner, spoofer, forwarder, and web server |
| `spoofer.py` | ARP poisoning and clean restoration on exit |
| `sniffer.py` | Captures packets, forwards them, extracts DNS queries |
| `events.py` | Broadcasts events to the dashboard in real time |
| `app.py` | Web server |
| `templates/index.html` | The dashboard |

---

## Setup

**Requirements:** Python 3, Scapy, Flask, Npcap (Windows)

```bash
pip install scapy flask
```

Open `main.py` and set your network interface and gateway:

```python
conf.iface = "Your Interface Name"
gateway_ip = "192.168.x.x"
```

Run as administrator (required for raw packet access):

```bash
python main.py
```

Open `http://localhost:5000` and watch the feed come alive.

---

## Credits

The ARP spoofing, packet forwarding, and DNS interception logic was written by me,
while the web dashboard and server were built with Claude Code.
