# new slack mcp server


1. ローカルビルド後の直接実行
# ビルド後、ローカルのdist/index.jsを直接実行
cd src/slack

# 環境変数を設定して実行
```bash
SLACK_BOT_TOKEN="xoxb-your-bot-token" \
SLACK_TEAM_ID="T01234567" \
node dist/index.js
```

1. Dockerを使用したローカルビルド実行
# ローカルでビルドしたDockerイメージを実行
```bash
docker run -i --rm \
  -e SLACK_BOT_TOKEN="xoxb-your-bot-token" \
  -e SLACK_TEAM_ID="T01234567" \
  mcp/slack
```

ローカルビルドを使用する場合:
```json
{
  "mcpServers": {
    "slack": {
      "command": "node",
      "args": ["/Users/takuro.saito/work/servers-archived/src/slack/dist/index.js"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-your-bot-token",
        "SLACK_TEAM_ID": "T01234567",
        "SLACK_CHANNEL_IDS": "C01234567,C76543210"
      }
    }
  }
}
```

dockerの場合
```json
{
  "mcpServers": {
    "slack": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "mcp/slack"
      ],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-your-bot-token",
        "SLACK_TEAM_ID": "T01234567",
        "SLACK_CHANNEL_IDS": "C01234567,C76543210"
      }
    }
  }
}
```
