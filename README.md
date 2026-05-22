# precoding-skills

Claude Code 技能由[@zjinhu](https://github.com/zjinhu)出版。

## 技能



### `precoding`—— 独立头脑风暴→规格



把一个模糊的想法变成书面规格文档，然后就停了。没有自动链接实施规划，也没有意外的下一步。你拿到规格;你自己决定怎么处理它。

**安装：**

```
npx skills add zjinhu/precoding-skills --skill precoding
```



这会把技能降为 。卸载方法：`~/.claude/skills/precoding/`

```
rm -rf ~/.claude/skills/precoding
```



**它的作用：**

- 一次只问一个问题来澄清你的想法
- 提出2–3种方法，包含权衡并提出建议
- 将设计分段展示供您审阅
- 写入最终规格并提交`docs/precoding/YYYY-MM-DD-<topic>-design.md`
- **就到这里。**把自定义路径还给他，回合结束

**使用时间：**

当你想在写代码前先探索一个想法，并且希望能在不让助手立刻去实现的情况下，先拿出一份书面规范。

## 制作人员



该技能可从[obra/superpowers](https://github.com/obra/superpowers)（MIT授权）中提取并修改为：`precoding`

- 在完成专精后停止——不要自动连锁到其他技能`writing-plans`
- 移除那些在完整Superpowers插件外不存在的跨技能依赖
- 为避免与原始技能混淆，请改名为`precoding``brainstorming`

原作者：杰西·文森特（[@obra](https://github.com/obra)）。这项技能的来源于Superpowers的方法论，在[他最初的发布公告](https://blog.fsck.com/2025/10/09/superpowers/)中有所记录。

## 许可



麻省理工学院——参见[许可证](https://github.com/wishworldbetter/seedex-skills/blob/main/LICENSE)。