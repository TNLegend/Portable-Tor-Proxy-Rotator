# 🧅 Portable Tor Proxy Rotator

A self-contained, lightweight Windows utility that manages a local **Tor SOCKS5 Proxy Farm**. It comes pre-packaged with the necessary Tor binaries, requiring zero external setup.

It automatically spawns multiple Tor circuits on different local ports and handles IP rotation without restarting the service.

  

## ✨ Features

  * **🔋 Batteries Included:** Comes with the Tor engine pre-packed. Just clone and run.
  * **🔄 Instant Rotation:** Rotates IP addresses for all open ports instantly via the Tor Control Protocol (`NEWNYM`).
  * **🔌 Multi-Port Support:** Automatically configures and opens **50+ simultaneous SOCKS5 proxy ports** (Default: `127.0.0.1:20000` to `20049`).
  * **⏱️ Auto-Pilot:** Configurable timer to rotate IPs automatically (Default: every 5 minutes).
  * **🎮 Manual Control:** Press **ENTER** at any time to force an immediate IP rotation.
  * **🧹 Self-Cleaning:** Aggressively cleans up temporary configuration files (`torrc`) and data directories (`data/`) upon startup and shutdown to keep your system clean.

## 📂 Repository Structure

The repository includes the Tor executables, so the structure is plug-and-play:

```text
Tor-Proxy-Rotator/
│
├── run_tor.bat     # The main script manager
├── tor.exe                 # Tor Engine (Included)
├── tor-gencert.exe         # Tor Utility (Included)
```

## 🚀 Installation & Usage

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/YourUsername/Tor-Proxy-Rotator.git
    cd Tor-Proxy-Rotator
    ```

2.  **Run the Rotator:**
    Double-click **`run_tor.bat`**.

3.  **Wait for Bootstrap:**
    The script will launch Tor in the background. Wait a few seconds for the status to show **RUNNING**.

### Controls

The console window accepts the following commands while running:

| Key | Action |
| :--- | :--- |
| **R** | **Force Rotate:** Sends the signal to get fresh IPs immediately. |
| **Q** | **Quit:** Kills the Tor process, deletes temp files, and closes the window. |
| **(Wait)** | **Auto-Rotate:** The script will automatically rotate IPs every 5 minutes. |

## ⚙️ Configuration

You can edit the settings directly at the top of the `run_tor.bat` file using any text editor:

```batch
:: --- CONFIGURATION ---
set "START_PORT=20000"        :: The starting port number
set "PORT_COUNT=50"           :: How many simultaneous ports/IPs to open
set "ROTATION_INTERVAL=300"   :: Auto-rotation time in seconds (300s = 5m)
```

## 🔌 Connecting to the Proxies

Once the script is running, you can connect to these proxies using any software (Python, Browser, cURL) that supports SOCKS5:

  * **Proxy 1:** `socks5://127.0.0.1:20000`
  * **Proxy 2:** `socks5://127.0.0.1:20001`
  * ...
  * **Proxy 50:** `socks5://127.0.0.1:20049`

*(Note: Tor creates a unique circuit isolation for each port listener, attempting to provide different IPs for each port where possible).*

-----

*Disclaimer: This tool is for educational and testing purposes only.*
