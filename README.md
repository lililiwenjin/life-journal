# 生活拾遗 · Hexo + Butterfly 生活手帐

一个 Markdown 驱动、适合长期维护的个人生活手帐起点。内含示例文章、封面、分类/标签/关于页面和 GitHub Pages 自动部署工作流。

## 本地启动

要求 Node.js 20+（建议 22）。

```bash
npm install
npm run server
```

打开 http://localhost:4000 。

## 发布到 GitHub Pages

1. 创建公开仓库 `life-journal`，把本项目推送到 `main`。
2. 在 `_config.yml` 把 `USERNAME` 替换成 GitHub 用户名；如仓库不是 `life-journal`，同步修改 `url` 和 `root`。
3. **注意：示例文章的 `cover` 和图片链接也含 `/life-journal/`，更换仓库名时需要同步修改。** 更推荐以后使用自定义域名，`root: /` 时资源路径写为 `/images/...`。
4. 在仓库 Settings → Pages → Build and deployment → Source 选择 **GitHub Actions**。
5. 首次运行 `npm install` 后，请将生成的 `package-lock.json` 一并提交，锁定依赖版本。后续可以把工作流中的 `npm install` 改成 `npm ci`。
6. 推送代码，等待 Actions 成功后访问 `https://USERNAME.github.io/life-journal/`。

## 写新文章

```bash
npx hexo new "周末散步"
```

编辑 `source/_posts/周末散步.md`，添加 Front Matter，例如：

```yaml
---
title: 周末散步
date: 2026-11-05 18:00:00
categories: [生活手帐]
tags: [散步, 秋天]
cover: /life-journal/images/walk.jpg
---
```

将图片放在 `source/images/walk.jpg`，正文中使用 `![照片](/life-journal/images/walk.jpg)`。

## 视频

文章可使用 HTML5 `<video>` 标签或平台嵌入代码。大量视频建议使用对象存储或视频平台；注意跨域、移动端播放和视频格式兼容。

## 维护原则

- 不修改 `node_modules` 中的 Butterfly 源码。
- `_config.butterfly.yml` 用于主题配置覆盖。
- 保留 `source/` 下的 Markdown 和原始照片，未来可迁移到其他静态站点。
- 这个起点未实现自定义摄影墙或时间轴页面；可在基础博客稳定后逐步增加。
