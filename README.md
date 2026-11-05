# 思路导航 V3

Codex 插件。主动 @「思路导航」后描述问题，模型按需选用、组合或切换思考方法，简单问题可以直接回答。插件附带 25 个方法入口及其原文。

## 安装

```sh
git clone https://github.com/xxkingstuggle/thought-navigator-v3.git
cd thought-navigator-v3
codex plugin marketplace add .
codex plugin add thought-navigator@thought-navigator-v3
```

在 Codex 的 @ 菜单选择「思路导航」，或显式调用 `$thought-navigator:thought-navigator`。想按某个方法的原文完整执行时，可以在请求里说明。

## 来源与许可

本项目基于 [LearnPrompt/laoyeye](https://github.com/LearnPrompt/laoyeye) 改编。源码在 [plugin/thought-navigator](plugin/thought-navigator)，作者和来源见 [NOTICE](plugin/thought-navigator/NOTICE) 与 [来源记录](plugin/thought-navigator/docs/provenance.json)。代码和文档的许可范围见 [LICENSE](LICENSE)，随包的第三方许可见 [docs/licenses](plugin/thought-navigator/docs/licenses)。
