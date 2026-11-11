# Changelog

## 0.1.2 (2026-11-11)

The companion serves the routes the hosted studio added since 0.1.1, so it no longer shows *update available*
or sends them to the browser:

- **Systems of boards:** build every board, load them all into SRAM, co-simulate them in lockstep with a live
  UART console per link, sign off each board and write the combined order files.
- **Microcontrollers:** firmware builds with the Pico SDK, ESP-IDF or RISC-V GCC on this machine, ESP32
  programming with esptool, and Build firmware for soft RISC-V systems without a new FPGA build.
- **Serial ports** on this machine, for live runs against a real board.
- **Projects:** Save a copy, IP cores written into the project, and library blocks opened as board projects.
- **Board blocks:** group wired parts into a reusable block in your `~/.hw-studio` library and place it again.
- Browser builds save their report into the project.

## 0.1.1 (2026-10-31)

- Route manifest in the handshake: a hosted studio newer than the companion sends the routes the companion
  doesn't have to the browser and shows *update available*, instead of failing.
- Multi-board systems, live analog simulation of chip-free boards, iCE40 SRAM loads over the FTDI's SPI,
  and the new library blocks (RV32I CPU, PWM audio, LM75, MCP3008).
- The boards' verification logs are left out of the package.

## 0.1.0 (2026-10-25)

First release of the companion for the hosted studio: `serve`, `pair`, `doctor` and `mcp`; local
projects, builds with the open toolchains, live simulation (Icarus Verilog, Verilator) and SRAM
programming over USB.
