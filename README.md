# hw-studio releases

Compiled releases of the **hw-studio companion**, the local half of the hw-studio FPGA IDE
(https://hw-studio-blond.vercel.app). The companion runs on your machine and gives the hosted studio
projects, builds, simulation and USB programming over localhost. Your projects stay on your machine.

This repository holds release notes, checksums and licence files only. The packages are attached to
[Releases](https://github.com/Pinka/hw-studio-releases/releases). The source code is not public.

## Install and start

You need **Node.js 20 or newer** (https://nodejs.org). Then, in any folder:

```
npx --yes https://github.com/Pinka/hw-studio-releases/releases/download/v0.1.0/hw-studio-0.1.0.tgz serve
```

Use the version the studio shows on its "Connect the local companion" page; it must match the studio's
major.minor version. The first start downloads the package and its runtime dependencies (about 700 MB on Windows,
mostly Next.js and the Claude Agent SDK used by the System view's prompt) into npm's cache.

The companion listens on `http://127.0.0.1:4317` (`--port` to change) and serves the local studio there too.

## Pair with the hosted studio

`serve` prints a pair link such as `https://hw-studio-blond.vercel.app/studio#pair=<token>@4317`.
Open it and the studio pairs in one step, or paste the token and port on the connect page. Chrome may
ask whether the site may reach devices on your local network: allow it, the companion is on localhost.

Other commands (same `npx --yes <url>` prefix):

- `pair [--rotate]`: print the pairing token again, or make a new one.
- `doctor`: check Node, the toolchains and a connected board.
- `mcp`: the MCP server on stdio, for Claude Code.
- `--version`

Settings, the token and recent projects are in `~/.hw-studio`.

## System requirements

- Windows 10/11, macOS or Linux, x64 or arm64.
- Node.js 20 or newer.
- For builds and simulation: the open FPGA toolchains from
  [OSS CAD Suite](https://github.com/YosysHQ/oss-cad-suite-build/releases) (Yosys, nextpnr, Apicula,
  Icarus Verilog, Verilator, openFPGALoader). Extract it and put its `bin` folder on your PATH, or let
  `doctor` tell you what it finds. Gowin's and other vendors' tools are optional.
- For programming: a supported board (for example Sipeed Tang Nano). Boards load into SRAM. On Windows
  the board's JTAG interface may need the WinUSB driver (Zadig); on Linux, a udev rule for the USB device.

## Verify a download

Each release lists the SHA-256 of its package, also in `SHA256SUMS`:

```
curl -LO https://github.com/Pinka/hw-studio-releases/releases/download/v0.1.0/hw-studio-0.1.0.tgz
sha256sum hw-studio-0.1.0.tgz      # Windows: certutil -hashfile hw-studio-0.1.0.tgz SHA256
```

## Licence

Free to use; all rights reserved. See [LICENSE.md](LICENSE.md). Third-party components and their
licences: [NOTICE](NOTICE), [LICENSES](LICENSES) and `THIRD-PARTY-LICENSES.txt` inside each package.
