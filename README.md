# LV24 Scoop bucket

Scoop manifests for LV24 apps.

## Install

```powershell
scoop bucket add lv24 https://github.com/LevapVeeskela/scoop-bucket
scoop install lv24/vigil
scoop install lv24/lv24-wifi-explorer
```

## Apps

| App | Manifest | Source |
| --- | --- | --- |
| Vigil | `bucket/vigil.json` | https://github.com/LevapVeeskela/lv24-vigil |
| LV24 WiFi Explorer | `bucket/lv24-wifi-explorer.json` | https://github.com/LevapVeeskela/lv24-Wifi-Explorer |

Vigil is a standalone Go binary, published for `64bit` and `arm64`. It is a
local-first security auditor; the same executable is a CLI and a stdio MCP
server.

The WiFi Explorer manifest mirrors the NSIS installer payload from the GitHub
release. The installer is unsigned, so Windows may show a SmartScreen prompt on
first run.
