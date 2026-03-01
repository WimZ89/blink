# GEMINI.md - Project Context

## Project Overview
This is the **Blink Example + WiFi AP** project for the **ESP-IDF**. It demonstrates how to blink an LED while simultaneously running a WiFi Access Point.

### Key Technologies
- **Language:** C
- **Framework:** ESP-IDF (FreeRTOS-based)
- **WiFi:** SoftAP mode (SSID: "Test Wifi AP WImz")
- **Build System:** CMake / `idf.py`
- **Dependencies:** `espressif/led_strip`, `esp_wifi`, `nvs_flash`, `esp_event`, `esp_netif`

## Architecture and Structure
- `main/`: Contains the core application logic.
    - `blink_example_main.c`: The main entry point (`app_main`) and LED control logic.
    - `idf_component.yml`: Defines external component dependencies.
    - `Kconfig.projbuild`: Defines project-specific configuration options for `menuconfig`.
- `sdkconfig.defaults*`: Default configuration files for various ESP32 targets.

## Building and Running
The project uses the `idf.py` tool for common development tasks.

### Core Commands
- **Set Target:** `idf.py set-target <chip_name>` (e.g., `esp32`, `esp32s3`, `esp32c3`)
- **Configure:** `idf.py menuconfig`
    - Navigate to `Example Configuration` to set:
        - LED type (GPIO or LED Strip)
        - GPIO number
        - Blink period
- **Build:** `idf.py build`
- **Flash & Monitor:** `idf.py -p <PORT> flash monitor`
    - Replace `<PORT>` with your serial port (e.g., `/dev/ttyUSB0` or `COM3`).

## Development Conventions
- **Configuration:** Use `Kconfig` for project-wide settings. Access them in C via `CONFIG_` prefixed macros (e.g., `CONFIG_BLINK_GPIO`).
- **Logging:** Use `ESP_LOGI`, `ESP_LOGE`, etc., for output. The tag for this project is `"example"`.
- **Task Management:** The application runs in a FreeRTOS environment. `app_main` is the main task. Use `vTaskDelay` for non-blocking delays.
- **Components:** Additional functionality should be added as components or managed via `idf_component.yml`.

## Key Files
- `main/blink_example_main.c`: Primary logic for LED initialization and the blink loop.
- `main/Kconfig.projbuild`: Source of truth for the `Example Configuration` menu.
- `README.md`: Original project documentation with hardware requirements.
