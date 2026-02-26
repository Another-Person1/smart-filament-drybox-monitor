# Smart Filament Drybox Monitor

A remote thermometer/hygrometer project for tracking 3D printer filament moisture levels via humidity/temperature sensing.

Designed to go into a filament drybox/filament management system for measuring drybox temperature/humidity.

Helps prevent print failures caused by wet filament by ensuring the drybox is dry.

Project name will probably be changed along with a few minor details.

---

## Compatibility Notice (Please Read)
**Please read carefully before proceeding.** This list is non-exhaustive but covers the most common use cases.

### Not Supported (Active Heating):

- Any system featuring integrated or add-on heating elements
- Bambu AMS 2 Pro / AMS HT
- Creality SpacePi
- Sunlu FilaDryer / S series
- Sunlu AMS Heater

### Supported (Passive Drying):

- Passive filament storage boxes using only desiccant to dry
- Original Bambu AMS (without external or internal heater accessories)
- Bambu AMS Lite
- Prusa MMU2S/MMU3
- Creality CFS
- Other passive filament management systems without heating

Disclaimer: I am not responsible for any damages or hardware failure caused by product misuse or use within unsupported thermal environments.

---

## Problem
Most affordable hygrometers currently available suffer from significant limitations:
1.  Many cannot measure reliably at the low humidity levels required for dry filament storage.
2.  LR44 batteries are disposable, hard to find, and expensive (at least where I live)
3.  Local-only sensors don't alert you when your filament is getting wet because your dessicant is oversaturated.
4.  Devices that *do* offer remote monitoring often require extracting binding keys, firmware flashing, Bluetooth proxies, and juggling multiple apps.

## Goals:
- Safe
- Simple to use
- Vendor agonistic
- No subscriptions/cloud
- Inexpensive
- Accurate at low humidity levels
- Easy to see display
- Compatibility with existing "XF002" rectangular footprint
- Local-first (over WiFi, Zigbee, BLE, or Thread, going to make it Matter compatible)
- Modern and clean aesthetic

---

With these goals in mind, here's what I ended up on for parts selection:

## Hardware Selection

Based on the goals above, the following components were selected:

### Microcontroller: [ESP32-C6-MINI-1](https://documentation.espressif.com/esp32-c6-mini-1_mini-1u_datasheet_en.pdf)
* Native support for Wi-Fi, BLE, Thread, and Zigbee.
* Widely supported with active community libraries/code (Arduino, ESPHome, etc.).
* Features both SPI and I2C interfaces plus USB Serial.
* Pre-certified radio module avoids complex antenna routing headaches.
* Small size
* Sufficient pins for all sensors and peripherals.

### Display: [Good Display GDEY0213F52](https://www.good-display.com/product/463.html)
* Matches the intended enclosure design (rectangular interface).
* E-Ink / ePaper technology offers excellent paper-like visibility and extremely low power consumption.
* Supports 4 colours (Red, Black, Yellow, White) for status indicators.
* Uses the common SPI interface
* Robust driver support available for Arduino and ESP32.

### Temp/Humidity Sensor: [SHT41](https://sensirion.com/products/catalog/SHT41)
* Industry-leading precision in relative humidity.
* Excellent stability in the low-humidity ranges critical for filament storage.
* Best price-to-performance ratio for high-quality sensors.
* I2C connection simplifies PCB routing and code implementation.

### Battery: 10440 LiFePO4
* Lithium Iron Phosphate chemistry offers superior thermal stability and safety compared to Li-ion/LiPoly.
* Fully rechargeable and user-replaceable.
* Fits AAA battery form factors; dimensions align with the XF002 standard.
* Significantly longer lifecycle than standard lithium chemistries.
* *Note: Charging requires specific LiFePO4 chargers/circuitry rather than standard Li-ion chips.*
*   **Warning:** Abusing batteries can be dangerous regardless of chemistry. Handle with care.

---

## Software
Coming soon!

---

### Trademark disclaimer:
All trademarks mentioned on this page are the property of their respective owners. This project is not affiliated with, endorsed by, or connected to those organizations. We do not claim ownership of any intellectual property rights belonging to third parties.
