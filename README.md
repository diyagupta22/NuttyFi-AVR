# NuttyFi-AVR

Custom Arduino Board Manager package for NuttyFi AVR boards, based on the official [Arduino AVR Boards](https://github.com/arduino/ArduinoCore-avr) core **1.8.8**.

## Supported Boards

| Board | MCU | Notes |
|-------|-----|-------|
| **NuttyFi 328** | ATmega328P @ 16 MHz | Optiboot bootloader, Arduino UNO–compatible pin map |
| **NuttyFi 2560** | ATmega2560 @ 16 MHz | STK500v2 bootloader, Arduino Mega–compatible pin map |

## Installation

### Option A — Arduino IDE (Boards Manager)

1. Create a [GitHub Release](https://github.com/YOUR_GITHUB_USERNAME/NuttyFi-AVR/releases) and upload `nuttyfiavr-1.0.0.zip` (the `hardware` folder archive).
2. Update `package_nuttyfiavr_index.json` with the release URL, archive size, and SHA-256 checksum.
3. Host the index file (e.g. via GitHub raw URL or GitHub Pages).
4. In **Arduino IDE**, open **File → Preferences**.
5. Add your index URL to **Additional boards manager URLs**, for example:
   ```
   https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/NuttyFi-AVR/main/package_nuttyfiavr_index.json
   ```
6. Open **Tools → Board → Boards Manager**, search for **NuttyFi**, and install **NuttyFi AVR Boards**.
7. Select **NuttyFi 328** or **NuttyFi 2560** from **Tools → Board**.

### Option B — Manual install

1. Copy the `hardware` folder from this repository into your Arduino sketchbook:
   - **Windows:** `%USERPROFILE%\Documents\Arduino\hardware\`
   - **macOS:** `~/Documents/Arduino/hardware/`
   - **Linux:** `~/Arduino/hardware/`
2. Restart Arduino IDE.
3. Select **NuttyFi 328** or **NuttyFi 2560** from **Tools → Board**.

The final path must be:

```
<sketchbook>/hardware/nuttyfiavr/avr/1.0.0/
```

When installing manually, rename or place the vendor folder as `nuttyfiavr` so it matches the package name in `package_nuttyfiavr_index.json`.

### Option C — Arduino CLI

```bash
arduino-cli config init
arduino-cli config add board_manager.additional_urls https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/NuttyFi-AVR/main/package_nuttyfiavr_index.json
arduino-cli core update-index
arduino-cli core install nuttyfiavr:avr
arduino-cli board listall nuttyfiavr
```

## Verify

Upload the built-in **Blink** example to confirm your setup:

```
File → Examples → 01.Basics → Blink
```

Choose the correct NuttyFi board and port, then upload.

## Repository Layout

```
NuttyFi-AVR/
├── hardware/
│   └── avr/
│       └── 1.0.0/
│           ├── boards.txt
│           ├── platform.txt
│           ├── programmers.txt
│           ├── bootloaders/
│           ├── cores/
│           ├── libraries/
│           └── variants/
│               ├── nuttyfi328/
│               └── nuttyfi2560/
├── extras/
├── tools/
├── package_nuttyfiavr_index.json
└── README.md
```

## Creating a Release Archive

From the repository root:

```bash
# The zip must contain hardware/avr/1.0.0/ at the top level inside hardware/nuttyfiavr/
zip -r nuttyfiavr-1.0.0.zip hardware/
```

On Windows (PowerShell):

```powershell
Compress-Archive -Path hardware -DestinationPath nuttyfiavr-1.0.0.zip -Force
```

Then compute the SHA-256 checksum and file size for `package_nuttyfiavr_index.json`.

## License

Arduino core files are derived from the Arduino AVR core and are subject to the [GNU Lesser General Public License](https://www.gnu.org/licenses/lgpl-3.0.html). See individual source files for copyright notices.
