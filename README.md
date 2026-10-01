# tofi-rs-auto-output

A soft fork of [tofi-rs](https://github.com/Gigas002/tofi-rs) with automatic
output selection built-in. See
[this comment by the author of tofi-rs](https://github.com/Gigas002/tofi-rs/issues/58#issuecomment-5903204725)
on why my feature wasn't merged.

Any issues with tofi-rs-auto-output should be reported to this project rather
than to upstream.

[tofi-rs](https://github.com/Gigas002/tofi-rs) is itself a rust rewrite of
[tofi](https://github.com/philj56/tofi).

## Building

**System dependencies** (development headers required at compile time):

| Library        | Debian/Ubuntu package | Arch package   |
| -------------- | --------------------- | -------------- |
| Wayland client | `libwayland-dev`      | `wayland`      |
| Cairo          | `libcairo2-dev`       | `cairo`        |
| Pango          | `libpango1.0-dev`     | `pango`        |
| HarfBuzz       | `libharfbuzz-dev`     | `harfbuzz`     |
| xkbcommon      | `libxkbcommon-dev`    | `libxkbcommon` |
| pkg-config     | `pkg-config`          | `pkgconf`      |

The `clipboard` feature is opt-in; add `--features clipboard` to enable paste support.

**Note on binary name:** the installed binary is named `tofi`, the same as the upstream C program. Installing both will cause a PATH conflict — ensure only one is on your `PATH` at a time, or install one under a distinct prefix.

## Migrating from C tofi

See [CHANGELOG.md](CHANGELOG.md) for known differences and migration notes per release.

If something behaves differently from upstream, please [open an issue](https://github.com/theodorebje/tofi-rs/issues) with the compositor name, scale factor, and a minimal config to reproduce.

## Configuration

tofi reads its settings from two separate TOML files:

| File                                | Purpose                                          |
| ----------------------------------- | ------------------------------------------------ |
| `~/.config/tofi/config.toml`        | Behavioral settings (matching, history, output)  |
| `~/.config/tofi/themes/<name>.toml` | Visual settings (colors, fonts, window geometry) |

The theme file is referenced by the `[base].theme` key in the config, or overridden on the command line with `--theme <path>`.
