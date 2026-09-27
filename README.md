# bookcast — 个人播客源

把书做成播客：每章一期，带逐句文稿。

## 部署（全程网页操作，不需要命令行）

### 1) 新建仓库
打开 https://github.com/new
- Repository name：bookcast
- 可见性：**Public**
- README / .gitignore / license 都不要勾
点 Create repository。

### 2) 上传文件
在仓库页点 **Add file → Upload files**，或者直接打开：
https://github.com/www123456789-cell/bookcast/upload/main

然后用资源管理器打开本文件夹：
`C:\Users\theon\Documents\ChatGPT\githubmd\doc2speech\podcast-deploy`

**Ctrl+A 全选，拖进网页的虚线框**（本文件夹里没有子目录，拖的都是散文件，不会出层级问题）。

等上传完成（约 4.5 MB）→ 页面下方点 **Commit changes**。

> 上传后仓库首页应该**直接**看到 feed.xml、index.html 和一堆 mp3/vtt。
> 如果看到的是一个叫 podcast-deploy 的文件夹，说明拖错了一层——删掉重传。

### 3) 开启 Pages
仓库页 → Settings → 左侧 Pages → Source 选 Deploy from a branch
→ Branch 选 main、目录选 / (root) → Save

等 1~2 分钟，打开 https://www123456789-cell.github.io/bookcast/ ，能看到页面就是成功了。

### 4) 加到 iPhone 播客 App
资料库 → 右上角「…」→ 通过 URL 添加节目 → 粘贴：

https://www123456789-cell.github.io/bookcast/feed.xml

## 目录说明

| 文件 | 说明 |
|---|---|
| feed.xml | 播客订阅源 |
| *.mp3 | 每章一个音频 |
| *.vtt | 逐句文稿（苹果播客的「文稿」面板读它） |
| *.srt | 同样内容转 SRT，给 VLC/nPlayer 用 |
| index.html | 部署自检页 |
| .nojekyll | 让 Pages 不做 Jekyll 处理 |

## 版权提醒

GitHub Pages 免费版只能用公开仓库，等于这些音频对外公开、可被搜索引擎收录。
如果是正版书内容，公开托管有被下架、牵连账号的风险。
更稳妥：只放自制或有授权的内容；或改用 Cloudflare 隧道（不落地、地址不可猜）。
