# tofi-rs-auto-output

A soft fork of [tofi-rs](https://github.com/Gigas002/tofi-rs) that adds
automatic output selection, which upstream chose not to include. If you don't
need that specific feature, upstream is probably better suited. This fork tracks
upstream and is licensed under the same terms.

Please report any issues with this fork here rather than to upstream directly.
If a bug turns out to be in upstream as well, I'll forward it to upstream.

Credit to [Gigas002](https://github.com/Gigas002) for the upstream repo. Please
star the upstream project.

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

| File                                       | Purpose                                          |
| ------------------------------------------ | ------------------------------------------------ |
| `$XDG_CONFIG_HOME/tofi/config.toml`        | Behavioral settings (matching, history, output)  |
| `$XDG_CONFIG_HOME/tofi/themes/<name>.toml` | Visual settings (colors, fonts, window geometry) |

The theme file is referenced by the `[base].theme` key in the config, or overridden on the command line with `--theme <path>`.
