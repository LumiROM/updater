# LumiROM updater manifests

Update manifests served to the **LumiFota** app (`de.lumi.fota`).

The app fetches the manifest for its device from:

```
https://raw.githubusercontent.com/LumiROM/updater/refs/heads/main/<codename>.json
```

## Layout

| Path | Used by | Content |
|---|---|---|
| `<codename>.json` | LumiFota | Full-ROM releases, newest first (keeps history) |
| `ota/<codename>.json` | LumiFota (incremental) | Incremental OTA releases |

The files in this repository are **placeholders**: the LumiROM release workflow
regenerates and pushes them after every successful build (`ADD_LUMIFOTA`). Do not edit
them by hand unless you are fixing a broken release.

## Devices

`a22`, `a22x`, `a32`, `a32m`, `f22`, `m32`.

## Adding a device

1. Create `<codename>.json` with `rom_name`, `maintainer` and a `releases` array.
2. Create `ota/<codename>.json` with the same shape.
3. The workflow keeps both files updated from then on.

## Manifest shape

See `a32.json`. Minimum fields per release:

- `version`, `version_code`, `build_date`
- `changelog` (array of strings, shown in the app)
- `download.url`, `download.filename`, `download.size_bytes`
- optional: `download.sha256`, `build_fingerprint`, `oneui_version`, `security_patch`,
  `device_model`, `kernel_version`, `partition_layout`, `install_type`
