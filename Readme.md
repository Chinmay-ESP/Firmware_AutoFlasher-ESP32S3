# ESP32-S3 Parallel Auto Flashing Tool

## Overview

This project provides a **Python-based automated flashing utility** for **ESP32-S3 devices**.  
It continuously monitors available UART ports and **automatically flashes a firmware binary (`firmware.bin`)** when a new device is connected.

The tool supports **parallel flashing**, making it suitable for **production lines, batch testing, and rapid firmware deployment**.

---

## Key Capabilities

- Automatic detection of newly connected UART devices
- Parallel flashing of multiple ESP32-S3 boards
- No manual COM port selection required
- High-speed flashing using esptool
- Real-time console status reporting

---

## System Requirements

### Software
- Python 3.8 or newer
- `esptool`
- `pyserial`

Install dependencies:
```bash
pip install esptool pyserial
````
---

## Project Structure

```
.
├── auto_flasher.py     # Main flashing script
├── firmware.bin        # Firmware binary to be flashed
└── README.md           # Documentation
```

---

## Configuration Parameters

The following parameters are defined inside the script:

| Parameter  | Description               | Default      |
| ---------- | ------------------------- | ------------ |
| FIRMWARE   | Firmware binary file name | firmware.bin |
| FLASH_ADDR | Flash start address       | 0x0000       |
| CHIP       | Target microcontroller    | esp32s3      |
| BAUD RATE  | UART flashing speed       | 1500000      |

Modify these values directly in the script if required.

---

## Operational Flow

1. The script scans all available UART ports at regular intervals
2. When a new port is detected, it is assumed to be a newly connected ESP32-S3
3. Flashing is initiated immediately in a separate thread
4. Multiple devices can be connected and flashed simultaneously
5. Flash status is displayed in the terminal

---

## Usage Instructions

1. Place the compiled firmware file in the project directory:

   ```
   firmware.bin
   ```
2. Execute the script:

   ```bash
   python auto_flasher.py
   ```
3. Connect ESP32-S3 devices via USB
4. Flashing begins automatically upon detection

---

## Example Console Output

```
[14:32:10] === PARALLEL ESP32-S3 FLASHER STARTED ===
[14:32:15] Detected COM42 → Starting parallel flash
[14:32:15] START Flashing on COM42...
[14:32:21] SUCCESS on COM42
```

---

## Important Notes

* Some ESP32-S3 boards may require **BOOT mode** for flashing
* Ensure `firmware.bin` is present before running the script
* Avoid disconnecting devices during flashing
* Use powered USB hubs for large-scale parallel flashing

---

## Intended Use Cases

* Production firmware flashing
* R&D lab automation
* Manufacturing end-of-line testing
* Educational and institutional labs

```

---
