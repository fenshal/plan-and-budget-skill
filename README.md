# plan-and-budget-skill

> Make your AI agent **quote the price before it starts spending**.
>
> 让你的 AI 助手在动手之前先说清楚：这活有多复杂、要花多久、要烧多少 token。

一个纯文本 skill（`SKILL.md`），不依赖任何框架。DSH、WorkBuddy、Claude Code、Codex 都能直接用。

---

## 为什么需要它

Agent 最常见的事故不是写错代码，而是**默默干了二十分钟**：

- 接到一句话就开始下载 1.8G 的模型
- 没说复杂度就铺开五个文件的重构
- 干到一半发现方向不对，前面全废

这个 skill 只做一件事：**强制先报账，再动手**。中高复杂度必须先拿到你的“可以”。

## 它会输出什么

```
复杂度：中
代价：装两个命令行工具（约 2 分钟），然后登录、建仓库、推送，总共 5–8 分钟
计划：
  1. winget 安装 gh（用户级，不动系统）
  2. 设备码登录
  3. 建 public 仓库并上传 SKILL.md / README / LICENSE
预计 token：2–3 万（探查 0.5 万 / 写文档 1 万 / 调试 1 万），约 ¥0.03
```

然后停下来等你点头。

## 什么时候它**不会**触发

小活直接干完再汇报，不走这套流程：

- 一次查询、一句话回答
- 单文件小改
- 你已经说清楚怎么做的
- 判据：**≤ 3 步、不下载安装、不碰 3 个以上文件**

## 安装

每个平台的技能目录不一样，但文件格式是一样的（一个目录 + 一个 `SKILL.md`）。

| 平台 | 放这里 |
|---|---|
| **DSH** | `~/.dsh/skills/plan-and-budget/SKILL.md` |
| **WorkBuddy** | `~/.workbuddy/skills/plan-and-budget/SKILL.md` |
| **Claude Code** | `~/.claude/skills/plan-and-budget/SKILL.md` |
| **Codex** | 放进它的 skills 目录（同格式） |

> Windows 上 `~` 就是 `C:\Users\<你的用户名>`。

```powershell
# 以 DSH 为例
git clone https://github.com/fenshal/plan-and-budget-skill
Copy-Item .\plan-and-budget-skill\SKILL.md "$env:USERPROFILE\.dsh\skills\plan-and-budget\SKILL.md" -Force
```

装完**重启一次对应软件**，技能列表里就会出现 `plan-and-budget`。

## 自定义

想改价格表、改分档阈值、加自己的项目约定，直接编辑 `SKILL.md`。
建议把“预算怎么估”那几条换成你实际模型的价格，估算会准很多。

## 许可

MIT。随便用、随便改、不用署名。
