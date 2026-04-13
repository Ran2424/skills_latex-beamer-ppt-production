# latex-beamer-ppt-production

这是一份 Agent Skill，用于在 Tongji Beamer 工程中高效完成 LaTeX 幻灯片生产。

## 作用

- 新建或改写学术汇报幻灯片（论文汇报、项目进展、开题与结题）
- 按现有模板组织页面结构，减少样式和排版错误
- 支持编译检查与导出，保证可交付

## 安装

1. 将本仓库克隆到本机：
   `git clone https://github.com/Ran2424/latex-beamer-ppt-production.git`
2. 把目录放到你的 Codex skills 路径下（示例）：
   `~/.agents/skills/latex-beamer-ppt-production`
3. 确保该目录包含 `SKILL.md`，并能被你的 Agent/工具链扫描到。

## 使用方式

1. 在任务中明确提到技能名：`latex-beamer-ppt-production`
2. 提供输入信息：主题、受众、时长、已有材料
3. 按技能约定先确认页级大纲，再进入具体页面制作与编译验证

## 目录说明

- `SKILL.md`：技能主说明与执行规范
- `assets/`：模板与示例资源
- `references/`：辅助参考内容
- `agents/`：相关 Agent 配置
