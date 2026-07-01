---
name: skills-top-stars-maintainer
description: 维护 GitHub 高星 Skills 精选列表。当用户提到「更新 skills-top-stars」、「维护 wind8ai 的 Skills 列表」、「检查 skills 仓库星数变化」、「整理 skills-top-stars」时触发。
---

# skills-top-stars-maintainer

维护 [wind8ai/skills-top-stars](https://github.com/wind8ai/skills-top-stars) 排行榜。

**完整规范见 top-stars-ops，本文件仅类目入口与路径。**

## 必读（执行前）

1. [docs/top-stars-ops-spec.md](https://github.com/wind8ai/top-stars-ops/blob/main/docs/top-stars-ops-spec.md)
2. [registry/categories.yaml](https://github.com/wind8ai/top-stars-ops/blob/main/registry/categories.yaml) — 类目 `skills`

## Monorepo 路径

| 路径 | 远程 |
|------|------|
| `lists/skills-top-stars/` | `git@github.com:wind8ai/skills-top-stars.git` |
| `maintainers/skills-top-stars-maintainer/` | `git@github.com:wind8ai/skills-top-stars-maintainer.git` |

## 维护命令

```bash
git clone --recurse-submodules git@github.com:wind8ai/top-stars-ops.git
cd top-stars-ops

./scripts/export-star-list.sh skills
./scripts/diff-registry.sh skills
./scripts/render-readme.py skills

cd lists/skills-top-stars
git add README.md README.en.md
git commit -m "chore: update skills-top-stars $(date +%F)"
git push

cd ../..
git add lists/skills-top-stars registry/skills.json
git commit -m "chore: bump skills-top-stars submodule and registry"
git push
```

## 确认门

批量改描述 / 新增收录 / 剔除 → **等八风确认后再写文件**。

## Git 身份

列表仓提交使用 wind8ai（`~/.gitconfig-wind8ai`）。
