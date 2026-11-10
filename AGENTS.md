# Notes for Coding Agents

bruce-util-progress is a Rust crate for reporting the progress of long work, and cancelling it, between a library
doing the work and the app showing it. Its first user is bruce-db.

## Building

- Std only, with no dependencies: it must build for ESP-IDF targets as well as macOS, Linux and Windows. A dependency
  is added only with the maintainer's approval, see the README's licences and `deny.toml`.
- `cargo build` and `cargo test`. Format with `cargo fmt`, see `rustfmt.toml`; `cargo fmt --check` should pass.
- It is published to crates.io, so a published version can never be changed or removed. Do not publish; the
  maintainer does, see [docs/Release.md](docs/Release.md).

## Conventions

- **Errors** are formatted with `{error:#}`, their chain of causes, not `{error:?}`.
- **Comments** are doc comments in full sentences, saying what a thing is for and why.
