# INSTALL.md — 安装 paper-search 工具

本项目使用 `paper-search` skill 检索 / 下载 / 阅读学术论文。该 skill 调用本地 `paper-search-mcp` CLI（由 `uv run` 启动）。**本文件是安装该 CLI 的唯一权威说明。**

> **给 AI agent**：读完本文件后可直接执行下文命令完成安装，**无需任何手动路径替换**。所有命令都在 **项目根目录**（本文件所在目录，与 `CLAUDE.md` 同级）执行。

---

## 0. 它会装什么

| 组件 | 说明 |
|---|---|
| `uv` | Python 包 / 任务运行器，用于免手动建虚拟环境启动 CLI |
| `paper-search-mcp` | 上游 CLI 工具，clone 到 `.claude/tools/paper-search-mcp` |

`paper-search` skill 里的命令使用**相对路径** `.claude/tools/paper-search-mcp`，因此装好后无需任何机器特定配置即可工作。

`.claude/tools/` 已在 `.gitignore` 中，**不会随仓库分发**——所以每个新 clone 的环境都需要按本文安装一次。这正是本文件存在的意义。

---

## 1. 前置条件

- Python ≥ 3.10（`python --version` 检查）
- git
- 可访问 GitHub（clone 仓库）与 PyPI（uv 解析依赖）

---

## 2. Agent 快速安装（复制即用）

> 在**项目根目录**依次执行：

```bash
# 2.1 安装 uv（跨平台，最简；本机已有 pip 即可）
pip install uv

# 2.2 clone 工具仓库到项目内
git clone https://github.com/openags/paper-search-mcp.git .claude/tools/paper-search-mcp

# 2.3 验证（首次运行 uv 会自动创建虚拟环境并安装依赖，约 30s~2min）
uv run --directory .claude/tools/paper-search-mcp paper-search sources
```

第 3 步应输出一段 JSON，其中 `sources` 数组包含 **21 个数据源**（arxiv、pubmed、semantic、crossref…），即表示安装成功。

---

## 3. 分平台安装 uv（备选）

若 `pip install uv` 不适用，按平台任选一种：

**Windows (PowerShell)**：
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**macOS / Linux**：
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows winget**：
```bash
winget install --id=astral-sh.uv -e
```

装完验证：`uv --version`

---

## 4. 可选：配置 API key（提升稳定性）

多数源（arXiv、PubMed、Semantic Scholar、Crossref…）无需 key 即可用。在 `.claude/tools/paper-search-mcp/.env` 填写可提升速率与覆盖（该文件已被 `.gitignore` 忽略，安全）：

```dotenv
PAPER_SEARCH_MCP_UNPAYWALL_EMAIL=你的邮箱        # 启用 Unpaywall OA 回退（填邮箱才生效）
PAPER_SEARCH_MCP_CORE_API_KEY=                   # core.ac.uk 免费申请
PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY=       # semanticscholar.org 免费
```

完整变量列表见上游仓库 README。

---

## 5. 验证 skill 可用

CLI 装好后，在 **Claude Code** 会话里用自然语言即可自动触发 skill，例如：

- "搜一下 VLA 领域最近的论文，arxiv 和 semantic 各 5 篇"
- "下载 arxiv 论文 2202.09061 的 PDF"

也可直接手动验证 CLI（不依赖 Claude Code）：
```bash
uv run --directory .claude/tools/paper-search-mcp paper-search search "transformer" -n 1 -s arxiv
```
返回 JSON 论文列表即正常。

---

## 6. 常见问题

| 问题 | 原因 / 解决 |
|---|---|
| `uv: command not found` | uv 未装或不在 PATH；重开终端，或临时用 `python -m uv ...` 代替 |
| `git clone` 超时 / 失败 | 网络问题；配置代理或使用 GitHub 镜像 |
| 首次 `uv run` 很慢 | 正常现象，正在下载依赖；后续运行会命中缓存，秒级启动 |
| 提示 `paper-search` 不是命令 | 确认 clone 目标路径正是 `.claude/tools/paper-search-mcp`，且该目录下有 `pyproject.toml` |
| Python 版本过低报错 | 需 ≥ 3.10；`uv run` 一般会自动拉取合适版本的 Python |
| Windows 下路径报错 | 命令在 git bash / WSL / PowerShell 均可；正斜杠路径通用，不要混用反斜杠 |
| stderr 出现 `No CORE API key` 等警告 | **无害**，仅提示部分源受限，可忽略；想消除按第 4 节配 key |

---

## 7. 卸载

```bash
rm -rf .claude/tools/paper-search-mcp
pip uninstall uv          # 可选，仅当不再需要 uv 时
```

---

## 8. 参考

- 上游仓库：https://github.com/openags/paper-search-mcp
- 项目规则：[`CLAUDE.md`](CLAUDE.md)
- skill 定义：[`.claude/skills/paper-search/SKILL.md`](.claude/skills/paper-search/SKILL.md)
