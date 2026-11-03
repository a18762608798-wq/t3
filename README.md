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
