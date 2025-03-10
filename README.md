# Rust CSS Color Parser

[![crates.io](https://img.shields.io/crates/v/csscolorparser.svg)](https://crates.io/crates/csscolorparser)
[![Documentation](https://docs.rs/csscolorparser/badge.svg)](https://docs.rs/csscolorparser)
[![Build Status](https://github.com/mazznoer/csscolorparser-rs/workflows/Rust/badge.svg)](https://github.com/mazznoer/csscolorparser-rs/actions)
[![Build Status](https://travis-ci.org/mazznoer/csscolorparser-rs.svg?branch=master)](https://travis-ci.org/mazznoer/csscolorparser-rs)
[![codecov](https://codecov.io/gh/mazznoer/csscolorparser-rs/branch/master/graph/badge.svg)](https://codecov.io/gh/mazznoer/csscolorparser-rs)
[![Total Downloads](https://img.shields.io/crates/d/csscolorparser.svg)](https://crates.io/crates/csscolorparser)
![Lines of Code](https://tokei.rs/b1/github/mazznoer/csscolorparser-rs?category=code)

[Rust](https://www.rust-lang.org/) library to parse CSS color string as defined in the W3C's [CSS Color Module Level 4](https://www.w3.org/TR/css-color-4/).

## Supported Color Format

* [Named colors](https://www.w3.org/TR/css-color-4/#named-colors)
* RGB hexadecimal
     + Short format `#rgb`
     + Short format with alpha `#rgba`
     + Long format `#rrggbb`
     + Long format with alpha `#rrggbbaa`
* `rgb()` and `rgba()`
* `hsl()` and `hsla()`
* `hwb()`
* `hsv()` - not in CSS standard.

Not yet supported: `lab()`, `lch()`.

### Example Color Format

```text
transparent
gold
rebeccapurple
lime
#0f0
#0f0f
#00ff00
#00ff00ff
rgb(0,255,0)
rgb(0% 100% 0%)
rgb(0 255 0 / 100%)
rgba(0,255,0,1)
hsl(120,100%,50%)
hsl(120deg 100% 50%)
hsl(-240 100% 50%)
hsl(-240deg 100% 50%)
hsl(0.3333turn 100% 50%)
hsl(133.333grad 100% 50%)
hsl(2.0944rad 100% 50%)
hsla(120,100%,50%,100%)
hwb(120 0% 0%)
hwb(480deg 0% 0% / 100%)
hsv(120,100%,100%)
hsv(120deg 100% 100% / 100%)
```

## Usage

Add this to your `Cargo.toml`

```toml
csscolorparser = "0.4.0"
```

## Examples

Using `csscolorparser::parse()` function.

```rust
let c = csscolorparser::parse("rgb(100%,0%,0%)")?;

assert_eq!(c.rgba(), (1., 0., 0., 1.));
assert_eq!(c.rgba_u8(), (255, 0, 0, 255));
assert_eq!(c.to_hex_string(), "#ff0000");
assert_eq!(c.to_rgb_string(), "rgb(255,0,0)");
```

Using `parse()` method on string.

```rust
use csscolorparser::Color;

let c = "#ff00007f".parse::<Color>()?;

assert_eq!(c.rgba_u8(), (255, 0, 0, 127));
assert_eq!(c.to_hex_string(), "#ff00007f");
```

## Links

* [csscolorparser](https://github.com/mazznoer/csscolorparser) - Go version of this library.

