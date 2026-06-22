---
notion-id: 24398e9c-907e-8009-b526-db64816c30ff
---
On Sprout (HP Victus):
```json
{
  "mcpServers": {
    "cloud-run": {
      "command": "npx",
      "args": [
        "-y",
        "@google-cloud/cloud-run-mcp"
      ]
    },
    "MCP_DOCKER": {
      "command": "docker",
      "args": [
        "mcp",
        "gateway",
        "run"
      ],
      "env": {
        "LOCALAPPDATA": "C:\\Users\\harve\\AppData\\Local",
        "ProgramData": "C:\\ProgramData",
        "ProgramFiles": "C:\\Program Files"
      }
    },
    "playwright-mcp": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "-y",
        "@smithery/cli@latest",
        "run",
        "@microsoft/playwright-mcp",
        "--key",
        "5782116a-7eeb-443c-9a23-eeffb5aa523d"
      ]
    }
  }
}

```