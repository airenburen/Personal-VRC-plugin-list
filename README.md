# 自用 VRChat VPM 插件列表

按 VRChat 官方 [vpm-listing-curated](https://github.com/vrchat-community/vpm-listing-curated) 的结构维护的个人 VPM 列表。

## 怎么用

在 VCC（VRChat Creator Companion）里：Settings → Packages → Add Repository，粘贴：

```
https://<你的GitHub用户名>.github.io/<仓库名>/index.json
```

## 怎么加/改包

编辑仓库根目录的 `source.json`：

- 顶层：`name` / `id` / `description` / `author` / `infoLink` / `url` / `bannerUrl`
- `packages[]`：每个包写 `id` 和 `releases[]`（一串指向 VPM 包 `.zip` 的直链，新版本放最前面）
- `githubRepos[]`：也可以只填 `owner/repo`，构建时会自动抓取这些仓库的所有 release zip

改完 push 后，GitHub Actions 会自动重建 `index.json` 并发布到 GitHub Pages。

## 目录结构

- `source.json`：源清单（你维护这个）
- `Website/`：GitHub Pages 站点（`index.html` / `app.js` 构建时由模板渲染），构建产物 `index.json` 也生成在这里
- `.github/workflows/build-listing.yml`：构建 + 部署工作流