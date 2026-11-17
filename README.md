# LV24 Scoop bucket

[Scoop](https://scoop.sh) manifests for LV24 apps on Windows.

```powershell
scoop bucket add lv24 https://github.com/LevapVeeskela/scoop-bucket
scoop install lv24/vigil
```

| App | What it is | Architectures | Source |
| --- | --- | --- | --- |
| [`vigil`](#vigil) | Local-first security auditor: CLI and stdio MCP server | `64bit`, `arm64` | [lv24-vigil](https://github.com/LevapVeeskela/lv24-vigil) |
| [`lv24-wifi-explorer`](#lv24-wifi-explorer) | Wi-Fi scanner with channel, signal and security analysis | `64bit` | [lv24-Wifi-Explorer](https://github.com/LevapVeeskela/lv24-Wifi-Explorer) |

## Vigil

Vigil runs 263 deterministic security rules over a repository (secrets,
injection, crypto, auth, web, config/IaC, CI, dependencies, MCP configuration,
release hardening) and can then use the model you configure to triage findings,
propose fixes and write a threat model. One standalone binary, no account, no
telemetry.

```powershell
scoop install lv24/vigil
vigil version
vigil scan . --no-llm --fail-on high    # deterministic rules: no key, no network
```

| | Command |
| --- | --- |
| Update | `scoop update vigil` |
| Remove | `scoop uninstall vigil` |
| Inspect the manifest | `scoop info lv24/vigil` |

The manifest downloads the release binary for your CPU straight from the
[GitHub release](https://github.com/LevapVeeskela/lv24-vigil/releases). Its
hashes are the `windows_amd64` and `windows_arm64` entries of that release's
`checksums.txt`, which is signed with cosign; how to verify it yourself:
[Verify a download](https://github.com/LevapVeeskela/lv24-vigil#verify-a-download).

Use it as an MCP server in Claude Code, Cursor, Codex or OpenCode:

```json
{
  "mcpServers": {
    "vigil": {
      "command": "vigil",
      "args": ["mcp"]
    }
  }
}
```

Documentation: [README](https://github.com/LevapVeeskela/lv24-vigil#readme) ·
[CLI](https://github.com/LevapVeeskela/lv24-vigil/blob/main/docs/cli.md) ·
[MCP](https://github.com/LevapVeeskela/lv24-vigil/blob/main/docs/mcp.md) ·
[agent index](https://github.com/LevapVeeskela/lv24-vigil/blob/main/llms.txt).

## LV24 WiFi Explorer

```powershell
scoop install lv24/lv24-wifi-explorer
```

The manifest mirrors the NSIS installer payload from the GitHub release. The
installer is unsigned, so Windows may show a SmartScreen prompt on first run.

## For AI agents

```json
{
  "bucket": "lv24",
  "bucket_url": "https://github.com/LevapVeeskela/scoop-bucket",
  "platform": "windows",
  "apps": {
    "vigil": {
      "install": "scoop install lv24/vigil",
      "binary": "vigil",
      "mcp": { "command": "vigil", "args": ["mcp"] },
      "deterministic_only": "vigil scan --no-llm",
      "json_report": "vigil scan --format json",
      "docs_index": "https://github.com/LevapVeeskela/lv24-vigil/blob/main/llms.txt"
    },
    "lv24-wifi-explorer": { "install": "scoop install lv24/lv24-wifi-explorer" }
  }
}
```

Add the bucket once, then install by `lv24/<app>`. Manifests live in
[`bucket/`](bucket); each one pins a release version and a SHA-256 per
architecture.

## Other ways to install Vigil

npm (`npm i -g lv24-vigil`), Homebrew, Linux packages, a container image and
release binaries:
[install guide](https://github.com/LevapVeeskela/lv24-vigil/blob/main/docs/install.md).
