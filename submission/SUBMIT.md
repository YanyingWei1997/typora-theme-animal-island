# 提交到 Typora 官方主题库 · 操作指南

把 Animal Island 提交到 [Typora 官方主题市场](https://theme.typora.io) 的完整流程。

## 📂 本目录结构

```
submission/
├── _posts/
│   └── theme/
│       └── 2026-05-24-animal-island.md          ← 主题 post（已写好）
├── thumbnails/
│   └── animal-island-thumbnail.png              ← 自己截图：250×200 px
├── media/
│   └── theme/
│       └── animal-island/
│           ├── preview.png                       ← 自己截图：主预览
│           └── (可选: preview-dark.png 等)
└── SUBMIT.md                                     ← 本文件
```

## 🪜 步骤

### 1. 截图

需要两张图：

| 文件 | 尺寸 | 放在哪 |
|---|---|---|
| `animal-island-thumbnail.png` | **250 × 200 px** | `submission/thumbnails/` |
| `preview.png` | **1200 × 800 px**（或更大） | `submission/media/theme/animal-island/` |

截图技巧：
- 在 Typora 里打开一份示例 Markdown（包含 H1/H2/H3、正文、引用、代码块、表格、列表）
- 用 macOS 的 `Cmd+Shift+4` 框选截图
- 缩略图用图片软件裁成 250×200（推荐图：H1 标题 + 引用块 + 一段正文）

截好后**删除两个 placeholder 文件**（`PLACE_*.md`）。

### 2. Fork Typora 官方主题库

```bash
gh repo fork typora/theme.typora.io --clone
cd theme.typora.io
git checkout gh-pages   # ⚠️ 主分支是 gh-pages，不是 main/master
```

### 3. 把 submission/ 的文件复制过去

假设你在 `theme.typora.io/` 目录下，且本仓库 `typora-theme-animal-island/` 在隔壁：

```bash
# 1. 主题 post
cp ../typora-theme-animal-island/submission/_posts/theme/2026-05-24-animal-island.md \
   _posts/theme/

# 2. 缩略图
cp ../typora-theme-animal-island/submission/thumbnails/animal-island-thumbnail.png \
   thumbnails/

# 3. 大图预览（注意 media/theme/animal-island/ 目录要先建好）
mkdir -p media/theme/animal-island
cp ../typora-theme-animal-island/submission/media/theme/animal-island/preview.png \
   media/theme/animal-island/
```

### 4. 提交并发起 PR

```bash
git add _posts/theme/2026-05-24-animal-island.md \
        thumbnails/animal-island-thumbnail.png \
        media/theme/animal-island/

git commit -m "Add Animal Island theme"
git push origin gh-pages

gh pr create \
  --repo typora/theme.typora.io \
  --base gh-pages \
  --title "Add Animal Island theme" \
  --body "Submitting **Animal Island** — a cozy Animal Crossing inspired theme with Light + Dark variants.

- Repo: https://github.com/YanyingWei1997/typora-theme-animal-island
- Thumbnail: 250×200 px (added under \`thumbnails/\`)
- Preview: added under \`media/theme/animal-island/\`
- License: MIT
- Tested on: macOS"
```

### 5. 等审核合并

通常几天到几周。合并后会出现在 https://theme.typora.io

## 📋 检查清单（PR 前自查）

- [ ] `_posts/theme/2026-05-24-animal-island.md` YAML 字段全部填写
- [ ] `thumbnail:` 字段 = 实际文件名（`animal-island-thumbnail.png`）
- [ ] `homepage` / `download` 链接可访问
- [ ] 缩略图严格 250×200 px
- [ ] preview.png 已上传
- [ ] PLACE_*.md placeholder 已删除
- [ ] 主仓库的 `animal-island.css` 和 `animal-island-dark.css` 在 `main` 分支可见
