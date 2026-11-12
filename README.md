# TestPad ZMK firmware scaffold

Hardware:
- MCU board: Seeed XIAO nRF52840 (`xiao_ble`)
- Matrix columns: COL0=D0, COL1=D1
- Matrix rows: ROW0=D10, ROW1=D9
- Default keymap: Q W / A S
- BLE HID; single, non-split keyboard

## Build with the official unified ZMK config template

1. Create a repository from https://github.com/zmkfirmware/unified-zmk-config-template
2. Copy the contents of this archive into the repository, preserving paths.
3. Push to GitHub.
4. Open Actions and wait for the `build` workflow.
5. Download the `firmware` artifact and flash the `testpad` UF2 to the XIAO nRF52840.

## Important hardware assumption

The overlay currently assumes `diode-direction = "col2row"` and uses active-high
columns plus active-high/pulldown rows, matching the ZMK GPIO matrix example.
The PCB diode orientation must actually be col2row. If the board is wired
row2col, change the diode direction and GPIO polarity/pulls accordingly before
flashing.

## Battery

The battery/DC-DC circuit is not configured by this keyboard shield. Ensure the
XIAO receives a correctly regulated supply within its documented limits and
that USB and external power cannot back-feed each other. Do not connect a
single 1.5 V AA cell directly to the XIAO BAT or 3V3 pin.

## Notes

This is a source/configuration scaffold, not a precompiled UF2. A GitHub Actions
build is needed to produce the firmware binary.
