# Sveltia CMS 使用说明

## 目录说明
- `admin/index.html`：Sveltia CMS 后台入口
- `admin/config.yml`：CMS 集合、字段与媒体目录配置
- `content/site.json`：站点基础信息
- `content/start.json`：开始在一起的日期
- `content/anniversary.json`：纪念日列表
- `content/memories.json`：相册内容
- `content/timeline_events.json`：时间线内容
- `content/images/`：页面与 CMS 使用的图片资源目录

## 本地预览
1. 在仓库根目录运行 `python -m http.server 8000`
2. 访问 `http://localhost:8000/` 查看页面
3. 访问 `http://localhost:8000/admin/` 打开 CMS

## CMS 配置
- 当前配置采用 Git-based 工作流，分支固定为 `master`
- `admin/config.yml` 中的 `backend.repo` 已设为 `liujin/liujin.fallsky.cn`
- 这个值来自当前本地 Git 用户名 `liujin` 与仓库目录名 `liujin.fallsky.cn`
- 如果你的真实 GitHub 仓库不是这个地址，请把 `backend.repo` 改成实际的 `owner/repo`

## 内容编辑规则
- 所有日期统一保存为 `YYYY-MM-DD`
- 纪念日字段：`name`、`date`
- 精彩瞬间字段：`title`、`date`、`description`、`image`
- 时间线字段：`title`、`date`、`description`
- 图片统一保存在 `content/images/`

## 发布前检查
1. 确认 `content/` 下 JSON 结构有效
2. 确认首页、纪念日、相册、时间线均能正常渲染
3. 确认 `登录 CMS` 链接指向 `admin/`
4. 确认 `admin/config.yml` 中的仓库信息与生产环境一致

## 回滚方式
- 内容回滚：使用 Git 恢复 `content/` 目录对应历史版本
- CMS 配置回滚：恢复 `admin/config.yml` 和 `admin/index.html`
- 页面回滚：恢复 `index.html`
