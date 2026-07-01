---
name: skills-top-stars-maintainer
description: 维护 GitHub 高星 Skills 精选列表仓库。当用户提到「更新 skills-top-stars」、「维护 wind8ai 的 Skills 列表」、「检查 skills 仓库星数变化」、「整理 skills-top-stars」时触发。执行抓取、排序、作者简介、描述更新、收录规则检查、提交推送等完整维护流程。
---

# skills-top-stars-maintainer

维护 [wind8ai/skills-top-stars](https://github.com/wind8ai/skills-top-stars) 列表仓库的标准流程。

## Monorepo 布局

本 skill 由 [top-stars-ops](https://github.com/wind8ai/top-stars-ops) monorepo 编排：

| 路径 | 远程 |
|------|------|
| `lists/skills-top-stars/` | `git@github.com:wind8ai/skills-top-stars.git` |
| `maintainers/skills-top-stars-maintainer/` | `git@github.com:wind8ai/skills-top-stars-maintainer.git` |

```bash
git clone --recurse-submodules git@github.com:wind8ai/top-stars-ops.git
cd top-stars-ops/lists/skills-top-stars
```

## 仓库信息

- **收录上限**：42 个（按星数倒序）
- **排序规则**：按 GitHub Star 总数倒序
- **星数展示**：量级格式（137k、135k...）
- **授权协议**：CC BY-SA 4.0
- **维护者**：wind8

---

## 收录规则摘要

### 来源

- 仅收录 wind8ai GitHub Stars 中 `Skills` 列表的仓库
- 地址：https://github.com/stars/wind8ai/lists/skills
- **注意**：列表有分页，必须翻完所有页

### 收录条件

1. 以 wind8ai 的 star 为准，star 即收录，无需二次判断
2. 已公开（public repo）
3. Star ≥ 500（除非有特殊代表性）
4. 收录上限 **42 个**，按星数倒序

### 剔除规则

- 剔除时在 README.md 对应条目**标题**旁注明 `❌ [YYYY-MM-DD] 原因`
- 超出 42 个时按星数淘汰最低者

---

## README 条目格式

```markdown
## N. repository-name (Xk ⭐)

**🔗** https://github.com/owner/repo  
**🍴** Fork Xk | **🔄** Updated YYYY-MM-DD  
**👤** 作者简介（1句话）

> 仓库描述（精炼到 1-2 句话）
```

---

## 双语策略

- **README.md**（中文）与 **README.en.md**（英文）必须同步，同一 commit 提交
- 中文版顶部：`**中文** | [English](./README.en.md)`
- 英文版顶部：`[中文](./README.md) | **English**`

---

## 维护流程

### Step 1：拉取最新

```bash
cd top-stars-ops/lists/skills-top-stars
git pull
```

### Step 2：抓取列表（翻完所有页）

1. 访问 https://github.com/stars/wind8ai/lists/skills
2. 核对星数变化、新增/剔除项
3. 整理变化清单，**等八风确认后再写文件**

### Step 3：更新并提交

```bash
git add README.md README.en.md
git commit -m "chore: update skills-top-stars YYYY-MM-DD"
git push
```

---

## Git 身份

列表仓提交使用 wind8ai 身份（`~/.gitconfig-wind8ai`）。
