# Ekairos Canvas

<img src="./logo.png" alt="Ekairos Canvas Logo" width="120" align="left">

**An infinite canvas whiteboard built with Rust and WebGPU.**

Forked from [PatWie/drafft-ink](https://github.com/PatWie/drafft-ink) and adapted as the open-source canvas base for Ekairos.

Cross-platform (Linux, Windows, macOS, browser, mobile). Real-time collaboration via CRDTs. No account required. Self-hostable with a single binary.

<br clear="left"/>

<img width="874" alt="Screenshot" src="./screenshot.png" />

---

## Current Status

- Public fork created for Ekairos experimentation
- WebAssembly build working locally on Windows
- Rust/WebGPU stack compiles to `web/pkg`
- ReX/LaTeX rendering is temporarily disabled to unblock Windows builds

---

## Features

- Shapes and drawing
- Smart guides and snapping
- Text editing
- Images
- Collaboration via CRDTs
- Open formats
- Touch support
- Sketch-style rendering

---

## Installation

### Desktop

```bash
cargo run --release
```

### Web (Local)

```bash
cd crates/drafftink-app
wasm-pack build --target web --out-dir ../../web/pkg --release --no-default-features
cd ../../web
python -m http.server 8080
```

### Collaboration Server

```bash
cargo build --release -p drafftink-server
./target/release/drafftink-server
```

---

## Fork Notes

- This fork is intended to become the open-source base for `ekairos-canvas`.
- The current Windows blocker was a git dependency on `KenyC/ReX` that contains invalid NTFS paths.
- For now, math shapes render as placeholders until that dependency is replaced or vendored cleanly.

---

## Architecture

```text
crates/
  drafftink-core/     Canvas state, shapes, CRDT sync, snapping logic
  drafftink-render/   Vello-based GPU rendering, text layout
  drafftink-app/      Application logic, UI, event handling
  drafftink-server/   WebSocket collaboration server
  drafftink-widgets/  Custom UI components
```

---

## License

**AGPLv3** - Use it, modify it, host it. Keep it open.
