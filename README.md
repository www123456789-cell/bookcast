# bookcast — 个人播客源（第 2 版）

## 这版改了什么（针对苹果的硬性要求）

苹果官方《Podcast RSS feed technical requirements》里有两条我们之前违反了：

| 苹果的要求 | 上一版 | 这一版 |
|---|---|---|
| "Use only **ASCII filenames and URLs** that include a-z, A-Z, or 0-9" | 文件名是 `01 第 1 节.mp3`（中文+空格）| **改成 `ep01.mp3` / `ep02.mp3` / `ep03.mp3`** |
| "Required tags → **Artwork**" | 没有封面 | **加了 `cover.png`（1400×1400，RGB 无透明）** |

另外补上了 `xmlns:content` 命名空间（苹果文档的示例里有）。
章节标题仍然是中文——那是在 `<title>` 文本里，不受 ASCII 限制。

## 上传步骤（纯网页）

1. 打开 https://github.com/www123456789-cell/bookcast/upload/main
2. 资源管理器打开本文件夹，**Ctrl+A 全选，拖进虚线框**
3. 等上传完 → **Commit changes**

上传后仓库根目录应该有这些新文件：

```
feed.xml          cover.png         .nojekyll
ep01.mp3  ep01.vtt  ep01.srt
ep02.mp3  ep02.vtt  ep02.srt
ep03.mp3  ep03.vtt  ep03.srt
```

旧的 `01 第 1 节.mp3` 之类**可以留着不管**（feed 已经不再引用它们），也可以之后有空删掉。

## 然后在 iPhone 上

**必须删掉旧节目重新添加**，否则苹果用的还是缓存里的旧 feed：

1. 播客 App → 资料库 → 左滑「查理九世4：法老王之心（AI 朗读）」→ 删除
2. 资料库 → 右上角「…」→ 通过 URL 添加节目 → 粘贴
   `https://www123456789-cell.github.io/bookcast/feed.xml`
3. 等 1~2 分钟让它抓封面和剧集，然后播放一期 → 点「文稿」

## 文件说明

| 文件 | 说明 |
|---|---|
| `feed.xml` | 播客订阅源（URL 全部 ASCII，含封面与逐句文稿标签）|
| `cover.png` | 节目封面 1400×1400 |
| `epNN.mp3` | 每章一个音频 |
| `epNN.vtt` | 逐句文稿（苹果播客的「文稿」面板读它）|
| `epNN.srt` | 同样内容转 SRT，给 VLC/nPlayer 用 |
| `.nojekyll` | 让 Pages 不做 Jekyll 处理 |

## 版权提醒

公开仓库 = 音频对外可下载、可被搜索引擎收录。测试阶段只有 13 分钟；
要放整本书之前请先想清楚这一点，或改用 Cloudflare 隧道（不落地、地址不可猜）。
