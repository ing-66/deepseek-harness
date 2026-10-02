# Office Skills 安装说明（WorkBuddy / DeepSeek Harness）

本仓库是 `deepseek-ai/deepseek-harness` 的公开 Fork。Office Skill 位于：

- `packages/skill/skill-office/assets/office-docx/`
- `packages/skill/skill-office/assets/office-xlsx/`
- `packages/skill/skill-office/assets/office-pptx/`
- 共享检查脚本：`packages/skill/skill-office/assets/scripts/`

## 安装到 WorkBuddy

WorkBuddy 的当前用户级 Skill 根目录为 `%USERPROFILE%\.workbuddy\skills`。在仓库根目录执行：

```powershell
$source = '.\packages\skill\skill-office\assets'
$target = "$HOME\.workbuddy\skills"
Copy-Item "$source\office-docx" "$target\office-docx" -Recurse -Force
Copy-Item "$source\office-xlsx" "$target\office-xlsx" -Recurse -Force
Copy-Item "$source\office-pptx" "$target\office-pptx" -Recurse -Force
Copy-Item "$source\scripts" "$target\scripts" -Recurse -Force
```

复制前如目标存在同名目录，请先备份并人工合并，不要盲目覆盖自定义内容。复制后重启 WorkBuddy，并确认三个目录中均有 `SKILL.md`。这些 Skill 依赖 Python 3.9+ 及相应 Office 编写库；渲染能力还取决于宿主是否提供 LibreOffice Kit。

## 安装到 DeepSeek Harness

DSH Desktop 已随应用注册 `office-docx`、`office-xlsx`、`office-pptx`，通常无需重复安装。源码/自定义部署应挂载包 `@deepseek-ai/dsh-skill-office`，并同时提供 Skill 注册表与 `dsh-tool-skill`；最小 Cordis 配置为：

```yaml
- name: '@deepseek-ai/dsh-skill-office'
```

完整配置与 `assetRoot`、`node`、`cli` 说明见 `packages/skill/skill-office/README.zh.md`。不要仅复制 `SKILL.md` 后就宣称获得了 DSH Desktop 内置的 LibreOffice 运行时。

## 来源

官方上游：<https://github.com/deepseek-ai/deepseek-harness>

