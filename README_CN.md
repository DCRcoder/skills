# Skills Collection

一个用于 [Claude Code](https://code.claude.com) 的 Agent Skills 集合，旨在扩展 Claude 的功能，提供特定领域的专业能力。

## 🎯 什么是 Skills？

Skills 是教 Claude 如何执行特定任务的 Markdown 文件。它们是**模型调用的**：当你的请求与 Skill 的描述匹配时，Claude 会自动应用相关的 Skills，无需显式调用。

根据 [Claude Code 官方文档](https://code.claude.com/docs/zh-CN/skills)，Skills 提供了一种强大的方式来：
- 定制 Claude 的行为以匹配你的团队标准
- 教 Claude 使用特定的工具和框架
- 自动化常见的开发工作流程
- 在项目和团队之间共享最佳实践

## 📦 可用的 Skills

### generate-openapi-docs

**OpenAPI 3.0 文档生成专家** - 分析后端代码并生成结构严谨、符合 OpenAPI 3.0 规范的 YAML 文档。

**特性：**
- ✅ 从 Controllers、Routes、Serializers 生成 OpenAPI 3.0 YAML
- ✅ 完全兼容 [Redoc](https://redocly.com/redoc/) 渲染
- ✅ 自动推断 HTTP 方法、参数和响应结构
- ✅ 支持组件重用和引用完整性
- ✅ 最小化变更原则（仅更新变化部分）
- ✅ 内置预览和 HTML 导出指南

**使用场景：**
- 需要为 API 端点生成文档
- 创建 Swagger/Redoc 兼容的规范
- 从现有代码库提取 API 文档

**文档：**
- [中文说明](./generate-openapi-docs/SKILL_CN.md)
- [English Documentation](./generate-openapi-docs/SKILL.md)

## 🚀 安装和使用

### 个人使用（所有项目可用）

将 Skills 复制到你的个人 Skills 目录：

```bash
# 复制整个 skills 集合
cp -r ./generate-openapi-docs ~/.claude/skills/

# 或者只复制特定的 skill
cp -r ./generate-openapi-docs ~/.claude/skills/generate-openapi-docs
```

### 项目使用（团队共享）

在你的项目中创建 `.claude/skills` 目录并复制 Skills：

```bash
# 在项目根目录
mkdir -p .claude/skills
cp -r ./generate-openapi-docs .claude/skills/

# 提交到版本控制
git add .claude/skills
git commit -m "Add generate-openapi-docs skill"
```

### 验证安装

启动 Claude Code 并询问：

```
What Skills are available?
```

你应该会看到 `generate-openapi-docs` 出现在列表中。

## 💡 使用示例

### 生成 OpenAPI 文档

```
Please analyze my FastAPI controllers and generate OpenAPI 3.0 documentation.
```

或者：

```
Create Swagger docs for the API endpoints in src/routes/
```

Claude 会自动识别你的请求并应用 `generate-openapi-docs` Skill，生成符合规范的 YAML 文档。

### 预览生成的文档

生成文档后，使用以下命令预览：

```bash
# 在线预览（推荐）
npx @redocly/cli preview-docs docs/openapi.yaml

# 生成静态 HTML
npx @redocly/cli build-docs docs/openapi.yaml -o docs/index.html
```
### 添加新 Skill

1. 在项目根目录创建新的 Skill 目录：
```bash
mkdir -p ./my-new-skill
```

2. 创建 `SKILL.md` 文件，包含 YAML 前置元数据和说明

3. （可选）创建 `SKILL_CN.md` 中文版本

4. 测试 Skill：
```bash
cp -r ./my-new-skill ~/.claude/skills/
# 在 Claude Code 中测试
```

5. 提交 Pull Request

### 编写优秀 Skill 的要点

根据 [官方最佳实践](https://code.claude.com/docs/zh-CN/skills)：

- ✅ **清晰的描述** - 包含具体功能和触发关键词
- ✅ **具体的说明** - 提供明确的步骤和示例
- ✅ **使用示例** - 展示预期的输入和输出
- ✅ **处理边缘情况** - 说明限制和错误处理
- ✅ **保持专注** - 一个 Skill 做好一件事

## 📖 相关资源

- [Claude Code 官方文档](https://code.claude.com/docs/zh-CN/skills)
- [Agent Skills 指南](https://code.claude.com/docs/zh-CN/skills)
- [Skills 编写最佳实践](https://code.claude.com/docs/zh-CN/skills#best-practices)
- [OpenAPI 3.0 规范](https://swagger.io/specification/)
- [Redoc 文档](https://redocly.com/redoc/)

## 📄 许可证

[MIT]

## 🐛 问题和反馈

如果你遇到问题或有改进建议，请：
1. 查看 [故障排除指南](https://code.claude.com/docs/zh-CN/skills#troubleshooting)
2. 提交 Issue

---

