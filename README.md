# LV24 Scoop bucket

Scoop manifests for LV24 apps.

## Install

```powershell
scoop bucket add lv24 https://github.com/LevapVeeskela/scoop-bucket
scoop install lv24/lv24-wifi-explorer
```

## Apps

| App | Manifest | Source |
| --- | --- | --- |
| LV24 WiFi Explorer | `bucket/lv24-wifi-explorer.json` | https://github.com/LevapVeeskela/lv24-Wifi-Explorer |

The manifest mirrors the NSIS installer payload from the GitHub release. The
installer is unsigned, so Windows may show a SmartScreen prompt on first run.
