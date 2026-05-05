# Animal Doc - 动物科普文案生成器

一个专业的 Claude Code Skill，用于自动搜索权威文献资料并生成高质量的动物科普解说文案。

## 功能特点

- 🔍 **多维度权威搜索**：自动搜索 IUCN、National Geographic、WWF 等权威来源
- 📝 **智能模板适配**：支持自定义文案模板，或使用内置模板
- ✅ **真实数据保障**：只使用搜索到的真实资料，禁止编造
- 🌍 **中英文双语搜索**：英文搜索确保权威性，中文输出便于阅读

## 安装方法

### 方法 1：复制到项目

将此 skills 文件夹复制到你的项目 `.claude/skills/` 目录下：

```
your-project/.claude/skills/animal-doc/
├── skill.md              # Skills 定义
├── template-default.md   # 默认模板
└── README.md             # 使用说明
```

### 方法 2：全局安装

复制到 Claude Code 全局配置目录：

```
~/.claude/skills/animal-doc/
```

## 使用方法

### 基本用法

直接告诉 Claude 你想了解的动物：

```
我想了解老虎
给我介绍一下熊猫
帮我写一篇关于蓝鲸的科普文案
```

### 使用自定义模板

1. 创建模板文件 `.claude/templates/animal-template.md`
2. 粘贴你想要的文案格式示例
3. Claude 会自动读取并按模板生成

### 如果没有模板

Claude 会主动询问你提供参考格式。

## 输出示例

```markdown
【开头悬念】你敢相信吗？眼前这只老虎，居然是隐藏在大自然里的凶猛猎手！

【基础介绍】它叫老虎（Panthera tigris），主要栖息在亚洲热带雨林...

【生活习性】看似威风凛凛，实则是独行侠...

【参考来源】
1. National Geographic - Tiger
2. IUCN Red List - Panthera tigris
```

## 配置选项

可在 `.claude/templates/animal-template.md` 中设置：
- 文案风格（活泼/严谨/科普/趣味）
- 目标受众（大众/儿童/学术）
- 内容深度（简介/详细）

## 文件结构

```
animal-doc-skill/
├── skill.md              # Skills 主文件（Claude Code 读取）
├── template-default.md   # 默认模板示例
├── README.md             # 本说明文件
└── examples/
    └── output-example.md # 输出示例
```

## 作者

Claude Code Skills Community

## 版本

v1.0.0