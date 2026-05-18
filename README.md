# Animal Video Script - 动物科普短视频脚本生成器

一个用于生成动物科普短视频脚本的 Claude Code Skill。它会先搜索权威资料，再输出可直接用于视频制作的分镜脚本、卡通 AI 生图提示词、完整口播稿和剪辑建议。

## 功能特点

- **权威资料检索**：优先参考 IUCN、WWF、National Geographic、Britannica 等来源。
- **短视频脚本化**：默认生成 60-90 秒脚本，拆成 10-15 个镜头。
- **逐镜头生图提示词**：每段解说都配中文提示词和英文 Prompt。
- **卡通风格统一**：先生成统一角色设定，减少 AI 生图角色不一致的问题。
- **制作友好**：包含画面内容、动效建议、配音建议、BGM 方向和事实来源。

## 安装方法

### 项目级安装

复制整个文件夹到项目的 `.claude/skills/` 目录：

```text
your-project/.claude/skills/animal-video-script/
├── skill.md
├── template-default.md
├── template-guide.md
└── examples/
```

### 可选：自定义模板

如果你想固定自己的视频脚本格式，可以创建：

```text
your-project/.claude/templates/animal-video-template.md
```

Claude 会优先读取这个模板；如果没有模板，就使用本目录的 `template-default.md`。

## 使用方法

直接告诉 Claude 想做哪种动物视频：

```text
帮我写一篇关于大熊猫的科普短视频脚本，要卡通生图提示词
我想了解帝企鹅，做成 60 秒分镜脚本
给我一个蓝鲸的视频脚本，每段都要有 AI 生图 Prompt
```

## 默认输出

```markdown
# [动物名称]科普短视频脚本

## 视频设定

## 统一角色设定

## 分镜脚本

| 镜头 | 时间 | 解说词 | 画面内容 | 中文生图提示词 | English Prompt | 动效建议 | 事实依据 |
|:---|:---|:---|:---|:---|:---|:---|:---|

## 完整口播稿

## AI 生图清单

## 剪辑与配音建议

## 事实参考来源
```

## 示例文件

- `examples/panda-video-script.md`：大熊猫短视频分镜脚本示例。
- `examples/video-script-editor.html`：可编辑分镜工作台示例。
- `examples/panda-output.md` 和 `examples/penguin-with-images.html`：旧版图文输出示例，仅作历史参考。

## 版本

v2.0.0 - 从图文科普文案升级为短视频分镜脚本与 AI 生图提示词工作流。
