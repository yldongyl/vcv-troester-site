# VCV 设备功能与失效模式视图 · Render 静态站点

本站为纯静态 HTML（1 个总览 + 30 个设备页，页面自包含、无构建依赖），发布到 Render Static Site 即可。

## 部署步骤（约 5 分钟）

1. **建 GitHub 仓库**：新建一个仓库（私有也可），把本目录内容推到仓库根，例如：
   ```bash
   git remote add origin https://github.com/<你的用户名>/vcv-troester-site.git
   git push -u origin master
   ```
2. **Render 连接**：登录 [render.com](https://dashboard.render.com) → **New** → **Static Site** → 授权并选择该仓库。
3. **关键设置**（若用仓库内 `render.yaml` 走 Blueprint 会自动带上，手动创建则按此填）：
   - Build Command：**留空**（无构建）
   - Publish Directory：**`.`**（一个英文句点＝仓库根；也可留空。注意不能填 `/`，Render 会报 "StaticPublishPath must be a relative path"）
4. 点 **Create Static Site**，约 1 分钟得到 `https://vcv-troester-site.onrender.com`，自动 HTTPS + 全球 CDN。
5. 以后更新：改完 HTML 直接 `git push`，Render 自动重新发布。

## 说明

- 文件名保留中文（如 `01_挤出机_三层共挤.html`），浏览器访问会自动百分号编码，功能不受影响；如需更短的分享链接，可统一改为英文数字 slug（如 `01.html`），需同步替换 index.html 中的链接。
- 页内互链全部是相对路径（设备页 → `index.html` 返回总览），无需任何服务端逻辑。
- `404.html` 为兜底页；在 Render 静态站设置中可将 Error Page 指向它。
