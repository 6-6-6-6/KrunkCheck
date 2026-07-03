# Krunker Checker v2.0 🎮

<img width="1105" height="622" alt="image" src="https://github.com/user-attachments/assets/d0f77d17-c36f-4bfa-8828-80139f10a496" />


A high-performance command-line utility designed to check the availability of **Krunker.io** usernames and clan tags. 

Unlike basic HTTP scraper tools that get blocked instantly, this checker utilizes a headless automated browser (`undetected-chromedriver`) to simulate organic user behaviour, bypassing anti-bot measures and rendering Krunker Social Hub pages dynamically to determine if a name is taken, available, or invalid.

---

## ✨ Features

- **Single Check Mode**: Check a single username or clan tag instantly. Returns profile stats (level, kills, deaths, score, clan) if the name is taken.
- **Bulk Check Mode**: Paste a comma, space, or newline-separated list of names (up to 100) directly into the terminal.
- **Wordlist Mode**: Load a `.txt` list containing names (one per line, up to 500) and export all available names automatically to a new text file (`*_available.txt`).
- **Cool CLI Aesthetic**: Sleek color gradients, animated terminal spinners, real-time progress bars, and neat box-drawing menus.
- **Auto Dependency Installer**: The script automatically checks for and installs required libraries (`selenium` and `undetected-chromedriver`) on the first launch.

---

## 🛠️ Prerequisites

1. **Python 3.7+** must be installed. Make sure it is added to your system PATH.
2. **Google Chrome** must be installed on your system (undetected-chromedriver relies on your local Chrome binary to execute).

---

## 🚀 Installation & Running

1. Clone or download this repository.
2. Open your terminal or command prompt in the directory containing `checker.py`.
3. Run the script:
   ```bash
   python checker.py
   ```
   *Note: On the very first launch, the script will automatically install `selenium` and `undetected-chromedriver` for you.*

---

## 📖 How to Use

When you run `checker.py`, you will be greeted by the interactive main menu:

```text
  ╭──────────────────────────────────────────────────────────╮
  │   ──── MAIN MENU ────                                     │
  ├──────────────────────────────────────────────────────────┤
  │   [1]  single username check                              │
  │   [2]  single clan tag check                              │
  ├──────────────────────────────────────────────────────────┤
  │   [3]  bulk username check                                │
  │   [4]  bulk clan tag check                                │
  ├──────────────────────────────────────────────────────────┤
  │   [5]  wordlist username check                            │
  │   [6]  wordlist clan tag check                            │
  ├──────────────────────────────────────────────────────────┤
  │   [0]  exit                                               │
  ╰──────────────────────────────────────────────────────────╯
```

1. **Enter a number (0-6)** and press `Enter`.
2. Follow the prompt instructions:
   - For **Bulk Mode**, paste your list and press `Enter` on an empty line to start the check.
   - For **Wordlist Mode**, type or paste the file path (e.g., `wordlist.txt`).
3. The checker will display results dynamically:
   - `✓ <name> | AVAILABLE` (Green)
   - `✗ <name> | TAKEN` (Red) - will display stats like Level, Kills, Clan if available.
   - `⚠ <name> | ERROR` (Yellow) - connection drops or timeouts.

---

## ℹ️ Technical Details & Rate Limits

- **WebSocket vs. Browser Automation**: Krunker's WebSocket backend (`wss://social.krunker.io/ws`) actively rejects raw socket requests from third-party clients with a `Connection Failed` error. This tool bypasses that by loading pages through a headless browser instance.
- **Delay Intervals**: The tool uses a `0.5` second delay between queries during bulk/wordlist tasks to prevent rate limiting, IP blocks, or triggering CAPTCHA flags.
