# rickyin.github.io — 开发者站点

这个文件夹就是 `https://rickyin.github.io` 仓库的**完整内容**，整个仓库只此一份，发布多少个 app 都不需要再建新仓库。

## 结构

```
rickyin.github.io/            ← 仓库根 = 域名根
├── app-ads.txt               ← 【永远只改一次】发布人级授权，所有 app 共用
├── index.html                ← 开发者落地页（Play 里的「开发者网站」指向这里）
├── robots.txt
├── hanzi-privacy/
│   └── index.html            ← https://rickyin.github.io/hanzi-privacy/
├── <新app>-privacy/          ← 以后每加一个 app 就加一个这样的文件夹
│   └── index.html
└── _template/
    └── privacy.html          ← 隐私政策模板，复制用，不会被别人访问到（下划线开头）
```

## 新增一个 app 时做什么

1. 复制 `_template/privacy.html` → 新建文件夹 `<新app>-privacy/index.html`
2. 替换 4 个占位符 + 描述性占位块（`{{APP_NAME}}` `{{PACKAGE_ID}}` `{{EFFECTIVE_DATE}}` `{{DEV_EMAIL}}` `{{AD_FORMATS}}` 等），没做的功能整节删掉
3. 在 `index.html` 的 `<ul class="apps">` 里加一个 `<li>`
4. 把 Play 商品详情里的隐私政策网址填成 `https://rickyin.github.io/<新app>-privacy/`

**`app-ads.txt` 不用动。** 它授权的是「发布人账号 `pub-1468263849143711`」，不是某个 app。新 app 上架后 AdMob 爬虫读的还是同一个文件，自动覆盖。

## 上传

网页端：仓库页 → Add file → Upload files → 整个文件夹拖进去 → Commit。
命令行：`git push` 到 `main` 分支，Pages 会自动重新部署（约 1 分钟）。

## 检查

```bash
curl -s https://rickyin.github.io/app-ads.txt          # 应返回 google.com, pub-..., DIRECT, ...
curl -sI https://rickyin.github.io/hanzi-privacy/ | head -1   # 应返回 200
```
