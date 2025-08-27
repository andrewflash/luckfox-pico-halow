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

## Dependencies

- CONFIG_CRC7=y (automatically included in patch)
- Linux kernel with cfg80211/mac80211 support
- ARM cross-compilation toolchain