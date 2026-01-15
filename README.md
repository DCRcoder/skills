# Skills Collection

A collection of Agent Skills for [Claude Code](https://code.claude.com), designed to extend Claude's capabilities and provide domain-specific expertise.

[中文文档](./README_CN.md)

## 🎯 What are Skills?

Skills are Markdown files that teach Claude how to perform specific tasks. They are **model-invoked**: Claude automatically applies relevant Skills when your request matches a Skill's description, without requiring explicit invocation.

According to the [Claude Code official documentation](https://code.claude.com/docs/zh-CN/skills), Skills provide a powerful way to:
- Customize Claude's behavior to match your team standards
- Teach Claude to use specific tools and frameworks
- Automate common development workflows
- Share best practices across projects and teams

## 📦 Available Skills

### generate-openapi-docs

**OpenAPI 3.0 Documentation Generation Expert** - Analyzes backend code and generates structurally rigorous OpenAPI 3.0 YAML documentation.

**Features:**
- ✅ Generate OpenAPI 3.0 YAML from Controllers, Routes, Serializers
- ✅ Fully compatible with [Redoc](https://redocly.com/redoc/) rendering
- ✅ Automatically infer HTTP methods, parameters, and response structures
- ✅ Support component reuse and reference integrity
- ✅ Minimal changes principle (only update changed sections)
- ✅ Built-in preview and HTML export guide

**Use Cases:**
- Need to document API endpoints
- Create Swagger/Redoc-compatible specifications
- Extract API documentation from existing codebase

**Documentation:**
- [中文说明](./generate-openapi-docs/SKILL_CN.md)
- [English Documentation](./generate-openapi-docs/SKILL.md)

## 🚀 Installation and Usage

### Personal Use (Available Across All Projects)

Copy Skills to your personal Skills directory:

```bash
# Copy entire skills collection
cp -r ./generate-openapi-docs ~/.claude/skills/

# Or copy specific skill only
cp -r ./generate-openapi-docs ~/.claude/skills/generate-openapi-docs
```

### Project Use (Team Sharing)

Create `.claude/skills` directory in your project and copy Skills:

```bash
# In project root
mkdir -p .claude/skills
cp -r ./generate-openapi-docs .claude/skills/

# Commit to version control
git add .claude/skills
git commit -m "Add generate-openapi-docs skill"
```

### Verify Installation

Start Claude Code and ask:

```
What Skills are available?
```

You should see `generate-openapi-docs` appear in the list.

## 💡 Usage Examples

### Generate OpenAPI Documentation

```
Please analyze my FastAPI controllers and generate OpenAPI 3.0 documentation.
```

Or:

```
Create Swagger docs for the API endpoints in src/routes/
```

Claude will automatically recognize your request and apply the `generate-openapi-docs` Skill to generate compliant YAML documentation.

### Preview Generated Documentation

After generating documentation, use these commands to preview:

```bash
# Online preview (recommended)
npx @redocly/cli preview-docs docs/openapi.yaml

# Generate static HTML
npx @redocly/cli build-docs docs/openapi.yaml -o docs/index.html
```
### Adding a New Skill

1. Create a new Skill directory in the project root:
```bash
mkdir -p ./my-new-skill
```

2. Create `SKILL.md` file with YAML front matter and instructions

3. (Optional) Create `SKILL_CN.md` for Chinese version

4. Test the Skill:
```bash
cp -r ./my-new-skill ~/.claude/skills/
# Test in Claude Code
```

5. Submit a Pull Request

### Key Points for Writing Good Skills

Based on [official best practices](https://code.claude.com/docs/zh-CN/skills):

- ✅ **Clear description** - Include specific features and trigger keywords
- ✅ **Specific instructions** - Provide clear steps and examples
- ✅ **Use examples** - Show expected inputs and outputs
- ✅ **Handle edge cases** - Explain limitations and error handling
- ✅ **Stay focused** - One Skill does one thing well

## 📖 Related Resources

- [Claude Code Official Documentation](https://code.claude.com/docs/zh-CN/skills)
- [Agent Skills Guide](https://code.claude.com/docs/zh-CN/skills)
- [Skills Writing Best Practices](https://code.claude.com/docs/zh-CN/skills#best-practices)
- [OpenAPI 3.0 Specification](https://swagger.io/specification/)
- [Redoc Documentation](https://redocly.com/redoc/)

## 📄 License

[MIT]

## 🐛 Issues and Feedback

If you encounter issues or have suggestions for improvements:
1. Check the [Troubleshooting Guide](https://code.claude.com/docs/zh-CN/skills#troubleshooting)
2. Submit an Issue

---

