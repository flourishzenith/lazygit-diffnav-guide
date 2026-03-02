# 📖 LazyGit & DiffNav 使用指南

> 高效的终端 Git 工具完全指南

---

## ✨ 特性

- 🦥 **LazyGit**：美观的终端 Git UI 工具（73k+ Stars）
- 🐳 **DiffNav**：带文件树的 Git diff 分页器（865 Stars）
- 📚 **100+ 快捷键**：完整的快捷键参考
- 🎯 **实战场景**：真实工作流程示例
- ⚡ **性能优化**：针对大型仓库的优化建议
- 🔧 **集成指南**：与 Neovim、tmux、fzf 等工具集成

---

## 🚀 快速开始

### 安装 LazyGit

```bash
# macOS
brew install lazygit

# Linux (Debian/Ubuntu)
sudo apt install lazygit

# 从源码安装
go install github.com/jesseduffield/lazygit@latest
```

### 安装 DiffNav

```bash
# 安装 Delta（前置要求）
brew install git-delta

# 安装 DiffNav
go install github.com/dlvhdr/diffnav@latest
```

### 配置 Git

在 `~/.gitconfig` 中添加：

```ini
[core]
    pager = delta

[delta]
    navigate = true
    line-numbers = true
    syntax-theme = Monokai Extended
```

---

## 📖 文档内容

### 基础指南
- ✅ 工具介绍和对比
- ✅ 安装方法（macOS/Linux/Windows）
- ✅ 快速开始教程
- ✅ 界面布局说明

### LazyGit 指南
- ✅ 核心功能（文件/提交/分支/远程操作）
- ✅ 高级功能（交互式 Rebase、自定义配置）
- ✅ 实用技巧和快捷键
- ✅ 集成工具（Neovim/tmux/fzf）

### DiffNav 指南
- ✅ 核心功能（文件树导航、Diff 导航）
- ✅ 高级功能（自定义主题、Delta 优化）
- ✅ 实用技巧和快捷键
- ✅ 性能优化建议

### 集成使用
- ✅ 最佳实践工作流
- ✅ 工具组合场景
- ✅ 性能优化
- ✅ 进阶技巧

### 常见问题
- ✅ LazyGit FAQ（4 个问题）
- ✅ DiffNav FAQ（4 个问题）

---

## ⚡ 快速参考

### LazyGit 常用快捷键

| 快捷键 | 功能 |
|--------|------|
| `Space` | 暂存/取消暂存 |
| `c` | 提交 |
| `p` | 推送 |
| `b` | 分支管理 |
| `q` | 退出 |

### DiffNav 常用快捷键

| 快捷键 | 功能 |
|--------|------|
| `Ctrl-n` | 下一个变更 |
| `Ctrl-p` | 上一个变更 |
| `/` | 搜索 |
| `q` | 退出 |

---

## 📚 完整文档

查看 **[README.md](README.md)** 获取完整的使用指南（13,600 字）

---

## 🛠️ 相关工具

- **[lazygit](https://github.com/jesseduffield/lazygit)** - 终端 Git UI 工具
- **[diffnav](https://github.com/dlvhdr/diffnav)** - Git diff 分页器
- **[delta](https://github.com/dandavison/delta)** - Diff 高亮工具
- **[gitui](https://github.com/extrawurst/gitui)** - Rust 编写的 Git TUI

---

## 📊 项目统计

- **文档字数**：13,600 字
- **快捷键数量**：100+ 个
- **代码示例**：50+ 个
- **配置示例**：20+ 个

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

---

## 📄 许可证

MIT License - 详见 [LICENSE](LICENSE)

---

## 🔗 资源链接

- [LazyGit 官方文档](https://github.com/jesseduffield/lazygit/blob/master/docs/Config.md)
- [Delta 官方文档](https://dandavison.github.io/delta/)
- [Awesome Git](https://github.com/stevemao/awesome-git)

---

**Happy Coding! 🚀**
