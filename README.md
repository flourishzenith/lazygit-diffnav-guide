# LazyGit & DiffNav 使用指南

> 高效的终端 Git 工具完全指南

---

## 📚 目录

- [工具介绍](#工具介绍)
- [LazyGit 完全指南](#lazygit-完全指南)
- [DiffNav 完全指南](#diffnav-完全指南)
- [集成使用](#集成使用)
- [常见问题](#常见问题)

---

## 工具介绍

### 🦥 LazyGit

**简介**：一个用 Go 编写的简单终端 UI for Git 命令

**官网**：https://github.com/jesseduffield/lazygit

**Stars**：73,000+

**特点**：
- 🎨 美观的终端界面
- ⚡ 快速操作 Git
- 🔍 可视化状态、日志、diff
- ⌨️ 键盘快捷键驱动
- 📦 跨平台支持（Linux/macOS/Windows）

**适合场景**：
- 日常 Git 操作
- 需要可视化 Git 状态
- 提升工作效率

### 🐳 DiffNav

**简介**：基于 delta 的 Git diff 分页器，带文件树（类似 GitHub）

**官网**：https://github.com/dlvhdr/diffnav

**Stars**：865+

**特点**：
- 📁 文件树导航
- 🎨 语法高亮（基于 delta）
- 🔍 快速搜索文件
- ⚡ 高性能 diff 浏览
- 🌲 类似 GitHub 的 diff 视图

**适合场景**：
- 查看大型代码变更
- 需要文件树结构
- 追求美观的 diff 显示

---

## LazyGit 完全指南

### 安装

#### macOS
```bash
brew install lazygit
```

#### Linux
```bash
# Debian/Ubuntu
sudo apt install lazygit

# Fedora
sudo dnf install lazygit

# Arch Linux
sudo pacman -S lazygit

# 从源码安装
go install github.com/jesseduffield/lazygit@latest
```

#### Windows
```powershell
# 使用 Scoop
scoop install lazygit

# 使用 Chocolatey
choco install lazygit
```

#### 验证安装
```bash
lazygit --version
```

---

### 快速开始

#### 1. 基础使用

在 Git 仓库目录下运行：
```bash
cd /path/to/your/repo
lazygit
```

#### 2. 界面布局

```
┌─────────────────────────────────────────┐
│  Main Panel (文件状态)                   │
│  ├─ Staged files    (已暂存)            │
│  ├─ Unstaged files  (未暂存)            │
│  └─ Stash files     (储藏)              │
├─────────────────────────────────────────┤
│  Files Panel (文件列表)                  │
├─────────────────────────────────────────┤
│  Commits Panel (提交历史)                │
├─────────────────────────────────────────┤
│  Options Panel (可选操作)                │
└─────────────────────────────────────────┘
```

---

### 核心功能

#### 1. 文件操作

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `Space` | 暂存/取消暂存 | 切换文件状态 |
| `Enter` | 查看 diff | 查看文件变更 |
| `d` | 删除文件 | 删除选中文件 |
| `e` | 编辑文件 | 打开编辑器 |
| `o` | 打开文件 | 用系统默认打开 |
| `i` | 忽略文件 | 添加到 .gitignore |

#### 2. 提交操作

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `c` | 提交 | 创建新提交 |
| `C` | 直接提交 | 跳过编辑器 |
| `a` | 修改提交 | 修改最新提交 |
| `A` | 修改提交（包含暂存） | 添加所有变更 |
| `f` | 修复提交 | 创建 fixup! 提交 |

#### 3. 分支操作

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `b` | 切换分支 | 查看和切换分支 |
| `n` | 新建分支 | 创建新分支 |
| `D` | 删除分支 | 删除选中分支 |
| `m` | 合并分支 | 合并到当前分支 |
| `r` | 变基 | Rebase 当前分支 |

#### 4. 远程操作

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `p` | 推送 | 推送到远程 |
| `P` | 强制推送 | 强制推送（慎用） |
| `f` | 拉取 | 从远程拉取 |
| `F` | 拉取并变基 | Fetch + rebase |

#### 5. 其他操作

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `s` | 储藏 | Stash 变更 |
| `S` | 储藏（包含未跟踪） | Stash 所有 |
| `k` | 丢弃变更 | 丢弃文件变更 |
| `x` | 自定义命令 | 执行自定义命令 |
| `q` | 退出 | 退出 LazyGit |

---

### 高级功能

#### 1. 交互式 Rebase

```bash
# 启动 LazyGit
lazygit

# 步骤：
1. 按 `v` 进入提交视图
2. 选择要 rebase 的提交
3. 按 `r` 选择 rebase 模式
4. 选择操作：
   - `r` - rebase
   - `e` - edit
   - `s` - squash
   - `f` - fixup
   - `d` - drop
```

#### 2. 自定义配置

创建配置文件 `~/.config/lazygit/config.yml`：

```yaml
# GUI 配置
gui:
  # 主题颜色
  theme:
    activeBorderColor:
      - "#ff00ff"  # 活跃边框颜色
    inactiveBorderColor:
      - "#ffffff"  # 非活跃边框颜色
    optionsTextColor:
      - "#00ff00"  # 选项文本颜色

  # 显示文件数量
  showFileTree: true
  showBranchCommitHash: true

  # 分支排序
  branchLogGraph: "style"

# 键盘绑定
keybinding:
  universal:
    # 自定义快捷键
    cancel: "<esc>"
    confirm: "<enter>"
    quit: "q"

# 更新配置
update:
  method: "background"  # 后台更新
  days: 14              # 每 14 天检查

# 禁用功能
disableStartupPopups: true

# 提交信息格式
commitLength:
  show: true
```

#### 3. 自定义命令

在配置文件中添加：

```yaml
customCommands:
  - key: "a"
    command: "git commit --amend --no-edit"
    description: "修改最新提交"
    context: "files"

  - key: "F"
    command: "git fetch --all --prune"
    description: "获取所有远程分支并清理"
    context: "files"

  - key: "<c-r>"
    command: "git rebase -i HEAD~{{ .Form.RemoteBranch }}"
    description: "交互式 rebase"
    context: "commits"
    prompts:
      - type: "input"
        title: "Rebase 多少次提交？"
        key: "RemoteBranch"
```

#### 4. 过滤和搜索

```bash
# 在 LazyGit 中
/        # 搜索文件
'        # 搜索提交
Ctrl-f   # 过滤文件
```

#### 5. 分支比较

```bash
# 查看分支差异
b (查看分支)
选择两个分支进行比较
```

---

### 实用技巧

#### 1. 快速提交工作流

```
1. lazygit              # 打开 LazyGit
2. 选择文件
3. Space                # 暂存文件
4. c                    # 提交
5. 输入提交信息
6. Enter                # 确认
7. p                    # 推送
```

#### 2. 撤销提交

```
1. v                    # 查看提交历史
2. 选择要撤销的提交
3. a                    # 修改提交
4. 调整变更
5. c                    # 重新提交
```

#### 3. 清理分支

```
1. b                    # 查看分支
2. 选择要删除的分支
3. D                    # 删除分支
```

#### 4. 储藏临时变更

```
1. 选择要储藏的文件
2. s                    # 储藏
3. 需要时按 S 恢复
```

---

### 集成工具

#### 1. 与 Neovim 集成

使用插件 `kdheepak/lazygit.nvim`：

```lua
-- init.lua
require('telescope').load_extension('lazygit')

-- 快捷键映射
vim.api.nvim_set_keymap('n', '<leader>gg', ':LazyGit<CR>', {noremap = true})
```

#### 2. 与 tmux 集成

```bash
# 在 tmux.conf 中添加
bind-key g new-window -n lazygit lazygit
```

#### 3. 与 fzf 集成

```bash
# 快速跳转到仓库目录并打开 LazyGit
lazygit() {
  cd $(find ~/projects -type d -name .git | sed 's/.git$//' | fzf) && lazygit
}
```

---

## DiffNav 完全指南

### 安装

#### 前置要求

**需要先安装 delta**（Git diff 高亮工具）：

```bash
# macOS
brew install git-delta

# Linux
cargo install git-delta

# 或从源码
cargo install git-delta
```

#### 安装 DiffNav

```bash
# 使用 go install
go install github.com/dlvhdr/diffnav@latest

# 验证安装
diffnav --version
```

---

### 配置 Git

#### 1. 设置 Delta

在 `~/.gitconfig` 中添加：

```ini
[core]
    pager = delta

[interactive]
    diffFilter = delta --color-only

[delta]
    navigate = true
    light = false
    line-numbers = true
    syntax-theme = Monokai Extended

[merge]
    conflictstyle = diff3

[diff]
    colorMoved = default
```

#### 2. 配置 DiffNav

创建 `~/.config/git/config`：

```ini
[pager]
    diff = diffnav
    show = diffnav
    log = diffnav
```

或设置环境变量：

```bash
export GIT_PAGER=diffnav
```

---

### 快速开始

#### 1. 基础使用

```bash
# 查看 diff
git diff

# 查看提交
git show

# 查看日志
git log
```

#### 2. 界面布局

```
┌─────────────────────────────────────────┐
│  File Tree Panel                        │
│  ├─ src/                                │
│  │   ├─ main.rs                         │
│  │   └─ utils.rs                        │
│  └─ tests/                              │
│      └─ test.rs                         │
├─────────────────────────────────────────┤
│  Diff Panel                             │
│  ├─ old code                            │
│  ├─ separator                           │
│  └─ new code                            │
├─────────────────────────────────────────┤
│  Status Bar                             │
│  File: src/main.rs | Line: 10-20        │
└─────────────────────────────────────────┘
```

---

### 核心功能

#### 1. 文件树导航

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `↑/↓` | 上下移动 | 在文件树中移动 |
| `Enter` | 查看文件 | 查看选中文件的 diff |
| `←/→` | 折叠/展开 | 折叠或展开目录 |
| `/` | 搜索 | 搜索文件名 |
| `n` | 下一个搜索结果 | 跳转到下一个 |
| `N` | 上一个搜索结果 | 跳转到上一个 |

#### 2. Diff 导航

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `Ctrl-n` | 下一个变更 | 跳转到下一个 diff 块 |
| `Ctrl-p` | 上一个变更 | 跳转到上一个 diff 块 |
| `Ctrl-f` | 向下滚动 | 向下滚动一页 |
| `Ctrl-b` | 向上滚动 | 向上滚动一页 |
| `Space` | 向下滚动 | 向下滚动半页 |
| `b` | 向上滚动 | 向上滚动半页 |
| `d` | 半页向下 | 向下滚动半页 |
| `u` | 半页向上 | 向上滚动半页 |
| `q` | 退出 | 退出 DiffNav |

#### 3. 其他操作

| 快捷键 | 功能 | 说明 |
|--------|------|------|
| `h` | 帮助 | 显示帮助信息 |
| `g` | 跳转 | 跳转到指定行 |
| `G` | 跳转到底部 | 跳转到文件末尾 |
| `zz` | 居中 | 将当前行居中显示 |

---

### 高级功能

#### 1. 自定义配置

创建 `~/.config/diffnav/config.yml`：

```yaml
# 颜色主题
theme:
  # 文件树颜色
  fileTree:
    foreground: "#c0caf5"
    background: "#1a1b26"

  # Diff 颜色
  added:
    foreground: "#9ece6a"
    background: "#2b3328"

  removed:
    foreground: "#f7768e"
    background: "#33262d"

  # 语法高亮
  syntaxTheme: "Monokai Extended"

# 界面设置
ui:
  # 显示行号
  showLineNumbers: true

  # 显示空白字符
  showWhitespace: false

  # Tab 宽度
  tabWidth: 4

  # 文件树宽度
  fileTreeWidth: 30

# 性能设置
performance:
  # 大文件阈值（MB）
  largeFileThreshold: 10

  # 禁用语法高亮
  disableSyntaxHighlighting: false
```

#### 2. Delta 配置优化

在 `~/.gitconfig` 中：

```ini
[delta]
    # 导航功能
    navigate = true

    # 暗色主题
    light = false

    # 显示行号
    line-numbers = true

    # 语法主题
    syntax-theme = Monokai Extended

    # 侧边栏宽度
    side-by-side = true

    # 显示文件名
    file-style = "yellow ul"

    # 显示修改行号
    hunk-header-style = "file"

    # 零行合并
    zero-style = "dim syntax"

    # 显示统计信息
    line-numbers-left-format = "{nm:>4} "
    line-numbers-right-format = " {np:>4}"
```

#### 3. 针对特定文件类型的配置

```ini
[delta "latex"]
    word-diff = true

[delta "json"]
    word-diff = true

[delta "python"]
    syntax-theme = "Monokai Extended"
```

---

### 实用技巧

#### 1. 查看大文件 diff

```bash
# 自动分页
git diff large_file.py

# 导航到特定行
/git diff main.py | diffnav
# 按 g，输入行号
```

#### 2. 比较分支

```bash
# 比较两个分支
git diff main..feature

# 查看特定文件
git diff main..feature -- src/main.rs
```

#### 3. 查看历史

```bash
# 查看提交历史
git log

# 查看特定文件历史
git log --follow -- path/to/file
```

#### 4. 搜索变更

```bash
# 在 diff 中搜索
git diff | diffnav
# 按 /，输入搜索词
# 按 n/N 跳转
```

---

### 集成工具

#### 1. 与 LazyGit 集成

在 LazyGit 配置中：

```yaml
os:
  editPreset: "nvim"

customCommands:
  - key: "<c-d>"
    command: "git diff | diffnav"
    description: "用 DiffNav 查看 diff"
```

#### 2. 与 Neovim 集成

```lua
-- 使用 DiffNav 作为 git pager
vim.opt.shell = "git diff | diffnav"

-- 或使用浮动窗口
vim.api.nvim_create_user_command('DiffNav', function()
  vim.fn.termopen("git diff | diffnav", {
    on_exit = function() end
  })
end, {})
```

#### 3. 与 fzf 集成

```bash
# 快速查找文件并查看 diff
git-diff-nav() {
  local file=$(git diff --name-only | fzf)
  if [ -n "$file" ]; then
    git diff "$file" | diffnav
  fi
}
```

---

## 集成使用

### 最佳实践工作流

#### 1. 日常开发流程

```bash
# 1. 查看变更
git diff              # 使用 DiffNav 浏览

# 2. 暂存文件
lazygit              # 使用 LazyGit 暂存

# 3. 查看暂存
git diff --cached    # 使用 DiffNav 确认

# 4. 提交
lazygit              # 使用 LazyGit 提交

# 5. 推送
git push             # 或在 LazyGit 中按 p
```

#### 2. 代码审查流程

```bash
# 1. 拉取变更
git fetch origin

# 2. 查看分支 diff
git diff origin/main | diffnav

# 3. 交互式 rebase
lazygit              # 使用可视化 rebase

# 4. 推送更新
git push
```

#### 3. 紧急修复流程

```bash
# 1. 快速查看变更
git diff | diffnav

# 2. 使用 LazyGit 快速提交
lazygit
# - Space 暂存
# - c 提交
# - P 强制推送
```

---

### 工具组合

#### 场景 1：大型重构

```bash
# 1. 使用 DiffNav 浏览所有变更
git diff | diffnav

# 2. 使用 LazyGit 选择性提交
lazygit

# 3. 使用 DiffNav 确认提交
git show HEAD | diffnav
```

#### 场景 2：解决冲突

```bash
# 1. 查看冲突
git diff | diffnav

# 2. 使用 LazyGit 选择冲突策略
lazygit

# 3. 确认解决
git diff --cached | diffnav
```

#### 场景 3：清理历史

```bash
# 1. 查看历史
git log | diffnav

# 2. 使用 LazyGit 交互式 rebase
lazygit
# - 按 v 进入提交视图
# - 按 r 选择 rebase
```

---

## 常见问题

### LazyGit FAQ

#### Q1: LazyGit 无法显示中文？

**A**: 设置字体支持：

```bash
# 在终端中设置 UTF-8 编码
export LANG=zh_CN.UTF-8
export LC_ALL=zh_CN.UTF-8
```

#### Q2: 如何自定义主题？

**A**: 编辑 `~/.config/lazygit/config.yml`：

```yaml
gui:
  theme:
    activeBorderColor:
      - bold
      - "#ff00ff"
```

#### Q3: LazyGit 启动很慢？

**A**: 优化配置：

```yaml
disableStartupPopups: true
refresher:
  refreshInterval: 10  # 降低刷新频率
```

#### Q4: 如何集成到 IDE？

**A**: 使用对应插件：

- **VS Code**: LazyGit 扩展
- **Neovim**: `kdheepak/lazygit.nvim`
- **JetBrains**: GitToolBox 插件

### DiffNav FAQ

#### Q1: Delta 不工作？

**A**: 确认 Git 配置：

```bash
git config --list | grep delta

# 设置 pager
git config --global core.pager delta
```

#### Q2: DiffNav 显示乱码？

**A**: 设置终端编码：

```bash
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```

#### Q3: 如何禁用文件树？

**A**: 修改 DiffNav 配置：

```yaml
ui:
  showFileTree: false
```

#### Q4: 大文件性能问题？

**A**: 调整阈值：

```yaml
performance:
  largeFileThreshold: 5  # 降低阈值
  disableSyntaxHighlighting: true
```

---

## 性能优化

### LazyGit 优化

```yaml
# ~/.config/lazygit/config.yml
refresher:
  refreshInterval: 10      # 刷新间隔（秒）
  fetchInterval: 60        # fetch 间隔（秒）

gui:
  skipUnstageLineWarning: true  # 跳过警告

# 禁用不需要的功能
disableStartupPopups: true
```

### DiffNav 优化

```yaml
# ~/.config/diffnav/config.yml
performance:
  largeFileThreshold: 5         # 大文件阈值（MB）
  disableSyntaxHighlighting: false

  # 缓存设置
  enableCache: true
  cacheSize: 1000               # 缓存条目数
```

---

## 进阶技巧

### 1. 创建别名

```bash
# ~/.bashrc 或 ~/.zshrc
alias lg='lazygit'
alias dn='diffnav'
alias gdh='git diff HEAD | diffnav'
alias gds='git diff --staged | diffnav'
```

### 2. 脚本自动化

```bash
#!/bin/bash
# git-review.sh

# 拉取最新代码
git fetch origin main

# 使用 DiffNav 查看变更
git diff origin/main | diffnav

# 使用 LazyGit 选择性合并
lazygit
```

### 3. Git Hooks 集成

```bash
#!/bin/bash
# .git/hooks/pre-commit

# 使用 DiffNav 确认变更
read -p "使用 DiffNav 查看变更? (y/n) " -n 1 -r
echo
if [[ $REPLY =~ ^[Yy]$ ]]; then
  git diff --cached | diffnav
fi
```

---

## 资源链接

### 官方资源

- **LazyGit**: https://github.com/jesseduffield/lazygit
- **DiffNav**: https://github.com/dlvhdr/diffnav
- **Delta**: https://github.com/dandavison/delta

### 社区资源

- **LazyGit 文档**: https://github.com/jesseduffield/lazygit/blob/master/docs/Config.md
- **Delta 文档**: https://dandavison.github.io/delta/
- **Awesome Git**: https://github.com/stevemao/awesome-git

### 相关工具

- **gitui**: Rust 编写的 Git TUI
- **tig**: Git 文本模式界面
- **gitg**: GTK+ Git 查看器

---

*最后更新：2026-03-02*

**作者**: AI 助手
**版本**: 1.0.0

---

## 快速参考

### LazyGit 常用快捷键

| 快捷键 | 功能 |
|--------|------|
| `Space` | 暂存/取消暂存 |
| `c` | 提交 |
| `p` | 推送 |
| `b` | 分支 |
| `f` | 拉取 |
| `s` | 储藏 |
| `q` | 退出 |

### DiffNav 常用快捷键

| 快捷键 | 功能 |
|--------|------|
| `Ctrl-n` | 下一个变更 |
| `Ctrl-p` | 上一个变更 |
| `/` | 搜索 |
| `Enter` | 查看文件 |
| `q` | 退出 |

**Happy Coding! 🚀**
