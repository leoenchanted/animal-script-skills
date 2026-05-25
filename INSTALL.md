# 安装指南

## 快速安装

### 方法 1：项目级安装（推荐）

把整个 `animal-video-script` skill 文件夹放到项目的 `.claude/skills/` 目录下：

```bash
mkdir -p your-project/.claude/skills
cp -R animal-script-skills your-project/.claude/skills/animal-video-script
```

推荐目录结构：

```text
your-project/
└── .claude/
    ├── skills/
    │   └── animal-video-script/
    │       ├── SKILL.md
    │       ├── template-default.md
    │       ├── template-prehistoric.md
    │       ├── template-guide.md
    │       ├── template-storyboard.html
    │       └── examples/
    │           └── style-templates/
    │               ├── prehistoric-leviathan-survival.txt
    │               └── prehistoric-pterosaur-survival.txt
    └── templates/
        └── animal-video-template.md  # 可选，自定义模板
```

### 方法 2：全局安装

复制到 Claude Code 全局 skills 目录：

```bash
mkdir -p ~/.claude/skills
cp -R animal-script-skills ~/.claude/skills/animal-video-script
```

---

## 验证安装

### 标准科普模型

在 Claude Code 中输入：

```text
我想了解雪豹，帮我做成 60 秒卡通科普视频脚本，每段都要有 AI 生图提示词
```

如果 skill 正确触发，Claude 应该会：

1. 搜索权威动物资料。
2. 输出视频设定和统一角色设定。
3. 生成逐镜头分镜表（10-15 个镜头）。
4. 每个镜头给出中文生图提示词和英文 Prompt。
5. 追加完整口播稿、剪辑建议和事实参考来源。
6. 创建本地 HTML 分镜工作台。

### 史前穿越沉浸式解说模型

在 Claude Code 中输入：

```text
如果把利维坦鲸扔进现代太平洋，它还能成为霸主吗
```

如果 skill 正确触发，Claude 应该会：

1. 自动识别为「史前穿越」模式（无需手动指定）。
2. 双线搜索：古生物学数据 + 现代环境参照数据。
3. 输出 10 步情绪递进分镜，每个镜头包含 9 个电影级字段（景别、主体、动作、环境、光线、运镜、情绪、风格、设定）。
4. 创建本地 HTML 分镜工作台，分镜卡片含可编辑电影设定区域。

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

自定义模板会覆盖 `template-default.md` 和 `template-prehistoric.md` 两者，Claude 会按你的模板结构输出。

### 步骤 3：使用

告诉 Claude 想制作的动物视频主题，它会优先按你的模板生成。

---

## 叙事风格样本

如果想让 skill 参考某种短视频脚本的语气、开头、节奏和故事推进方式，把 `.txt` 样本放到：

```text
animal-video-script/examples/style-templates/
```

这些样本只用于风格参考，不作为事实来源。生成新动物脚本时，仍然需要重新搜索并核验动物事实。

本 skill 内置了两个史前穿越风格样本（利维坦鲸和风神翼龙），当你请求史前穿越模型时，Claude 会自动读取它们来学习叙事节奏和情绪推进方式。

---

## 文件清单

```text
animal-video-script/
├── SKILL.md                          必须，核心执行说明（含两种叙事模型分支逻辑）
├── template-default.md               推荐，标准科普模板
├── template-prehistoric.md           推荐，史前穿越沉浸式解说模板（10 步情绪递进）
├── template-guide.md                 推荐，模板编写指南（含 9 电影字段说明）
├── template-storyboard.html          推荐，HTML 分镜工作台模板（含电影字段渲染）
├── README.md                         说明文件
├── INSTALL.md                        安装指南
└── examples/
    └── style-templates/
        ├── prehistoric-leviathan-survival.txt    利维坦鲸叙事风格样本
        └── prehistoric-pterosaur-survival.txt    风神翼龙叙事风格样本
```

---

## 常见问题

### Q: 两种模型怎么切换？需要手动告诉 Claude 吗？

不需要。Claude 会自动根据你的提问判断：
- 如果你问"介绍雪豹"、"写蓝鲸科普"等 → 标准科普模型
- 如果你问"XX能活在现代吗"、"穿越到现代会怎样"等 → 史前穿越模型

你也可以手动指定：在提问中说明"用标准科普风格"或"用史前穿越风格"。

### Q: 史前穿越模型的 9 个电影字段在 HTML 里能编辑吗？

可以。生成的 HTML 分镜工作台中，每个分镜卡片都包含「电影分镜设定」区域，所有 9 个字段（景别、主体、动作、环境、光线、运镜、情绪、风格、设定）都是可编辑的 textarea，也可以一键复制。

如果使用的是标准科普模型生成的不含电影字段，HTML 会自动隐藏该区域。

### Q: 为什么不直接给真实图片？

新版工作流是为 AI 生图视频制作设计的。它会给每个镜头生成提示词，让你在即梦、可灵、Midjourney、DALL-E、Stable Diffusion 等工具中生成统一风格画面。

### Q: 事实来源和 AI 画面是什么关系？

事实来源只用于保证解说内容准确。AI 画面是创作素材，不应被标注成真实摄影来源。

### Q: 角色每张图不一致怎么办？

优先复制"统一角色设定"，再把单个镜头提示词接在后面一起使用。必要时在生图工具里固定 seed 或使用角色参考图。

### Q: 能改成 9:16 竖屏吗？

可以。在用户请求或自定义模板中把比例从 16:9 改成 9:16，并要求所有镜头提示词继承这个比例。
