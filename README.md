# bruce-util-progress

Reporting the progress of long work, and cancelling it, between a library doing the work and the app showing it: a
`Progress` the work reports to and asks whether to stop, a `Cancel` token the app keeps to stop it, and the `Cancelled`
error the work returns when it has. Std only, with no dependencies, so that it builds for ESP-IDF devices as well as
computers.

Its first user is [bruce-db](https://github.com/bruceskingle/bruce-db), a record store, whose compaction and
conversions report through it, in whose repository it began.

License
=======

Licensed under either of

* Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
* MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

Contribution
------------

Unless you explicitly state otherwise, any contribution intentionally
submitted for inclusion in the work by you, as defined in the Apache-2.0
license, shall be dual licensed as above, without any additional terms or
conditions.
