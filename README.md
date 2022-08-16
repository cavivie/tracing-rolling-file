# tracing-rolling-file

[![tracing-rolling-file on GitHub Actions](https://github.com/cavivie/tracing-rolling-file/actions/workflows/test.yaml/badge.svg)](https://github.com/cavivie/tracing-rolling-file/actions?query=workflow%3Atest)
[![tracing-rolling-file on crates.io](https://img.shields.io/crates/v/tracing-rolling-file.svg)](https://crates.io/crates/tracing-rolling-file)
[![tracing-rolling-file on docs.rs](https://docs.rs/tracing-rolling-file/badge.svg)](https://docs.rs/tracing-rolling-file)
[![GitHub: cavivie/tracing-rolling-file](https://img.shields.io/badge/GitHub--cavivie-tracing--rolling--file-lightgrey?style=flat-square)](https://github.com/cavivie/tracing-rolling-file)
![license: MIT or Apache-2.0](https://img.shields.io/badge/license-MIT%20or%20Apache--2.0-red?style=flat-square)
![minimum rustc: 1.42](https://img.shields.io/badge/minimum%20rustc-1.42-yellowgreen?logo=rust&style=flat-square)

A rolling file appender with customizable rolling conditions, based on [rolling-file](https://github.com/Axcient/rolling-file-rs).
Includes built-in support for rolling conditions on date/time
(daily, hourly, every minute) and/or size.

Follows a Debian-style naming convention for logfiles,
using basename, basename.1, ..., basename.N where N is
the maximum number of allowed historical logfiles.

This is useful to combine with the [tracing](https://crates.io/crates/tracing) crate and
[tracing_appender::non_blocking::NonBlocking](https://docs.rs/tracing-appender/latest/tracing_appender/non_blocking/index.html) -- use it
as an alternative to [tracing_appender::rolling::RollingFileAppender](https://docs.rs/tracing-appender/latest/tracing_appender/rolling/struct.RollingFileAppender.html).

## Examples

```rust
use tracing_rolling_file::*;
let file_appender = RollingFileAppenderBase::new(
    "/var/log/myprogram",
    RollingConditionBase::new().daily(),
    9
).unwrap();
```

## Development

Must pass latest stable clippy, be formatted with nightly rustfmt, and pass unit tests:

```
cargo +nightly fmt
cargo clippy --all-targets
cargo test
```

## License

Dual-licensed under the terms of either the MIT license or the Apache 2.0 license.
