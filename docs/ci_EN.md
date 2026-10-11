# Pull requests and CI

The default branch is `master`. Required `CI` aggregates Go 1.27.1 native/compiler E2E, executable examples and race on Linux amd64, Windows amd64 and macOS arm64, plus compile-only checks for the other three supported architectures.

Tags and explicit full acceptance require all six native platforms, five race platforms, all three frozen Go versions, the same six release archives executed natively, and remote installation of the immutable commit. Version tags use one release orchestrator, avoiding duplicate full source runs. Compile-only checks are not native acceptance. Actions has no dedicated runner or external test credential prerequisite and only retains internal release artifacts.

See the [Chinese policy](ci.md) and [testing guide](testing.md).
