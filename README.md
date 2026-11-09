# T3 配置版本记录

此仓库用于记录本机 T3 配置，采用 `.gitignore` 白名单规则。

纳入版本管理：

- `userdata/settings.json`：用户设置、模型偏好和 provider 配置。
- `userdata/keybindings.json`：快捷键配置。
- `userdata/themes/`：自定义主题；空目录不会被 Git 记录。
- `.gitignore`、`README.md`，以及将来添加的根目录 `AGENTS.md`。

默认忽略：

- `caches/`、`logs/`、`userdata/logs/`：缓存与日志。
- `runtime/`、`tools/`：运行程序及下载的工具。
- `worktrees/`：独立工作目录。
- `userdata/secrets/`：凭据。
- `userdata/attachments/`、`userdata/server-browser/`：附件及浏览器数据。
- `userdata/*.sqlite*`：数据库、锁及事务文件。
- `usage-host-id`、`userdata/anonymous-id`、`userdata/environment-id`：本机标识。
- 运行信息、模型清单缓存、用量统计缓存、迁移标记及配置备份。
- 其他未加入白名单的新文件，以及 `*.bak`、`*.tmp`、`*.swp`、`*.swo`、`*~`。

新增需要记录的配置时，在 `.gitignore` 中补充白名单。凭据应保留在被忽略的凭据目录中，不要写入已跟踪的配置。恢复配置前先退出 T3；本仓库不包含会话、附件和登录状态。

当前启用的 provider：

- `codex`：Codex，保留原配置。
- `codex_opencode_go`：OpenCode Go，使用 Codex 驱动，保留原配置。
- `pi`：Pi，使用 Pi 驱动，默认使用 DeepSeek，模型范围见 `userdata/settings.json` 的 `customModels`。

`pi` 使用 `/home/dell/.pi/agent/bin/pi`，通过 `PI_CODING_AGENT_DIR` 复用 `/home/dell/.pi/agent` 中的设置和认证。`--models` 指定四个可切换模型，混用 `opencode-go` 与 `openai` 两个上游。Pi 的安装与凭据由 `~/.pi` 单独管理，不复制到此仓库；迁移到其他机器时需要调整路径并配置认证。

模型范围与现有 Codex、OpenCode Go 实例的选择对齐。2026-11-03 核对来源为本机 Codex app-server 的 `account/read`、`model/list`，以及 [OpenCode Go 实时模型目录](https://opencode.ai/inference/go/v1/models)；四个选定模型都在相应目录中。套餐说明见 [OpenAI 官方模型文档](https://learn.chatgpt.com/docs/models?surface=web) 和 [OpenCode Go 文档](https://opencode.ai/v2/docs/console/go/)。Pi 的本地模型缓存不作为套餐权限依据。
