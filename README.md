# 自动化周刊 · Automated Weekly Digest

> 每周日晚读取 ima 知识库当周新增卡片，生成《本周沉淀周刊》并回存知识库，附卡片点评与关键词深挖方向

![License](https://img.shields.io/badge/license-MIT-5a6b4f)
![Type](https://img.shields.io/badge/type-Agent%20Skill-4a6b7c)
![Platform](https://img.shields.io/badge/platform-WorkBuddy%20%7C%20Claude%20Code-b8935a)

## 它解决什么问题

知识库最大的问题是**只写不读**。卡片越存越多，实际调用率接近零，沉淀就变成了电子垃圾场。

这个 skill 是 [`wechat-deposit`](https://github.com/px-pangu/wechat-deposit) 的配套复盘环节：每周把当周新增的卡片强制读一遍，挑出最值得回看的三张，给出下一周的深挖方向。

## 执行流程

| 步骤 | 动作 |
|---|---|
| 1 | 确定时间范围（默认本周一 00:00 至今） |
| 2 | 拉取该区间内 ima「微信沉淀库」的全部新增卡片 |
| 3 | 生成周刊正文（四段结构） |
| 4 | 回存到知识库「周刊」分类 |
| 5 | 推送给用户一句话摘要 + 文件路径 |

## 周刊结构

```markdown
# 本周沉淀周刊（YYYY-MM-DD ~ YYYY-MM-DD）

## 一、本周沉淀总览
（卡片数量、类型分布、与上周对比）

## 二、最值得回看的 3 张卡片
（每张：为什么值得回看 / 能用在什么地方 / 一句话评价）

## 三、本周关键词与深挖方向
（高频词 + 一条具体可执行的下一步）

## 四、周刊存档
（本期文件位置与命名）
```

## 定时触发

配合自动化能力，设为每周日 21:00 执行；也可以在对话里直接说「生成本周周刊」。

## 硬性规则

- 卡片数量为 0 时，直接说「本周无新增」，**不要编内容凑数**
- 点评必须给出判断（好/一般/存疑），不做无立场的罗列
- 不重复上周已点评过的卡片，除非它被更新过

## 目录结构

```
wechat-weekly-digest/
└─ SKILL.md     角色 · 五步流程 · 周刊模板 · 硬性规则
```

## 许可

MIT © 2026 px-pangu


## 安装

把本仓库整个目录放进 Agent 的 skills 目录即可，目录名保持仓库名：

```bash
# WorkBuddy
git clone https://github.com/px-pangu/wechat-weekly-digest.git ~/.workbuddy/skills/wechat-weekly-digest

# Claude Code
git clone https://github.com/px-pangu/wechat-weekly-digest.git ~/.claude/skills/wechat-weekly-digest
```

装好后在对话里说一句相关的话就会自动触发，也可以用 `@wechat-weekly-digest` 显式点名。

