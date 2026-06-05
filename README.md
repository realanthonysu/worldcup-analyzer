# worldcup-analyzer

2026 美加墨世界杯深度分析 Claude Code Skill。为中文球迷设计，一个老球迷赛前该问的 5 件事，每次都问全。

## 功能

通过 `/worldcup-analyzer` 斜杠命令触发，支持 4 种分析模式：

| 模式 | 触发方式 | 输出 |
|------|----------|------|
| 赛前 | 有未踢比赛 | 五件套：赛事概览 / 双方首发 / 战术推演 / H2H / 典故 |
| 赛后 | 比赛已结束 | 五件套：比赛回顾 / 事件链 / 战术评估 / 亮点 / 展望 |
| 球员 | 含球员名 | 球队模式 + 球员聚焦段 |
| 历史 | 未参赛球队 | 历届记录表 + 经典比赛回顾 |

## 安装

```bash
# 克隆仓库
git clone <repo-url> worldcup-analyzer
cd worldcup-analyzer

# 部署到 Claude Code skills 目录
cp SKILL.md ~/.claude/skills/worldcup-analyzer-2026/SKILL.md
cp -r references ~/.claude/skills/worldcup-analyzer-2026/references/
```

## 使用

```
/worldcup-analyzer 法国          # 球队模式
/worldcup-analyzer 姆巴佩 法国   # 球员模式
/worldcup-analyzer 姆巴佩        # 单人，自动推断球队
```

## 项目结构

```
SKILL.md              Skill 定义（路由、规则、搜索策略、输出风格）
references/
  pre-match.md        赛前五件套模板
  post-match.md       赛后五件套模板
  player.md           球员聚焦段模板
  historical.md       历史模式模板
tests/
  scenario-*.md       测试场景（S1-S5）
  baseline/           RED 阶段基线报告
  e2e/                GREEN 阶段端到端测试
ROADMAP.md            优化路线图（v1.3.0 全部完成）
CHANGELOG.md          版本变更记录
```

## 设计原则

- **斜杠命令触发**：不会从自然语言自动激活，必须显式 `/worldcup-analyzer`
- **不编造数据**：比分/进球/伤停等必须 web search，无把握时标注"待官方确认"
- **五件套齐全**：每个模式有固定输出结构，不偷工减料
- **数据溯源**：关键事实附 Wikipedia/BBC/FIFA/Transfermarkt 链接

## 赛事时效

限定 2026 世界杯赛事期间（2026-06-11 ~ 2026-07-19）
## 许可

MIT
