# Changelog

All notable maintenance changes to this repository are documented here.

The project uses [Semantic Versioning](https://semver.org/). Historical display-driver updates predate this maintenance policy.

## [Unreleased]

### Changed
- Scoped installer validation to model-specific installer scripts rather than unrelated shell helpers.
- Added a bounded validation runtime so malformed installer trees cannot consume CI indefinitely.
- Documented that automated installer validation checks shell syntax and executable bits only; hardware, kernel, and panel compatibility still require target-device testing.

## [0.1.1] - 2026-08-20

### Changed
- Reworked the README around the repository's current maintenance status and model-specific installer architecture.
- Added safer installation guidance and explicit warnings for low-level boot/display configuration changes.
- Added clear manual update, revision pinning, and rollback instructions.
- Documented why unattended automatic updates are intentionally not enabled until versioned releases and validated rollback support exist.
