# 开发计划
## Sveltia CMS 开发计划
目标：将页面中的纪念日、时间线、相册和基础站点信息改为内容驱动，便于非开发者通过 CMS 维护。

### 需求列表
- 引入 `Sveltia CMS` 所需后台入口与配置文件，如 `admin/`、`config.yml`
- 选择 Git-based 内容源，并明确仓库分支、媒体目录、发布流程
- 将 `index.html` 中硬编码内容改为从结构化内容文件读取
- 约束内容模型：字段类型、必填项、日期格式、图片地址规则
- 为图片与封面资源预留统一目录，如 `assets/images/`
- 补充本地预览方案，确保编辑后可快速验证页面展示
- 明确部署影响：CMS 后台路径、静态资源缓存、权限控制
- 建立 `content/` 目录，拆分index.html中的内容
    - 开始在一起的日期`startDate`
        - 迁移至start.json中
    - 纪念日`anniversaryCountdown`
        - 迁移至`anniversary.json`中，包含name和date字段
        - Sveltia CMS支持添加anniversary，包含name和date字段
    - 精彩瞬间`memories`: 
        - 迁移至memories.json中，包含title, date, description和image字段
        - 照片存储在`content/images`中，image字段填充照片的地址
        - Sveltia CMS支持添加memories，添加会话中包含title, date, description字段，以及上传照片，照片以时间（年月日时分秒微秒）重命名保存，系统自动将保存的照片名称填入image字段
    - 时间线`timelineEvents`
        - 迁移至timeline_events.json中，包含title, date和desciption
        - Sveltia CMS支持添加event，添加会话中包含title, date和desciption
- 将页面的`登入`链接指向CMS后台

### 分阶段实施
1. 内容建模：梳理页面中所有可编辑内容，定义集合与字段。
2. CMS 接入：增加后台页面、配置仓库后端、设置媒体目录。
3. 前端改造：把时间线、相册、纪念日等数据从内联脚本迁移到内容文件。
4. 前端清理：清理前端页面中的硬编码内容
5. 编辑流验证：测试新增、修改、删除内容后的页面表现。
6. 发布与文档：补充编辑说明、回滚方式和上线检查清单。

### 验收标准
- 不修改源码即可新增时间线或相册条目
- 关键内容变更可通过 CMS 完成并提交到仓库
- 页面渲染结果与原设计一致，无明显布局回归
