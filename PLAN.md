# 开发计划
## Sveltia CMS 重构计划
目标：重构CMS的存储结构

### 需求列表
- 约束内容模型：字段类型、必填项、日期格式、图片地址规则
- 为图片与封面资源预留统一目录，如 `assets/images/`
- 明确部署影响：CMS 后台路径、静态资源缓存、权限控制
- 建立 `content/` 目录，拆分index.html中的内容
    - 精彩瞬间`memories`: 
        - 创建memories目录
        - 将memories.json中的内容拆分成独立的markdown文件，文件名为日期（年月日时分秒微秒），文件的yml字段包含title, date和image字段，其中description字段作为body
        - 按照markdown的文件名排序（时间升序）
        - 照片存储在`content/images`中，image字段填充照片的地址，照片文件名为memories前缀+markdown文件名
        - Sveltia CMS支持添加memories，添加会话中包含title, date, description字段，以及上传照片，照片以时间（年月日时分秒微秒）重命名保存，系统自动将保存的照片名称填入image字段
    - 时间线`timelineEvents`
        - 创建timeline_events目录
        - 将timeline_events.json中的内容拆分成独立的markdown文件，包含title和date，其中desciption作为body
        - 按照markdown的文件名排序（时间升序）
        - Sveltia CMS支持添加event，添加会话中包含title, date和desciption
- 其他结构不变
- 适配前端，确保能正确获取内容并渲染，注意不要做其他额外的修改
    - anniversaryCountdown按照时间顺序排序（data字段）
    - memories按照时间升序排序（data字段）
    - timelineEvents按照时间升序排序（data字段）
