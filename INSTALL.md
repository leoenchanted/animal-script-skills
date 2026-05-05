# 安装指南

## 快速安装

### 方法 1：项目级安装（推荐）

将 `animal-doc-skill` 文件夹内容复制到你的项目：

```bash
# 复制 skill.md 到项目的 skills 目录
mkdir -p your-project/.claude/skills
cp animal-doc-skill/skill.md your-project/.claude/skills/animal-doc.md

# 复制默认模板（可选）
mkdir -p your-project/.claude/templates
cp animal-doc-skill/template-default.md your-project/.claude/templates/animal-template.md
```

目录结构：
```
your-project/
└── .claude/
    ├── skills/
    │   └── animal-doc.md    # Skills 定义文件
    └── templates/
        └── animal-template.md  # 文案模板（可选）
```

### 方法 2：全局安装

复制到 Claude Code 全局配置目录：

```bash
# Windows
mkdir -p %USERPROFILE%\.claude\skills
cp animal-doc-skill/skill.md %USERPROFILE%\.claude\skills\animal-doc.md

# macOS/Linux
mkdir -p ~/.claude/skills
cp animal-doc-skill/skill.md ~/.claude/skills/animal-doc.md
```

---

## 验证安装

在 Claude Code 中输入：

```
我想了解老虎
```

如果 skills 正确安装，Claude 应会：
1. 检查模板文件
2. 开始多维度搜索
3. 按模板生成文案

---

## 自定义模板

### 步骤 1：创建模板文件

```bash
mkdir -p your-project/.claude/templates
touch your-project/.claude/templates/animal-template.md
```

### 步骤 2：编辑模板

打开 `animal-template.md`，粘贴你想要的文案格式。

### 步骤 3：使用

告诉 Claude 你想了解的动物，它会自动读取模板并生成文案。

---

## 文件清单

```
animal-doc-skill/
├── skill.md              ✅ 必须复制（核心文件）
├── template-default.md   ⭕ 可选复制（默认模板）
├── README.md             ⭕ 说明文件（不需复制）
├── INSTALL.md            ⭕ 安装指南（不需复制）
└── examples/
    └── panda-output.md   ⭕ 示例参考（不需复制）
```

---

## 常见问题

### Q: Claude 没有触发 skills？

确保：
- `skill.md` 文件名正确（不是 `animal-doc-skill.md`）
- 文件位于 `.claude/skills/` 目录下
- 用户输入包含触发关键词（"想了解"、"介绍一下"等）

### Q: Claude 说找不到模板？

正常行为。如果模板文件为空，Claude 会询问你提供模板。

### Q: 如何修改搜索维度？

编辑 `skill.md` 中的"搜索维度表"，添加或删除维度。

### Q: 输出的文案不符合预期？

检查模板文件格式，或直接告诉 Claude 你想要的风格调整。