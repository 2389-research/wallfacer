# Wallfacer

A Rust and SDL2 application for projection mapping and demoscene effects. It renders effects such as plasma, fire, tunnels, and starfields, with scene regions and an interactive calibration mode. Raspberry Pi is a target; the application also uses SDL2 for a desktop display.

## Build and run

Install Rust (the manifest declares a minimum of 1.75), Cargo, and the SDL2 development library for your platform. From the repository root:

```sh
cargo build --release
cargo run --release -- --help
cargo run --release -- --resolution 1280x720
```

The last command opens a graphics window. `--effect N` selects a zero-based effect, `--rotate 90` rotates output, and `--scene FILE` selects the scene file. Without `--scene`, the app uses `scene.json` in the current working directory. See `--help` for the full option list.

Tab switches between effects and calibration. In calibration mode, `S` saves the scene and `L` loads it; Esc quits. Use a separate scene file when experimenting with an existing setup.

## Development

```sh
make check
make test
```

`make` runs formatting checks, Clippy, tests, and a debug build. See the [Makefile](Makefile) for the remaining development targets. `make pi` targets `aarch64-unknown-linux-gnu` and requires a matching cross-compilation toolchain and SDL2 libraries; the target alone does not provision those dependencies.

The [ideas directory](doc/ideas/README.md) contains design notes and future ideas.
