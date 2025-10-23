<p align="center">
  <img src="https://socialify.git.ci/RunWang925/Simple-Homepage/image?custom_description=%E4%B8%80%E4%B8%AA%E5%9F%BA%E4%BA%8EVue%E7%9A%84%E7%AE%80%E7%BA%A6%E9%A3%8E%E4%B8%AA%E4%BA%BA%E4%B8%BB%E9%A1%B5&description=1&font=KoHo&forks=1&issues=1&language=1&name=1&owner=1&pattern=Brick+Wall&pulls=1&stargazers=1&theme=Light" alt="Simple-Homepage" />
</p>

## 项目介绍
基于鹊楠大佬的 [Simple-Homepage](https://github.com/QNquenan/Simple-Homepage)项目进行二次开发，感谢原作者的开源贡献！本项目在保留原设计轻量简洁风格的基础上，根据个人需求补充了备案信息展示功能并优化了部分样式。如果喜欢这个项目的基础框架，欢迎去原仓库给作者点个小星星🌟支持一下～

## 核心修改说明
1. **样式优化**：调整备案链接样式
   - 正常状态：文字色跟随主题（`var(--text-color)`），无下划线
   - 悬停状态：文字变为主题色（粉色），底部显示细主题色下划线
2. **功能扩展**：在 `MainCard.vue` 中添加备案信息区域（约 163-173 行），支持自定义文字及链接
3. **个性化配置入口**：
   - 网站图标：替换 `src/favicon.ico` 文件
   - 站点元信息：修改 `index.html` 中的标题、描述等
   - 底部信息：修改 `src/views/MainCard.vue` 的 `footer` 区域

## 完整配置指南
所有可自定义内容集中在 `src/config/` 目录及指定文件中，修改方式如下：

### 1. 基础信息配置（`src/config/config.json`）
存储个人核心信息，直接修改 JSON 字段即可：
```json
{
  "name": "姓名", // 显示在主页的名称
  "age": "01", // 建议填写出生年份后两位（如 01 代表 2001 年）
  "zodiac": "天蝎座♏", // 支持 emoji 展示星座
  "avatarUrl": "头像图片链接", // 个人头像的网络链接或本地路径
  "emjoi": "😋", // 个人签名前的表情符号
  "infoTags": {
    "sex": "男", // 性别（支持自定义文字）
    "school": "学校/教育背景", // 教育相关信息
    "province": "所在省份" // 地区信息
  },
  "professions": ["IT从业者", "DIY入门者", "后端初学者"] // 职业标签数组
}
```

### 2. 链接按钮配置（src/config/linkBtn.json）

配置主页展示的外部链接按钮，支持图标、颜色自定义：
```json
{
  "linkBtn": [
    {
      "icon": "fa7-solid:blog", // 图标名称（格式：图标集标识:图标名）
      "text": "博客", // 按钮显示文字
      "color": "#ffb3b3", // 按钮背景色（十六进制色值）
      "url": "https://hexo.814925.xyz/" // 跳转链接
    },
    {
      "icon": "mdi:github",
      "text": "Github",
      "color": "#2b2b2b",
      "url": "https://github.com/RunWang925"
    }
    // 可继续添加更多按钮...
  ]
}
```
### 3. 技术栈展示配置（src/config/techStack.json）
通过图标展示个人技能，配置格式如下：
```json
{
  "techStack": [
    {
      "icon": "vscode-icons:file-type-html", // 技术对应的图标
      "name": "HTML" // 技术名称
    },
    {
      "icon": "devicon:css3",
      "name": "CSS"
    }
    // 可继续添加更多技术...
  ]
}
```

### 4.待办事项配置（src/config/todo.json）
展示个人计划，支持标记完成状态：
```json
{
  "todoList": [
    {
      "text": "学习Vue3组件化开发", // 待办内容
      "checked": false // true=已完成（显示删除线），false=未完成
    },
    {
      "text": "优化个人主页加载速度",
      "checked": true
    }
    // 可继续添加更多待办...
  ]
}
```

### 5. 打字机文本配置（src/config/typewriter.json）

配置主页打字机动画的轮播文本，数组元素为逐行显示的内容：
```json
[
  "你好鸭，欢迎来到我的主页！",
  "彼方尚有荣光在，世界不止眼前的苟且",
  "累了可以在我这里歇歇脚嗷~",
  "May you happy every day！"
]
```

### 6. 底部版权与备案信息（src/views/MainCard.vue）
修改文件中 footer 区域的 HTML 代码，自定义版权、备案及其他链接：
```json
<div class="footer">
  <p>
    ©2025 佩奇
    |
    <a href="https://hexo.814925.xyz" target="_blank" class="beian-link">关于</a>
    |
    <a href="https://beian.miit.gov.cn/" target="_blank" class="beian-link">渝ICP备2024044325号</a>
    |
    <a href="https://beian.mps.gov.cn/#/query/webSearch?code=50023302000356/" target="_blank" class="beian-link">渝公网安备50023302000356号</a>
  </p>
</div>
```


## 图标修改方法
项目使用 **Iconify** 图标库（依赖 `@iconify/vue`），支持数千个免费图标，替换步骤如下：

1. **查找图标**  
   访问 [Iconify 官方图标库](https://icon-sets.iconify.design/)，搜索关键词（如 "github"、"email"）。

2. **复制标识**  
   每个图标有唯一标识，格式为 `图标集:图标名`，例如：fa7-solid:blog

3. **替换配置**  
   将复制的图标标识粘贴到 `linkBtn.json` 或 `techStack.json` 的 `icon` 字段中，示例如下：

   ```json
   // linkBtn.json 示例（按钮图标替换）
   {
     "linkBtn": [
       {
         "icon": "mdi:github",  // 此处替换为从 Iconify 复制的图标标识
         "text": "Github",
         "color": "#2b2b2b",
         "url": "https://github.com/RunWang925"
       }
     ]
   }



## 安装与使用

1. 克隆项目到本地：

   ```bash
   git clone https://github.com/RunWang925/Simple-Homepage.git
   ```

2. 安装依赖：

   ```bash
   npm install
   ```

3. 启动开发服务器：

   ```bash
   npm run dev
   ```
   打开终端提示的本地地址（通常为 http://localhost:5173）即可预览。
4. 构建生产版本：

   ```bash
   npm run build
   ```
   构建后的文件会生成在 dist 目录，可直接部署到服务器。

5. 预览生产构建：
   ```bash
   npm run preview
   ```

## 主题切换

项目支持明暗主题切换，点击页面右上角的主题切换按钮即可在浅色和深色主题间切换。

## 小白部署教程
关于 Cloudflare 配置与服务器部署的完整教程，可参考主页「[关于](https://814925.xyz)」链接跳转文章的详细步骤助你快速完成部署 ✨