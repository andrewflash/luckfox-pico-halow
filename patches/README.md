# FGH100M WiFi HaLow Driver Patches

This directory contains patches for adding FGH100M WiFi HaLow (802.11ah) driver support to the luckfox-pico-halow kernel.

## Patch Series

### 0001-net-wireless-Add-FGH100M-WiFi-HaLow-driver-support.patch
- **Size**: 1.9MB (60,439 lines)
- **Files changed**: 134 files, 59,324+ insertions
- **Commit**: 12fbf535b

**Description:**
Adds complete FGH100M WiFi HaLow driver with:
- 802.11ah (Sub-1GHz WiFi) protocol support
- SPI/SDIO/USB interface support  
- MMRC rate control algorithms
- Power management with TWT support
- Mesh networking capabilities
- Hardware abstraction for MM6108/MM8108 chips
- ARM architecture compilation fixes
- CRC7 library dependency resolution

## Application

Apply the patch using:
```bash
git apply patches/0001-net-wireless-Add-FGH100M-WiFi-HaLow-driver-support.patch
```

Or using git am for commit preservation:
```bash
git am patches/0001-net-wireless-Add-FGH100M-WiFi-HaLow-driver-support.patch
```

## Testing

Patches have been tested on:
- **Platform**: Luckfox RV1106 
- **Architecture**: ARM
- **Compiler**: arm-rockchip830-linux-uclibcgnueabihf-
- **Status**: ✅ Compilation successful

## Hardware Connection - Luckfox Mini Plus B to FGH100M

### SPI Interface Pins
| **Function** | **FGH100M Pin** | **Luckfox GPIO** | **Physical Pin** | **DTS Pin** |
|--------------|-----------------|------------------|------------------|-------------|
| **SPI Clock** | SPI_CLK | GPIO1_PC1 (49) | Pin 8 | spi0_clk_m0 |
| **SPI MOSI** | SPI_MOSI | GPIO1_PC2 (50) | Pin 7 | spi0_mosi_m0 |
| **SPI MISO** | SPI_MISO | GPIO1_PC3 (51) | Pin 10 | spi0_miso_m0 |
| **SPI CS** | SPI_CS | GPIO1_PC0 (48) | Pin 6 | spi0_cs0n_m0 |

### Control and Status Pins
| **Function** | **FGH100M Pin** | **Luckfox GPIO** | **Physical Pin** | **Purpose** |
|--------------|-----------------|------------------|------------------|-------------|
| **BUSY Status** | GPIO0 (BUSY) | **GPIO1_PB1 (9)** | **Pin 9** | Module busy indicator |
| **Wireless IRQ** | WIRQ | **GPIO1_PA6 (14)** | **Pin 14** | Interrupt from module |
| **Reset** | nRESET | **GPIO1_PA7 (15)** | **Pin 15** | Module reset control |
| **Wake Up** | HOST_WAKE | **GPIO1_PB0 (8)** | **Pin 8** | Wake module from sleep |
| **Power Enable** | VCC_EN | **GPIO1_PA5 (13)** | **Pin 13** | Power control |

### Power Supply
- **VCC**: 3.3V from Luckfox board
- **GND**: Common ground connection

### Device Tree File
Use the provided DTS file: `rv1103g-luckfox-pico-mini-plus-b.dts`

## Dependencies

- CONFIG_CRC7=y (automatically included in patch)
- Linux kernel with cfg80211/mac80211 support
- ARM cross-compilation toolchain
- Proper hardware connections as listed above