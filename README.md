<p align="center">
  <img src="assets/banner.png" alt="App Store Screenshots: a five-layer framework" width="100%">
</p>

# App Store Screenshots

A skill for AI agents that helps you design an App Store screenshot set.

**Core principle:** while showing the product honestly, let the user discover what it is worth to them.

[中文说明](docs/README_zh.md)

## How it works

The skill works through five layers: **copy, focus, device, light and shadow, background**. For each layer it proposes two or three options side by side. You pick one, and the choice goes into a spec table that governs the whole set. Then it builds the images, checks them, and exports.

It is deliberately light on rules. For each layer you get the question it answers, a small menu of options with a recommendation, and a short self-check at the end.

## Showcase: Poplex

[Poplex](https://github.com/LillyLiuJun/Poplex) is an iOS English-learning app. Its 1.0 screenshots were made with this framework.

<table>
  <tr>
    <td><img src="assets/poplex/01_cover.jpg" width="180" alt="Poplex screenshot 1: brand cover"></td>
    <td><img src="assets/poplex/02_ask.jpg" width="180" alt="Poplex screenshot 2: ask what you're curious about"></td>
    <td><img src="assets/poplex/03_snap.jpg" width="180" alt="Poplex screenshot 3: snap it, type it, say it"></td>
    <td><img src="assets/poplex/04_words.jpg" width="180" alt="Poplex screenshot 4: your words, sorted for you"></td>
    <td><img src="assets/poplex/05_scenes.jpg" width="180" alt="Poplex screenshot 5: your life, sorted into scenes"></td>
  </tr>
</table>

What was chosen, layer by layer:

| Layer | Choice in this set |
|---|---|
| Copy | A serif headline and one subline per image, each about a moment or a result: "Snap it. Type it. Say it.", "Your life, sorted into scenes." |
| Focus | No frame-breaking. The real screen carries the message. The one explicit emphasis is a light orange tint and a thin outline on the active chip in image 5. |
| Device | An edge-to-edge screen with rounded top corners that bleeds off the bottom edge, in the same position on every image. No bezel. |
| Light and shadow | One soft, wide shadow behind the screen. |
| Background | One solid warm paper color across the whole set. |
| First image | A brand cover (logo, headline, three value tags), followed by four real-screen images. |

The order follows the skill's story sequence: what it is (1), how you use it (2 and 3), what you get (4 and 5).

### How it was made

The Poplex set was made with Claude connected to Figma through the Figma MCP (its `use_figma` tool), plus a coding agent for the real screens.

1. **Options in Figma.** For each layer, Claude built two or three options side by side on the Figma canvas. New options went into new frames and never over a finalized one.
2. **One choice per layer.** The designer picked one option per layer. The choices were kept as a single spec for the whole set: positions, margins, corner radius, shadow values.
3. **Real screens from the simulator.** A coding agent prepared the demo data and captured the screens in the iOS simulator, in light mode, at default text size, with a 9:41 status bar and full signal and battery. The demo data was injected only in debug builds and never written to the live database, and nothing was added to or hidden from the interface for the shots.
4. **Placed and checked in Figma.** Each screen was scaled to the same width and placed at the same position with the same shadow. All five were checked side by side before export.

Notes on using the Figma MCP:

- Load the `figma-use` skill before calling `use_figma`.
- The plugin may not load a brand typeface. Use a close substitute while building and swap it by hand at the end.
- A script that errors rolls back as a whole. Before running one, check that the node ids it refers to still exist, because old frames get cleaned up.

The images in `assets/` are shown as a case study. They are not covered by the MIT license.

## Install

**Claude Code, for all your projects**

```bash
git clone https://github.com/LillyLiuJun/app-store-screenshots.git ~/.claude/skills/app-store-screenshots
```

**Claude Code, for one project**

```bash
git clone https://github.com/LillyLiuJun/app-store-screenshots.git .claude/skills/app-store-screenshots
```

**Other agents that read skills from `.agents/skills/`**

The layout used in the Poplex repo. Clone into `.agents/skills/app-store-screenshots`, or copy `SKILL.md` there.

**Claude.ai and the Claude desktop app**

Download this repository as a ZIP (Code → Download ZIP), then upload it under Settings → Capabilities → Skills. Menu names can differ between versions.

Only `SKILL.md` is required. The README, assets and docs are for people.

## Use it

Ask in plain language. For example:

- "Help me design the App Store screenshots for my app."
- "Revise my screenshots. The first image feels like an ad."
- "Here is a reference screenshot I like. Make it ours."

The skill starts by asking three things: what the product is and the value it gives, what the brand feels like, and what material you already have. A Figma connection is useful, because options are built side by side there, but it is not required.

## Languages

`SKILL.md` is in English. A Chinese version is in [docs/SKILL_zh.md](docs/SKILL_zh.md).

## License

MIT, except the images in `assets/`.
