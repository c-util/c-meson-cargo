c-meson-cargo
=============

Meson Integration of Cargo based Rust Code

The c-meson-cargo project provides Meson-Build integration of Cargo-based Rust
code. It fully integrates crates.io dependency resolution into the meson build
system, including vendoring support, offline builds, meson-dist assembly, as
well as independent cargo project management.

This project is meant to be included as meson-subproject and then provides
hooks to include your custom Cargo.toml in the build. All output artifacts can
then be used in your Meson build configuration and be linked into other Meson
targets.

Since Meson does not provide external module support, nor custom functions, the
integration has a suboptimal API and requires integrators to take some extra
steps. However, this can be easily remedied in the future if Meson starts
providing more user-friendly external module support.

### Project

 * **Website**: <https://c-util.github.io/c-meson-cargo>
 * **Bug Tracker**: <https://github.com/c-util/c-meson-cargo/issues>

### Requirements

The requirements for this project are:

 * `cargo >= 1.60`
 * `coreutils`
 * `jq >= 1.6`
 * `meson >= 0.60`

### Repository:

 - **web**:   <https://github.com/c-util/c-meson-cargo>
 - **https**: `https://github.com/c-util/c-meson-cargo.git`
 - **ssh**:   `git@github.com:c-util/c-meson-cargo.git`

### License:

 - **Apache-2.0** OR **LGPL-2.1-or-later**
 - See AUTHORS file for details.
