# Claude Code 源码相关项目整理

> **关于本项目**：Claude Code Hub 是一个存档备份项目，纯粹用于研究和学习 Claude Code 的架构设计、技术实现。任何代码仅供内部研究，请勿用于商业或违法用途。

> **免责声明**：以下项目均来源于第三方 GitHub 仓库，Claude Code Hub 不对这些项目的内容负责。这些项目仅供学习和研究使用，请勿用于任何商业或违法用途。使用前请自行判断内容合规性。

---

## 项目列表

### 1. ChinaSiro / claude-code-sourcemap

- **GitHub 链接**：https://github.com/ChinaSiro/claude-code-sourcemap
- **描述**：通过 npm 发布包内附带的 source map 还原的 TypeScript 源码
- **主要内容**：
  - 基于 `@anthropic-ai/claude-code` npm 包的 source map 还原
  - 还原版本：`2.1.88`
  - 还原文件数：4756 个（含 1884 个 `.ts`/`.tsx` 源文件）
  - 目录结构包含：main.tsx 入口、tools/ 工具实现（30+ 个）、commands/ 命令（40+ 个）、services/ API 服务、utils/ 工具函数、coordinator/ 多 Agent 协调、skills/ 技能系统、voice/ 语音交互等
  - **可运行文件**：项目中存在可直接运行的 `cli.js` 文件（构建后的产物）
- **运行方法**：
  ```bash
  git clone https://github.com/ChinaSiro/claude-code-sourcemap.git
  cd claude-code-sourcemap
  node cli.js
  ```
- **声明**：源码版权归 Anthropic 所有，仅用于技术研究与学习

---

### 2. instructkr / claw-code

- **GitHub 链接**：https://github.com/instructkr/claw-code
- **描述**：Better Harness Tools，不仅仅是存储泄露的 Claude Code 源码
- **主要内容**：
  - 2026 年 3 月 31 日凌晨源码泄露后，作者用 Python 从头重写了 Claude Code 的核心功能
  - 使用 oh-my-codex (OmX) 工作流驱动进行并行代码审查和持续执行循环
  - 纯 Python 重写，提取架构模式而非直接复制专有源码
  - 当前 `src/` 目录包含 Python 移植工作区：`commands.py`、`tools.py`、`models.py`、`query_engine.py`、`task.py` 等
  - 正在开发 Rust 版本（位于 `dev/rust` 分支）
- **运行方法**：
  ```bash
  git clone https://github.com/instructkr/claw-code.git
  cd claw-code
  # Python 模式
  python3 -m src.main summary
  # 运行测试
  python3 -m unittest discover -s tests -v
  ```
- **状态**：Python 工作区已完成基础功能，Rust 移植进行中

---

### 3. sanbuphy / claude-code-source-code

- **GitHub 链接**：https://github.com/sanbuphy/claude-code-source-code
- **描述**：Claude Code v2.1.88 源码分析
- **主要内容**：
  - 从 npm 包 `@anthropic-ai/claude-code` v2.1.88 提取的 TypeScript 源码
  - 包含深度分析报告（英文/中文双语）：
    - 遥测与隐私分析（01）
    - 隐藏功能与模型代号（Capybara/Tengu/Numbat 等）（02）
    - 卧底模式分析（Undercover Mode）（03）
    - 远程控制与紧急开关（04）
    - 未来路线图（Numbat、KAIROS、语音模式）（05）
  - 标注了 108 个未包含在 npm 包中的模块（Anthropic 内部模块）
  - 工具系统架构分析（40+ 工具、权限流程、子代理）
  - 12 种渐进式 Harness 机制分析
- **注意**：源码版权归 Anthropic 所有，仅供技术研究、学习和教育交流

---

## 项目对比

| 项目 | 语言/技术 | 还原版本 | 特点 |
|------|----------|----------|------|
| ChinaSiro/claude-code-sourcemap | TypeScript（源码还原） | 2.1.88 | 完整还原 source map |
| instructkr/claw-code | Python/Rust（重写） | - | Clean-room 架构重写 |
| sanbuphy/claude-code-source-code | TypeScript（源码+分析） | 2.1.88 | 深度分析报告 |

---

## 使用说明

以上项目均基于 2026 年 3 月 31 日泄露的 Claude Code 源码进行研究学习。这些分析项目对于理解 AI Agent 的工具调用架构、Harness 设计模式有重要参考价值。

## 参考来源

- [ChinaSiro/claude-code-sourcemap](https://github.com/ChinaSiro/claude-code-sourcemap)
- [instructkr/claw-code](https://github.com/instructkr/claw-code)
- [sanbuphy/claude-code-source-code](https://github.com/sanbuphy/claude-code-source-code)

---

*最后更新：2026-03-31*
