# MDS-01 Material Dryer/Dehumidifier

## Project Overview
The **MDS-01** is a material dryer/dehumidifier designed to maintain optimal moisture levels in sensitive materials. It features an ESP32-S3 microcontroller with a dial display for intuitive control of both the moisture recirculation and heater systems.

## Hardware Specifications
- **Microcontroller:** ESP32-S3
- **Display:** Dial display interface
- **Systems Controlled:**  
  - Moisture recirculation  
  - Heater
- **Connection:** USB Type-C for flashing and power

## Prerequisites
- **Development Environment:**  
  - [Visual Studio Code (VSCode)](https://code.visualstudio.com/)
  - [PlatformIO extension for VSCode](https://platformio.org/install/ide?install=vscode)
- **Hardware Needed:**  
  - ESP32-S3 device (as used in MDS-01)
  - USB Type-C cable

## Flashing the Device

1. **Clone the Repository**
   ```sh
   git clone https://github.com/FracktalWorks/MDS-01-De-Humidifier.git
   ```

2. **Open Project in VSCode**
   - Launch VSCode.
   - Open the project folder.

3. **Install PlatformIO**
   - If not already installed, get PlatformIO from the VSCode Extensions sidebar.

4. **Connect the Device**
   - Plug your ESP32-S3 into your computer using a USB Type-C cable.

5. **Flash the Firmware**
   - In VSCode, open PlatformIO (the alien icon).
   - Click on **"Upload"** or run the following command in the terminal:
     ```sh
     platformio run --target upload
     ```
   - Wait for the process to complete; the device will reboot when done.

## Troubleshooting
- **To be determined (TBD).**
- Please open an issue if you encounter any problems with setup or flashing.

---

For further details on configuration, contributing, or advanced features, see additional documentation or contact the maintainers.
