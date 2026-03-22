# Sveltia CMS 使用说明

## 目录说明
- `admin/index.html`：Sveltia CMS 后台入口
- `admin/config.yml`：CMS 集合、字段与媒体目录配置
- `content/site.json`：站点基础信息
- `content/start.json`：开始在一起的日期
- `content/anniversary.json`：纪念日列表
- `content/memories/`：精彩瞬间 markdown 内容目录
- `content/timeline_events/`：时间线 markdown 内容目录
- `content/images/`：页面与 CMS 使用的图片资源目录

## 本地预览
1. 在仓库根目录运行 `python -m http.server 8000`
2. 另开一个终端运行 `npx decap-server`
3. 访问 `http://localhost:8000/` 查看页面
4. 访问 `http://localhost:8000/admin/` 打开 CMS

## CMS 配置
- 本地开发使用 `local_backend: true`
- `admin/config.yml` 中的 `backend.repo` 会被前端用作 GitHub API 回退读取目录的仓库信息，因此线上仓库应保持公开可读
- CMS 真正写回本地文件依赖 `decap-server` 代理
- 如果没有启动 `npx decap-server`，后台里看起来可以编辑，但内容不会写入本地仓库

## 内容编辑规则
- 所有日期统一保存为 `YYYY-MM-DD`
- 纪念日字段：`name`、`date`
- 精彩瞬间 frontmatter 字段：`title`、`date`、`image`，正文作为 `description`
- 时间线 frontmatter 字段：`title`、`date`，正文作为 `description`
- `memories` 与 `timeline_events` 文件名格式为 `年月日时分秒-标题`，前端会按日期升序渲染
- 图片统一保存在 `content/images/`

## 发布前检查
1. 确认 `content/memories/` 和 `content/timeline_events/` 下 markdown frontmatter 合法
2. 确认首页、纪念日、相册、时间线均能正常渲染
3. 确认 `登录 CMS` 链接指向 `admin/`
4. 本地测试时确认 `python -m http.server 8000` 与 `npx decap-server` 同时运行

## 回滚方式
- 内容回滚：使用 Git 恢复 `content/` 目录对应历史版本
- CMS 配置回滚：恢复 `admin/config.yml` 和 `admin/index.html`
- 页面回滚：恢复 `index.html`

