# Releasing bruce-util-progress

How a version is published to crates.io. Each version is developed on a `vX.Y.Z` branch, published from it, tagged,
and merged to `main`. A published version can never be changed or removed, only yanked, which stops new projects from
choosing it, so everything is checked before `cargo publish`. The crates.io account and token are set up once, see
bruce-db's [docs/Release.md](https://github.com/bruceskingle/bruce-db/blob/main/docs/Release.md).

The checks, which CI runs too, see `.github/workflows/ci.yml`, except clippy and the dry run:

```sh
cd ~/git/bruce-util-progress
git switch v0.1.0
cargo fmt --all --check
cargo clippy --all-targets
cargo test
cargo deny check
cargo publish --dry-run
```

Commit and push, as `cargo publish` refuses a checkout with uncommitted changes, then publish:

```sh
git commit -am "Release 0.1.0"
git push
cargo publish
```

Check https://crates.io/crates/bruce-util-progress, and its documentation on https://docs.rs/bruce-util-progress,
which builds within a few minutes. Then tag the release and merge it to `main`:

```sh
git tag -a v0.1.0 -m "bruce-util-progress 0.1.0"
git push origin v0.1.0
git switch main
git merge --squash v0.1.0 && git commit -m "Release 0.1.0"
git push
```

The next version's branch is made when work on it starts, as its number depends on what it is: a fix, e.g.
`v0.1.1`, or something new, e.g. `v0.2.0`. It starts from the release's tag, with its version in `Cargo.toml`:

```sh
git switch -c v0.1.1 v0.1.0
```

Libraries which use it, e.g. bruce-db, depend on the published version, with a path to a checkout next to theirs for
working on both, `{ version = "0.1.0", path = "../bruce-util-progress" }`, which cargo leaves out when publishing them.
