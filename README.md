# precoding-skills

Claude Code 技能由[@zjinhu](https://github.com/zjinhu)出版。

## 技能

### `precoding`—— 独立头脑风暴→规格

把一个模糊的想法变成书面规格文档，然后就停了。没有自动链接实施规划，也没有意外的下一步。你拿到规格;你自己决定怎么处理它。

**安装：**

你可以使用 GitHub 简写别名或完整仓库 URL 来安装该技能：

* **使用别名安装（推荐）**：
  ```bash
  npx skills add zjinhu/precoding-skills --skill precoding
  ```
* **使用完整仓库 URL 安装**：
  ```bash
  npx skills add https://github.com/zjinhu/precoding-skills --skill precoding
  ```

这会把技能克隆并配置到本地的 `~/.claude/skills/precoding/`（针对 Claude Code）或 `~/.opencode/skills/precoding/` / `.opencode/skills/precoding/`（针对 OpenCode CLI）路径下。

**卸载：**

根据你的 AI Agent，删除对应的本地目录即可卸载：
```bash
# 卸载 Claude Code 技能
rm -rf ~/.claude/skills/precoding

# 卸载 OpenCode 技能
rm -rf ~/.opencode/skills/precoding
```

---

## 教程与 CLI 使用指南

`precoding` 技能可以通过不同的 Agent 工具及命令行界面（CLI）进行加载和使用。

### 1. 在 Claude Code 中使用（推荐）

Claude Code 拥有原生技能管理机制。

* **自动触发**：当你的提问或任务涉及系统架构设计、新功能头脑风暴或编写设计规格文档时（例如：“我想设计一个新功能”、“帮我梳理一下底层通信设计”），Claude Code 会基于技能的 `description` 描述自动识别并激活该技能。
* **显式/强制触发**：你可以直接通过 Prompt 强制命令 Claude 使用此技能，例如：
  > “请使用 `precoding` 技能帮我设计一个 iOS 记账 App 的本地数据同步功能。”
* **工作流演示**：
  1. Claude 会询问你要采用 **通用设计模板** 还是 **iOS/SwiftUI 设计模板**。
  2. 接下来 Claude 会通过**单问单答**的方式引导你逐步澄清需求，并提供 2-3 个多选方案。
  3. 如果需要做 UI 或架构图对比，Claude 会在本地启动 Visual Companion（视觉助手），并输出类似 `http://localhost:52341` 的链接。
  4. 你可以在浏览器中查看可视化 UI 框图，点击选择方案。Claude 可以在命令行无缝接收你的点击事件并继续对话。
  5. 最终生成 `docs/precoding/YYYY-MM-DD-<topic>-design.md` 后，Claude 将会**完全停止**，不会擅自开始写代码。

### 2. 在 Gemini CLI 中使用

如果你在 Gemini CLI 中加载此技能：

* **加载方式**：Gemini 会在启动时自动索引 `~/.claude/skills/precoding/SKILL.md`。
* **显式引导**：你可以通过直接告诉 Gemini 来触发：
  > “请读取我的已安装技能 `precoding` 里的 `SKILL.md`。严格按照它的头脑风暴流程，一次只问我一个问题，最终帮我生成 spec 规范文档。”
* **Visual Companion 运行**：如果你的终端环境会直接回收后台守护进程，你可让 Gemini 使用 `--foreground` 参数在前台运行：
  ```bash
  skills/precoding/scripts/start-server.sh --project-dir ./ --foreground
  ```
  并在 Gemini 命令行内协同完成可视化方案的选择。

### 3. 在 OpenCode CLI 中使用

OpenCode 是一个开源的终端 AI 编码智能体，同样原生支持 Agent 技能（Skills）规范。

* **自动识别**：OpenCode 启动时会自动扫描全局路径 `~/.opencode/skills/` 以及当前项目根目录下的 `.opencode/skills/`，并自动匹配并载入 `precoding` 技能。
* **显式唤醒**：在 OpenCode 的终端对话界面中，你可以用如下指令直接激活它：
  > “使用 `precoding` 技能，帮我为当前项目起草一份用户认证系统的设计规格书。”
  此时 OpenCode 将完全遵守规范，一次只向你提问一个澄清问题，并在设计完成后自动生成 `docs/precoding/` 下的 Spec 文档并自动结束回合，不会发生越权自动执行代码的操作。
* **配合 Visual Companion**：OpenCode 与本地浏览器事件流无缝集成。你可以在浏览器页面中直接交互，所有点击事件和选项都会自动记录在项目底下的 `.precoding/brainstorm/` 状态文件夹中，供 OpenCode 进行下一阶段的推理。

---

**它的作用：**

- 一次只问一个问题来澄清你的想法
- 提出2–3种方法，包含权衡并提出建议
- 将设计分段展示供您审阅
- 写入最终规格并提交`docs/precoding/YYYY-MM-DD-<topic>-design.md`
- **就到这里。**输出设计文档路径后回合结束

**使用时间：**

当你想在写代码前先探索一个概念、系统或功能设计，并且希望在不让助手擅自乱写代码的情况下，先沉淀出一份经过你评审的工程规范。

## 制作人员

该技能可从[obra/superpowers](https://github.com/obra/superpowers)（MIT授权）中提取并修改为：`precoding`

- 在完成专精后停止——不要自动连锁到其他技能`writing-plans`
- 移除那些在完整Superpowers插件外不存在的跨技能依赖
- 为避免与原始技能混淆，请改名为`precoding``brainstorming`

原作者：杰西·文森特（[@obra](https://github.com/obra)）。这项技能的来源于Superpowers的方法论，在[他最初的发布公告](https://blog.fsck.com/2025/10/09/superpowers/)中有所记录。

## 许可

麻省理工学院——参见[许可证](https://github.com/wishworldbetter/seedex-skills/blob/main/LICENSE)。