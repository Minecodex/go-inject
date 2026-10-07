# Pull requests and required CI

The default branch is `master`. Create a feature branch from the latest `origin/master`, push it to the organization repository, and open a pull request.

The default branch requires a pull request, the GitHub Actions check named `CI`, an up-to-date base, and resolved review conversations. Force pushes and branch deletion are prohibited, with no administrator bypass. No additional approving reviewer is currently required.

The `CI` job aggregates every native and race matrix result. All existing Go versions, operating systems, executable examples, unit tests and end-to-end checks remain mandatory. Failure, cancellation or an unexpected skipped matrix blocks merging. Release and remote installation workflows retain their separate acceptance requirements.

See the [Chinese policy](ci.md). Both native suites retain their explicit package timeouts; the slower compilers must finish real tests rather than being treated as successful on timeout.
