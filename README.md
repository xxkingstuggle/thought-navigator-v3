<p align="center">
  <img src="assets/logo.svg" width="96" alt="思路导航图标">
</p>

<h1 align="center">思路导航 V3 · Thought Navigator</h1>

<p align="center"><strong>你只管提出问题，让 AI 决定怎么思考。</strong></p>

<p align="center">一个面向 Codex 的思考 Skill 路由插件。主动唤起后，模型会判断是否需要借助思考方法，以及该用哪一种。</p>

---

## 它能做什么

有时你知道自己遇到了问题，却不知道该从哪里想起：该反驳自己的方案、补齐信息、比较选项，还是先做一个小实验？

使用「思路导航」时，**你只需描述问题，不必先学会那些方法的名字**。模型按当前任务选择、组合或切换 Skill；简单问题可以直接回答，不必为了使用方法而使用方法。

- **按需选择**：从随插件收录的 Skill 中寻找适合当前问题的方法，也允许一个都不用。
- **围绕结果**：优先帮助你形成判断、解决问题和采取行动，而不是展示思考术语。
- **尊重边界**：不自动介入普通对话，不替代模型的判断，也不越过宿主的工具和权限限制。
- **可指定原文**：默认按问题灵活借用方法；明确提出「严格按原文执行」时，再按该 Skill 的完整流程进行。

> 插件包含 **25 个方法入口**：24 种不同方法，加 1 个兼容旧 ID 的转发入口；另有「思路导航」路由入口。完整清单见[能力目录](plugin/thought-navigator/skills/thought-navigator/references/catalog.md)。

## 怎么用

在 Codex 中主动选择 **@思路导航**，然后像平时一样说出问题。例如：

| 你可以这样问 | 可能需要的思考方向 |
| --- | --- |
| `@思路导航 我有两个工作机会，哪一个更值得选？` | 比较双方最有力的理由，找到改变决定的关键信息 |
| `@思路导航 我做了计划，却总是执行不下去。` | 澄清卡点，检查假设，寻找可执行的下一步 |
| `@思路导航 我有个产品想法，帮我看看哪里站不住脚。` | 反向审查方案，寻找风险与验证办法 |
| `@思路导航 这个软件一直报错，我不知道怎么排查。` | 故障诊断与逐步定位 |

右侧是示例性的处理方向，**不是固定路由规则或运行结果**；实际由模型根据上下文判断。你也可以直接点名「第一性原理」「乔哈里视窗」等方法。

**工作方式**

```text
你描述问题
    ↓
模型判断：普通回答是否已经足够？
    ├─ 是 → 直接回答
    └─ 否 → 查阅能力目录 → 读取合适的 Skill → 解决当前问题
```

## 安装

需要一个支持 `codex plugin` 命令的 Codex 环境。仓库提供了本地插件市场配置和插件清单。

```sh
git clone https://github.com/xxkingstuggle/thought-navigator-v3.git
cd thought-navigator-v3
codex plugin marketplace add .
codex plugin add thought-navigator@thought-navigator-v3
```

安装后，在 Codex 的 **@ 菜单**里选择「思路导航」，或在支持的调用位置显式使用：

```text
$thought-navigator:thought-navigator
```

如果只想调用某种具体方法，可以直接选择该 Skill。安装命令与本仓库的配置对应，但并不意味着所有 Codex 版本都支持插件功能；请以当前使用的 Codex 版本为准。

> **关于 ChatGPT**：本仓库说明的是 Codex 插件的安装方式。普通 ChatGPT 聊天界面能否通过 @ 调用，取决于该插件是否另行接入对应环境；仅克隆 GitHub 仓库不会自动把它安装进 ChatGPT。

## 收录的方法

| 你遇到的情况 | 部分对应方法 |
| --- | --- |
| 问题还没想清楚 | [苏格拉底式提问](plugin/thought-navigator/skills/socratic-inquiry/SKILL.md)、[乔哈里视窗](plugin/thought-navigator/skills/johari-window/SKILL.md) |
| 要做选择或审查方案 | [双向钢人](plugin/thought-navigator/skills/steelman-both-sides/SKILL.md)、[点子王](plugin/thought-navigator/skills/carl-idea-king/SKILL.md)、[逆向排雷](plugin/thought-navigator/skills/inversion/SKILL.md) |
| 原来的思路走不通 | [第一性原理](plugin/thought-navigator/skills/first-principles/SKILL.md)、[跨领域借解](plugin/thought-navigator/skills/cross-domain-borrow/SKILL.md)、[最小实验](plugin/thought-navigator/skills/minimum-experiment/SKILL.md) |
| 想理解、研究或排查问题 | [双层解释](plugin/thought-navigator/skills/two-layer-explain/SKILL.md)、[事实核查](plugin/thought-navigator/skills/fact-check/SKILL.md)、[故障诊断](plugin/thought-navigator/skills/matt-diagnosing-bugs/SKILL.md) |
| 想把结论交给 Agent 执行 | [Agent 任务书](plugin/thought-navigator/skills/kaz-leader/SKILL.md)、[项目知识收尾](plugin/thought-navigator/skills/kaz-neat-freak/SKILL.md) |

[查看完整能力目录](plugin/thought-navigator/skills/thought-navigator/references/catalog.md) · [查看插件文件](plugin/thought-navigator) · [反馈问题](https://github.com/xxkingstuggle/thought-navigator-v3/issues)

## 使用边界

- **不是全局系统提示词**：只有用户主动调用时才进入导航流程；不在所有聊天中自动启用。
- **不是强制套模板**：选不出值得使用的 Skill 时，模型直接回答即可。
- **不是独立模型或 Agent**：它提供方法和选择依据，不承诺提高每次回答的质量，也不自行获得联网、文件修改或委派权限。
- **长流程需要用户意愿**：涉及多轮盘问、教学或长期协作时，不默认要求用户进入完整流程。

## 来源、版权与许可

本项目是 [LearnPrompt/laoyeye](https://github.com/LearnPrompt/laoyeye) 的**非官方 Codex 插件改编版**，保留了原项目收录的方法与提示语材料，并对入口、目录和插件调用方式做了适配。

- [LICENSE](LICENSE)：仓库沿用的 MIT 许可文本。
- [NOTICE](plugin/thought-navigator/NOTICE)：原项目、作者归属和第三方材料说明。
- [来源记录](plugin/thought-navigator/docs/provenance.json)：改编所基于的上游提交与 Skill 对应关系。
- [第三方许可](plugin/thought-navigator/docs/licenses)：随包保留的第三方许可文本。

提示语原文及第三方 Skill 的权利归各自作者；请以对应来源和许可为准。思路导航 V3 不是上述原作者的官方发行。
