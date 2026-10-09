# Pull requests and required CI

The default branch is `master`. Create a feature branch from the latest `origin/master`, push it to the organization repository, and open a pull request.

The default branch requires a pull request, the GitHub Actions check named `CI`, an up-to-date base, and resolved review conversations. Force pushes and branch deletion are prohibited, with no administrator bypass. No additional approving reviewer is currently required.

The `CI` job aggregates native and race checks on Go 1.27.1 for every supported native platform. Executable examples, unit tests and end-to-end checks remain mandatory. Failure, cancellation or an unexpected skipped matrix blocks merging.

Each version tag starts release acceptance, including the full Go 1.25.8 / 1.26.8 / 1.27.1 source matrix, six release archives executed on matching native hosts, and remote installation of the immutable source commit. The `Release CI` gate requires every stage to succeed before maintainers publish the release. Release acceptance uploads Actions artifacts only; it does not publish a public release. No scheduled workflow is used. The manual `full` CI input also checks the complete compatibility matrix before tagging.

See the [Chinese policy](ci.md). Both native suites retain their explicit package timeouts; the slower compilers must finish real tests rather than being treated as successful on timeout.
