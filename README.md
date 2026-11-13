# 提示词五要素框架 · Prompt Five Elements

把一句随口的请求，改造成一份可执行的需求说明书。

> 角色定视角，背景定上下文，任务定动作，要求定边界，示例定标准；想不清楚的时候，让 AI 先问你。

## 目录结构

| 路径 | 内容 |
| --- | --- |
| `提示词万能框架-五要素模板.md` | 原始文档：框架速览、五要素拆解、模板、改前改后、反问协议、自检清单 |
| `skill/SKILL.md` | 可安装的技能：复杂度分级（L0–L3）、执行流程、写作规则、8 项补充协议、可复制模板 |
| `skill/references/scenario-templates.md` | 10 类场景可直接套用的模板（文案 / 报告 / 方案 / 代码 / 数据 / 评审 / 翻译 / 讲解 / 决策 / 抽取） |
| `skill/references/anti-patterns.md` | 高频反模式对照表 + 4 组改前改后 |
| `skill/references/original-framework.md` | 原始文档在技能内的存档副本 |
| `skill/scripts/check_prompt.py` | 提示词体检脚本（纯标准库，无第三方依赖） |

## 装成技能

```bash
# macOS / Linux / Git Bash
cp -r skill ~/.workbuddy/skills/prompt-five-elements
```

```powershell
# Windows PowerShell
Copy-Item -Recurse skill "$env:USERPROFILE\.workbuddy\skills\prompt-five-elements"
```

装好后新开一个对话生效：可自动触发（你只说「帮我写个文案」，它按五要素补齐），也可手动点名调用。

也可以直接把 `skill/SKILL.md` 的内容贴给任何支持自定义指令的 AI 工具使用。

## 体检脚本

```bash
python skill/scripts/check_prompt.py prompt.md     # 检查文件
python skill/scripts/check_prompt.py - < prompt.md # 从 stdin 读
python skill/scripts/check_prompt.py prompt.md --json
```

输出：五要素齐备度、缺失项补齐建议、模糊表述（「专业点」「高大上」）、缺长度/受众/负面约束、多动作未拆条、长材料未做指令隔离。启发式提示，不替代判断。

## 比原文档多做了什么

| 补充 | 解决什么 |
| --- | --- |
| L0–L3 复杂度分级 | 问常识也套五要素是另一种失败 |
| 5 步执行流程（含缺口判定阈值） | 什么该直接做、什么该先反问，不再靠感觉 |
| 输出契约 / 不确定性协议 / 多版本自评 / 数据指令隔离 / 迭代协议 | 原文档未覆盖的工程性问题 |
| 场景模板库 + 反模式表 | 从「知道原则」到「能直接套」 |
| 体检脚本 | 把自检清单变成可执行的检查 |

---

## English

A five-element framework (Role · Background · Task · Requirements · Example) for turning vague requests into executable prompt specs.

`提示词万能框架-五要素模板.md` is the original write-up. `skill/` is an installable skill package that adds a task-complexity tier table (L0–L3), an explicit clarification policy, per-element authoring rules, ten scenario templates, an anti-pattern catalogue, and a dependency-free checker:

```bash
python skill/scripts/check_prompt.py prompt.md
```

Install by copying `skill/` into `~/.workbuddy/skills/prompt-five-elements`, or paste `skill/SKILL.md` into any AI tool that supports custom instructions.
