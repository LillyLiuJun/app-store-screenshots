<p align="center">
  <img src="../assets/banner.png" alt="App Store 商店图：五层框架" width="100%">
</p>

# App Store 商店图

一个给 AI agent 用的 Skill，帮你设计 App Store 商店图。

**核心原则：** 在真实展示产品的前提下，让用户发现它对自己的价值。

[English](../README.md)

## 怎么工作

按五层推进：**文案、焦点、设备、光影、背景**。每一层先并排给出 2–3 个方案，由你选择，选定后记进一张规范表，整套图都按它来。然后出图、核对、导出。

规则尽量少：每一层只给出它要回答的问题、一小张带推荐的方案表，以及最后一份简短的自查清单。

## 安装

把下面这段话发给你的 AI agent：

```
把 https://github.com/LillyLiuJun/app-store-screenshots 这个 skill
安装到你加载 skill 的位置，装完后确认它可用。
```

想自己装也可以：这个 Skill 只有一个文件 `SKILL.md`，放进 agent 的 skills 文件夹即可。

## 怎么用

直接用日常语言说就行，比如：

- "帮我设计我的 App 的商店图。"
- "帮我改一下商店图，首图看起来像广告。"
- "这是我喜欢的一张参考图，帮我做成我们自己的。"

Skill 会先问三件事：产品是什么、给用户什么价值，品牌的气质，以及你手上已有的素材。连接 Figma 会更方便，因为方案是在 Figma 里并排做出来的，但不是必需的。

## 案例：Poplex

[Poplex](https://github.com/LillyLiuJun/Poplex) 1.0 版本的商店图，由 **Claude 通过 Figma MCP 操控 Figma** 完成。

<table>
  <tr>
    <td><img src="../assets/poplex/01_cover.jpg" width="180" alt="Poplex 商店图 1：品牌封面"></td>
    <td><img src="../assets/poplex/02_ask.jpg" width="180" alt="Poplex 商店图 2：Ask what you're curious about"></td>
    <td><img src="../assets/poplex/03_snap.jpg" width="180" alt="Poplex 商店图 3：Snap it. Type it. Say it."></td>
    <td><img src="../assets/poplex/04_words.jpg" width="180" alt="Poplex 商店图 4：Your words, sorted for you"></td>
    <td><img src="../assets/poplex/05_scenes.jpg" width="180" alt="Poplex 商店图 5：Your life, sorted into scenes"></td>
  </tr>
</table>

## 许可

MIT，`assets/` 里的图片除外。
