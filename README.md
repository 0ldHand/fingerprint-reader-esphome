# Battery-Powered Fingerprint Reader for Home Assistant

A compact, reliable, and low-power fingerprint reader designed for Home Assistant. Built around the Seeed Xiao ESP32-C6 and Grow R503 sensor, with power-saving sleep mode, external antenna for excellent WiFi range, and full Home Assistant integration.

![Fingerprint Reader](images/IMG_1782.gif)  



---

## ✨ Features

- Full Home Assistant integration (events + services)
- Beautiful LED feedback (Green = Match, Red = No Match, Purple = Enrolling, etc.)
- Power-saving mode — sensor sleeps after 15 seconds of inactivity
- External 2.4GHz WiFi antenna for strong signal
- Battery powered with 2× 18650 cells (~6400mAh total)
- Solar panel ready
- Clean, modern Home Assistant dashboard included
- OTA updates supported

---

## 📦 Parts List

| Component                        | Quantity | Link |
|----------------------------------|----------|------|
| Grow R503 Fingerprint Sensor     | 1        | [AliExpress](https://www.aliexpress.us/item/2251832867340660.html) |
| Seeed Xiao ESP32-C6              | 1        | [Amazon](https://a.co/d/09wqSHJa) |
| 18650 Battery Cells (3200mAh)    | 2        | [18650 Battery Store](https://www.18650batterystore.com/collections/18650-batteries/products/eve-18650-33v) |
| 18650 BMS Protection Board       | 1        | [Amazon](https://a.co/d/00WszbO6) |
| 2.4GHz External WiFi Antenna     | 1        | [Amazon](https://a.co/d/0hRDYEtv) |
| BC327 PNP Transistor             | 1        | [Amazon](https://a.co/d/05GbPzts) |
| 10kΩ Resistor                    | 1        | [Amazon](https://a.co/d/0dJAFne8) |

---

## 🔧 Wiring

Detailed wiring instructions are included in the [`wiring/wiring_instructions.txt`](wiring/wiring_instructions.txt) file.

**Quick Summary:**
- **Red wire** (VCC) → Switched through PNP transistor (GPIO19)
- **White wire** (3.3VT) → Connected directly to 3.3V
- **Blue wire** (Sensing) → GPIO2
- **Yellow** (TX) → GPIO17
- **Green** (RX) → GPIO16


---

## 🚀 Installation (Using ESPHome Builder in Home Assistant)

This is the easiest way to install the firmware.

### Step 1: Create a New Device in ESPHome

1. Open **Home Assistant** → Go to **ESPHome** (from the sidebar)
2. Click the **+ New Device** button
3. Choose **Create a new device from scratch**
4. Give it a name: `fingerprint-reader`
5. Select your **Seeed Xiao ESP32-C6** board
6. Click **Next** → **Finish**

### Step 2: Paste the Configuration

1. Open the file [`esp-home/fingerprint-reader.yaml`](esp-home/fingerprint-reader.yaml) from this repository
2. Copy **all** the content
3. In ESPHome Builder, click on your new device (`fingerprint-reader`)
4. Delete the default YAML and **paste** the entire content from the file
5. Click **Save**

### Step 3: Update Your Secrets

Make sure you have created the following secrets containing values for your env (Top right in esphome builder)

wifi_ssid
wifi_password
api_encryption_key (create a 32-byte Base64-encoded key for this. e.g. 'openssl rand -base64 32')

### Step 4: Install the Firmware

1. Click the Install button (top right)
2. Choose one of these methods:
3. Plug into this computer (recommended for first install)
4. Install via USB (if your computer has a USB port)
5. Install via network (if the device is already on WiFi)

Wait for the flashing process to complete

### Step 5: Add to Home Assistant
Once the device boots successfully:

It should automatically appear in Settings → Devices & Services → ESPHome
If not, click + Add Integration → Search for ESPHome → Select your device

---

## 🏠 Home Assistant Integration

### Services Available:
- `esphome.fingerprint_reader_enroll`
- `esphome.fingerprint_reader_delete`
- `esphome.fingerprint_reader_delete_all`
- `esphome.fingerprint_reader_cancel_enroll`

### Events:
- `esphome.finger_scan_matched`
- `esphome.finger_scan_unmatched`
- `esphome.enrollment_done`
- `esphome.enrollment_failed`

---

## 📊 Dashboard

A clean and functional Home Assistant dashboard is included in the (home-assistant/dashboard.yaml) file.

Features:
- Real-time fingerprint status
- Easy enrollment with ID selector
- Delete single fingerprint or all fingerprints
- WiFi signal strength monitoring

---

## 📸 Screenshots

*(Placeholder for pics)*

- Assembled device
- Dashboard screenshot
- LED feedback examples
- Wiring close-up

---

## 📁 Repository Structure
fingerprint-reader-esphome/
├── README.md
├── esp-home/
│   └── fingerprint-reader.yaml
├── home-assistant/
│   ├── dashboard.yaml
│   └── scripts.yaml
├── wiring/
│   └── wiring_instructions.txt
├── 3d-models/
│   └── r503_flip_cover.stl
└── images/

---

## 🙏 Credits

- [ESPHome](https://esphome.io/) — The amazing framework that makes this possible
- [Seeed Studio](https://www.seeedstudio.com/) — For the excellent Xiao ESP32-C6
- Grow R503 community for documentation and support

---

**Made with ❤️ for Home Assistant users who want reliable, battery-powered fingerprint control.**
