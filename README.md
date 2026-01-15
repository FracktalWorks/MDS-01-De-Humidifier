# MDS-01 Material Dryer/Dehumidifier

## Project Overview
The **MDS-01** is a material dryer/dehumidifier designed to maintain optimal moisture levels in sensitive materials (3D printing filaments). It features an ESP32-S3 microcontroller with a dial display for intuitive control of both the moisture recirculation and heater systems.

## Hardware Specifications
- **Microcontroller:** ESP32-S3-DevKitM-1
- **Display:** ST7567 JLX12864 LCD (128x64)
- **Sensors:** DHT22 Temperature & Humidity sensor
- **User Input:** Rotary encoder with push button
- **Indicators:** WS2812B NeoPixel RGB LEDs (x3)
- **Outputs:** 2x Relay modules (Heater & Fan control)
- **Audio:** Buzzer for feedback
- **Connection:** USB Type-C for flashing and power

## Pin Configuration (ESP32-S3)
| Function | GPIO Pin |
|----------|----------|
| NeoPixel | 14 |
| LCD Clock | 36 |
| LCD Data | 35 |
| LCD CS | 21 |
| LCD DC | 47 |
| LCD Reset | 13 |
| DHT22 | 12 |
| Encoder A | 5 |
| Encoder B | 4 |
| Encoder Button | 1 |
| Buzzer | 48 |
| Relay 1 (Fan) | 15 |
| Relay 2 (Heater) | 16 |

## Prerequisites

### Software Requirements
- [Visual Studio Code (VSCode)](https://code.visualstudio.com/) - Free code editor
- [PlatformIO IDE Extension](https://platformio.org/install/ide?install=vscode) - Development platform for embedded systems
- USB drivers for ESP32-S3 (usually auto-installed)

### Hardware Requirements
- ESP32-S3-DevKitM-1 board
- USB Type-C cable (data-capable, not charge-only)
- MDS-01 hardware assembly

## Step-by-Step Installation Guide

### Step 1: Install Visual Studio Code
1. Download VSCode from [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Run the installer and follow the prompts
3. Launch VSCode after installation

### Step 2: Install PlatformIO Extension
1. Open VSCode
2. Click the **Extensions** icon in the left sidebar (or press `Ctrl+Shift+X`)
3. Search for **"PlatformIO IDE"**
4. Click **Install** on the PlatformIO IDE extension
5. Wait for installation to complete (may take a few minutes)
6. **Restart VSCode** when prompted

### Step 3: Clone the Repository
**Option A: Using Git (Recommended)**
```sh
git clone https://github.com/FracktalWorks/MDS-01-De-Humidifier.git
```

**Option B: Download ZIP**
1. Go to the repository on GitHub
2. Click the green **"Code"** button
3. Select **"Download ZIP"**
4. Extract the ZIP to your desired location

### Step 4: Open the Project
1. Open VSCode
2. Go to **File → Open Folder**
3. Navigate to: `MDS-01-De-Humidifier/Production Code/Dehumidifier V2`
4. Click **Select Folder**
5. PlatformIO will automatically detect the project

### Step 5: Install Dependencies
Dependencies are automatically installed when you build the project. The following libraries will be downloaded:

| Library | Version | Purpose |
|---------|---------|---------|
| U8g2 | ^2.35.10 | LCD display driver |
| SimpleRotary | ^1.1.3 | Rotary encoder handling |
| Adafruit NeoPixel | ^1.12.0 | RGB LED control |
| Adafruit Unified Sensor | ^1.1.14 | Sensor abstraction |
| DHT sensor library | ^1.4.6 | Temperature/humidity sensor |

**To manually trigger dependency installation:**
1. Click the PlatformIO icon (alien head) in the left sidebar
2. Under **PROJECT TASKS → esp32s3**, click **Build**
3. Wait for the build to complete (first build downloads all libraries)

### Step 6: Connect the ESP32-S3
1. Connect the ESP32-S3 to your computer using a **USB Type-C cable**
2. Windows should automatically install drivers
3. Verify connection:
   - Open **Device Manager** (Windows)
   - Look for a new **COM port** under "Ports (COM & LPT)"
   - Note the COM port number (e.g., COM3)

**If the device is not recognized:**
- Try a different USB cable (some cables are charge-only)
- Try a different USB port
- Install [CP210x drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) if needed

### Step 7: Upload the Firmware
1. In VSCode, click the **PlatformIO icon** (alien head) in the left sidebar
2. Under **PROJECT TASKS → esp32s3**, click **Upload**
3. Or use the keyboard shortcut: `Ctrl+Alt+U`
4. Or run in terminal:
   ```sh
   pio run --target upload
   ```
5. Wait for the upload to complete
6. The ESP32 will automatically reboot with the new firmware

### Step 8: Monitor Serial Output (Optional)
To view debug messages:
1. Click **PlatformIO icon** → **PROJECT TASKS → esp32s3 → Monitor**
2. Or use keyboard shortcut: `Ctrl+Alt+S`
3. Or run in terminal:
   ```sh
   pio device monitor
   ```

## Troubleshooting

### Upload Failed - No Serial Port
- Ensure USB cable supports data transfer
- Try holding the **BOOT** button while clicking Upload
- Check Device Manager for COM port

### Upload Failed - Permission Denied
- Close any other programs using the COM port
- Try running VSCode as Administrator

### Display Not Working
- Check SPI wiring connections
- Verify pin definitions in `include/pins.h`
- Ensure LCD contrast is set correctly in code

### DHT Sensor Reading NaN
- Check DHT22 wiring (VCC, GND, DATA)
- Ensure 10kΩ pull-up resistor on data line
- Sensor needs 2+ seconds between reads

### Rotary Encoder Not Responding
- Check encoder pin connections
- Verify debounce delay setting
- Test encoder with simple example sketch

## Project Structure
```
Dehumidifier V2/
├── platformio.ini      # PlatformIO configuration
├── include/
│   └── pins.h          # Pin definitions
├── src/
│   └── main.cpp        # Main application code
├── lib/                # Private libraries (if any)
└── test/               # Unit tests (if any)
```

## Supported Filament Presets
| Filament | Temperature | Dry Time |
|----------|-------------|----------|
| Custom | User-defined | User-defined |
| PLA | 50°C | 4 hours |
| ABS/ASA | 70°C | 6 hours |
| NYLON/PC | 80°C | 10 hours |
| PETG | 70°C | 10 hours |
| TPU | 80°C | 10 hours |
| PEEK | 100°C | 24 hours |
| ULTEM | 100°C | 24 hours |

## License
Please see LICENSE file for details.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request.

## Support
If you encounter any problems, please [open an issue](https://github.com/FracktalWorks/MDS-01-De-Humidifier/issues) on GitHub.

---

For further details on configuration, contributing, or advanced features, see additional documentation or contact the maintainers.
