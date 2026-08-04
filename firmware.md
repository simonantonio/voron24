# Klipper Firmware Settings

Firmware configuration notes for installed Klipper boards.

---

## SB2209 CAN

**Current board:** StealthBurner toolhead board  
**Connection:** CAN bus via Katapult bootloader

### Firmware Configuration

| Setting | Value |
| --- | --- |
| MCU | STM32G0B1 |
| Clock Reference | 8 MHz |
| Bootloader Offset | 8 KiB |
| Communication | CAN bus |
| CAN Pins | PB0 / PB1 |
| CAN Speed | 1,000,000 |

### Build Firmware

Configure Klipper:

```bash
make menuconfig
```

Use the settings above, then build:

```bash
make clean
make
```

Copy firmware:

```bash
cp ./out/klipper.bin ~/firmware/ebb-sb2209.bin
```

### Flash via Katapult

Find the CAN UUID:

```bash
python3 ~/katapult/scripts/flashtool.py -i can0 -q
```

Current UUID:

```text
0f8c391b52f4
```

Flash firmware:

```bash
python3 ~/katapult/scripts/flashtool.py \
    -i can0 \
    -u 0f8c391b52f4 \
    -f ~/firmware/ebb-sb2209.bin
```

---

## BTT Octopus

### Firmware Configuration

| Setting | Value |
| --- | --- |
| MCU | STM32F446 |
| Clock Reference | 12 MHz |
| Bootloader Offset | 32 KiB |
| Communication | USB |
| USB Pins | PA11 / PA12 |

---