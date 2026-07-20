Optimized tool selection我把它整理成可直接写入 shell 配置文件的版本，并顺手补上 macOS 常见的配置位置。

可以，下面这份适合直接粘贴到 shell 配置文件里，且会永久生效。

## 适用于 zsh 的版本
把下面内容追加到你的 shell 配置文件里：

- macOS 常见位置：
  - ~/.zshrc

```bash
# Claude Code + Vertex AI 配置
export CLAUDE_CODE_USE_VERTEX=1
export ANTHROPIC_VERTEX_PROJECT_ID="your-gcp-project-id"
export CLOUD_ML_REGION="us-east5"

# 可选：如果你使用的是服务账号 JSON 文件
export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.config/gcp/vertex-service-account.json"

# 可选：如果你想为某些模型单独指定区域
# export VERTEX_REGION_CLAUDE_3_7_SONNET="us-east5"
# export VERTEX_REGION_CLAUDE_3_5_SONNET="us-east5"
# export VERTEX_REGION_CLAUDE_HAIKU_4_5="us-east5"
```

## 让配置立即生效
执行：

```bash
source ~/.zshrc
```

## 如果你还没有服务账号文件
可以先创建目录并把 JSON 文件放进去：

```bash
mkdir -p ~/.config/gcp
```

然后把你的 GCP service account JSON 文件放到：

```bash
~/.config/gcp/vertex-service-account.json
```

## 如果你想更稳妥一点
也可以把项目 ID 和凭据路径写成更显式的形式，避免后续改动时混乱：

```bash
export CLAUDE_CODE_USE_VERTEX=1
export ANTHROPIC_VERTEX_PROJECT_ID="your-gcp-project-id"
export CLOUD_ML_REGION="us-east5"
export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.config/gcp/vertex-service-account.json"
```

## 额外建议
如果你是第一次配置 GCP 凭据，建议同时执行：

```bash
gcloud auth application-default login
```

这样可以避免只靠 `GOOGLE_APPLICATION_CREDENTIALS` 时出现认证问题。

如果你愿意，我也可以继续帮你整理成“适合直接复制到 ~/.zshrc 的完整版本”，顺便把注释写得更适合你自己长期使用。