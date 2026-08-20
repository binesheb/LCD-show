# LCD-show

Legacy Raspberry Pi display-driver collection for a range of LCDWiki/GoodTFT panels.

> **Maintenance status:** preserved for existing installations. The bundled scripts were last updated in April 2021 and may modify boot configuration, X11/input settings, kernel modules, or trigger a reboot. Review the selected script before running it, especially on current Raspberry Pi OS releases.

## What is in this repository

The repository contains model-specific installer scripts such as `LCD24-show`, `LCD35-show`, `LCD5-show`, `LCD7B-show`, DPI panel installers, and rotation helpers. It is not a single generic driver: choose the script that matches the exact display model.

## Before installing

1. Back up the Raspberry Pi or at least `/boot`/`/boot/firmware` and important configuration files.
2. Confirm the exact display model and Raspberry Pi OS version.
3. Inspect the installer before running it with elevated privileges.
4. Expect some installers to reboot the device.

## Install from this repository

```bash
git clone https://github.com/binesheb/LCD-show.git
cd LCD-show
git status --short
chmod +x LCD24-show   # replace with the required installer
sudo ./LCD24-show
```

Replace `LCD24-show` with the script for the connected panel. Some historical panel names and commands remain documented in the scripts themselves.

## Rotation

Where supported, installers historically accept a rotation argument:

```bash
sudo ./LCD24-show 90
```

Valid values are typically `0`, `90`, `180`, and `270`. If the display is already configured, use the repository's `rotate.sh` helper when present and supported by the selected driver.

## Updates

### Safe automatic update policy

Do **not** enable unattended updates for these display drivers. A driver update can change low-level boot and display configuration, so automatic upgrades should be performed only after a tested, versioned release and a device-specific rollback path exist.

### Manual update

From an existing clone:

```bash
cd /path/to/LCD-show
git fetch --tags --prune
git status --short
git pull --ff-only
```

For reproducibility, pin a known revision instead of following the moving branch:

```bash
git fetch --tags
git checkout <tag-or-commit>
```

To roll back:

```bash
git checkout <previous-tag-or-commit>
```

Re-run the relevant installer only after reviewing its changes and confirming compatibility with the operating system and panel.

## Versioning and releases

Maintenance changes follow Semantic Versioning. Patch releases are for documentation, packaging, and compatible fixes; minor releases add compatible capabilities; major releases indicate incompatible installation or support changes. Historical upstream-style version notes are retained in repository history, while current maintenance entries are recorded in `CHANGELOG.md`.

## Support scope

This fork does not claim compatibility with every current Raspberry Pi OS/kernel combination. When reporting a problem, include:

- Raspberry Pi model
- exact display/panel model
- operating system and kernel version
- installer script used
- relevant console output

## Next modernization priorities

- Audit each installer against current Raspberry Pi OS layouts and kernel interfaces.
- Add compatibility checks and explicit backups before configuration changes.
- Replace broad permission changes and destructive setup where possible.
- Establish tested, tagged releases before any automated updater is introduced.
