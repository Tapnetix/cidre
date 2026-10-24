# RecapIt compatibility patch

This change applies to upstream yury/cidre 0.11.3 at
`a9587fa1d4ff6f0d5d082849ae7c62880fd739f7` under the MIT license.

In `src/core_audio/hardware.rs`, the `Tap` import and `System::taps()` are
conditional on the existing `macos_14_2` feature. Upstream gates the `Tap`
type on that feature but leaves these references unconditional, which breaks
builds using RecapIt's supported `macos_13_3` feature set. The change aligns
the API references with the type's availability. It does not enable
`macos_14_2` or alter runtime tap resolution.
