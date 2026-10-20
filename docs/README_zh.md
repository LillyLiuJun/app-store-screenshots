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

## 案例：Poplex

[Poplex](https://github.com/LillyLiuJun/Poplex) 是一款 iOS 英语学习 App，它 1.0 版本的商店图就是用这套框架做的。

<table>
  <tr>
    <td><img src="../assets/poplex/01_cover.jpg" width="180" alt="Poplex 商店图 1：品牌封面"></td>
    <td><img src="../assets/poplex/02_ask.jpg" width="180" alt="Poplex 商店图 2：Ask what you're curious about"></td>
    <td><img src="../assets/poplex/03_snap.jpg" width="180" alt="Poplex 商店图 3：Snap it. Type it. Say it."></td>
    <td><img src="../assets/poplex/04_words.jpg" width="180" alt="Poplex 商店图 4：Your words, sorted for you"></td>
    <td><img src="../assets/poplex/05_scenes.jpg" width="180" alt="Poplex 商店图 5：Your life, sorted into scenes"></td>
  </tr>
</table>

逐层的选择：

| 层 | 这套图的选择 |
|---|---|
| 文案 | 每张一个衬线主标加一句副标，讲的都是一个时刻或一个结果："Snap it. Type it. Say it."、"Your life, sorted into scenes." |
| 焦点 | 不破框，由真实界面本身传达信息。唯一明确的强调是第 5 张里当前标签上的浅橙底加细描边。 |
| 设备 | 无边框屏幕，上方圆角，底部出血，每张的位置一致，没有机身。 |
| 光影 | 屏幕后面一层柔和的大范围阴影。 |
| 背景 | 整套同一个暖纸色纯色。 |
| 首图 | 品牌封面（logo、大标题、三个价值标签），后面是四张真实界面。 |

整套顺序按 Skill 里的叙事顺序：是什么（第 1 张）、怎么用（第 2、3 张）、得到什么（第 4、5 张）。

### 制作过程

Poplex 这套图是用 Claude 通过 Figma MCP（它的 `use_figma` 工具）连接 Figma 来做的，真实界面截图则由一个编码 agent 负责。

1. **在 Figma 里做方案。** 每一层，Claude 在 Figma 画布上并排做出两三个方案。新方案放进新的 frame，不覆盖已经定稿的。
2. **每层选一个。** 设计者每层选定一个方案，选择被记成整套图的唯一规范：位置、边距、圆角、阴影参数。
3. **真实界面来自模拟器。** 编码 agent 准备演示数据，并在 iOS 模拟器里截图：浅色模式、默认字号、状态栏 9:41 且信号和电量满格。演示数据只在调试版本里注入，不写进线上数据库，也没有为了截图添加或隐藏界面元素。
4. **在 Figma 里摆放和核对。** 每张截图缩放到同一宽度、放在同一位置、用同一个阴影，导出前把五张并排检查。

使用 Figma MCP 的几点经验：

- 调用 `use_figma` 之前先加载 `figma-use` skill。
- 插件里可能加载不到品牌字体。制作时先用相近字体代替，最后再手动替换。
- 脚本一旦报错会整段回滚。运行前先确认脚本引用的节点 id 还在，因为旧 frame 常被清理掉。

`assets/` 里的图片只作为案例展示，不适用 MIT 协议。

## 安装

**Claude Code，对所有项目生效**

```bash
git clone https://github.com/LillyLiuJun/app-store-screenshots.git ~/.claude/skills/app-store-screenshots
```

**Claude Code，只对某个项目生效**

```bash
git clone https://github.com/LillyLiuJun/app-store-screenshots.git .claude/skills/app-store-screenshots
```

**读取 `.agents/skills/` 的其他 agent**

Poplex 仓库用的就是这个目录。克隆到 `.agents/skills/app-store-screenshots`，或者只复制 `SKILL.md` 过去。

**Claude.ai 和 Claude 桌面端**

把本仓库下载成 ZIP（Code → Download ZIP），在 Settings → Capabilities → Skills 里上传。不同版本的菜单名称可能不同。

只有 `SKILL.md` 是必需的，README、assets 和 docs 是给人看的。

## 怎么用

直接用日常语言说就行，比如：

- "帮我设计我的 App 的商店图。"
- "帮我改一下商店图，首图看起来像广告。"
- "这是我喜欢的一张参考图，帮我做成我们自己的。"

Skill 会先问三件事：产品是什么、给用户什么价值，品牌的气质，以及你手上已有的素材。连接 Figma 会更方便，因为方案是在 Figma 里并排做出来的，但不是必需的。

## 语言

`SKILL.md` 是英文版，中文版在 [SKILL_zh.md](SKILL_zh.md)。

## 许可

MIT，`assets/` 里的图片除外。
