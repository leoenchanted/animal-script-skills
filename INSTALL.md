# 安装指南

## 快速安装

### 方法 1：项目级安装（推荐）

把整个 `animal-video-script` skill 文件夹放到项目的 `.claude/skills/` 目录下：

```bash
mkdir -p your-project/.claude/skills
cp -R animal-script-skills-main your-project/.claude/skills/animal-video-script
```

推荐目录结构：

```text
your-project/
└── .claude/
    ├── skills/
    │   └── animal-video-script/
    │       ├── skill.md
    │       ├── template-default.md
    │       ├── template-guide.md
    │       └── template-storyboard.html
    └── templates/
        └── animal-video-template.md  # 可选，自定义模板
```

### 方法 2：全局安装

复制到 Claude Code 全局 skills 目录：

```bash
mkdir -p ~/.claude/skills
cp -R animal-script-skills-main ~/.claude/skills/animal-video-script
```

---

## 验证安装

在 Claude Code 中输入：

```text
我想了解雪豹，帮我做成 60 秒卡通科普视频脚本，每段都要有 AI 生图提示词
```

如果 skill 正确触发，Claude 应该会：

1. 搜索权威动物资料。
2. 输出视频设定和统一角色设定。
3. 生成逐镜头分镜表。
4. 每个镜头给出中文生图提示词和英文 Prompt。
5. 追加完整口播稿、剪辑建议和事实参考来源。

---

## 自定义模板

### 步骤 1：创建模板文件

```bash
mkdir -p your-project/.claude/templates
touch your-project/.claude/templates/animal-video-template.md
```

### 步骤 2：编辑模板

在 `animal-video-template.md` 中写入你想固定的格式。建议至少包含：

- 视频设定
- 统一角色设定
- 分镜脚本表格
- 完整口播稿
- AI 生图清单
- 事实参考来源

### 步骤 3：使用

告诉 Claude 想制作的动物视频主题，它会优先按你的模板生成。

---

## 文件清单

```text
animal-video-script/
├── skill.md                         必须，核心执行说明
├── template-default.md              推荐，默认视频脚本模板
├── template-guide.md                推荐，模板编写指南
├── template-storyboard.html         推荐，HTML 分镜工作台模板
├── README.md                        说明文件
└── INSTALL.md                       安装指南
```

---

## 常见问题

### Q: 为什么不直接给真实图片？

新版工作流是为 AI 生图视频制作设计的。它会给每个镜头生成提示词，让你在即梦、可灵、Midjourney、DALL-E、Stable Diffusion 等工具中生成统一风格画面。

### Q: 事实来源和 AI 画面是什么关系？

事实来源只用于保证解说内容准确。AI 画面是创作素材，不应被标注成真实摄影来源。

### Q: 角色每张图不一致怎么办？

优先复制“统一角色设定”，再把单个镜头提示词接在后面一起使用。必要时在生图工具里固定 seed 或使用角色参考图。

### Q: 能改成 9:16 竖屏吗？

可以。在用户请求或自定义模板中把比例从 16:9 改成 9:16，并要求所有镜头提示词继承这个比例。
