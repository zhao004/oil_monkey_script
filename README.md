# Oil Monkey Script

一个功能强大的油猴脚本集合，用于增强各类网站的中文使用体验。

## 项目结构

```
oil_monkey_script/
├── translator/                  # 翻译脚本目录
│   ├── translator.meta.js      # 油猴脚本元数据
│   └── translator.user.js      # 主脚本文件
├── index.js                     # 入口文件 (占位符)
├── package.json                 # 项目配置
└── README.md                    # 项目文档
```

---

## 插件列表

### 1. 翻译机 (translator)

**版本**: 1.0.5  
**作者**: HolynnChen/zhao  
**命名空间**: https://github.com/zhao004

#### 插件描述

该脚本用于翻译各类常用社交网站为中文，不会经过中间服务器。

#### 支持的网站

| 网站 | 匹配规则 | 翻译内容 |
|------|----------|----------|
| Twitter | `*://*.twitter.com/*` | 推文、背景信息 |
| X.com | `*://*.x.com/*` | 推文、背景信息 |
| YouTube | `*://*.youtube.com/*` | 评论区、视频简介、CC 字幕 |
| Facebook | `*://*.facebook.com/*` | 帖子内容、评论区 |
| Reddit | `*://*.reddit.com/*` | 帖子标题、内容、评论 |
| 5ch | `*://*.5ch.net/*` | 标题、内容 |
| Discord | `*://*.discord.com/*` | 聊天内容 |
| Telegram | `*://*.telegram.org/*` | 聊天内容 |
| Quora | `*://*.quora.com/*` | 标题、帖子内容 |
| TikTok | `*://*.tiktok.com/*` | 评论区 |
| Instagram | `*://*.instagram.com/*` | 评论区 |
| Threads | `*://*.threads.net/*` | 帖子 |
| GitHub | `*://*.github.com/*` | Issues、Discussions |
| Bluesky | `*://*.bsky.app/*` | 主页帖子、回复 |

#### 支持的翻译引擎

- 谷歌翻译 / 谷歌翻译 mobile
- 腾讯翻译 / 腾讯 AI 翻译
- 有道翻译 mobile
- 百度翻译
- 彩云小译
- 必应翻译
- Papago 翻译
- 阿里翻译
- 爱词霸翻译
- Deepl 翻译

#### 功能特性

**通用设置**:
- **不翻译中文 (简体)** - 智能识别并跳过简体中文内容
- **不翻译中文 (繁体)** - 智能识别并跳过繁体中文内容
- **自动过滤 URL** - 翻译前移除文本中的链接
- **显示翻译源** - 在翻译结果上显示使用的引擎
- **全屏时不显示** - 全屏模式下自动隐藏悬浮球
- **替换式翻译** - 直接替换原文而非显示在下方
- **压缩缓存** - 压缩存储翻译结果以节省空间

**规则定制**:
- 每个网站可独立启用/禁用
- 每个网站的每个翻译区域可独立配置
- 支持针对特定规则覆盖通用设置

#### 界面操作

**悬浮球**:
- 右上角紫色「译」字按钮
- 点击打开控制面板
- 可拖拽调整位置 (自动保存)
- 支持触摸设备操作

**控制面板**:
1. 翻译引擎选择下拉菜单
2. 当前网站启用规则展示
3. 通用设置复选框
4. 规则专属配置选项

**菜单命令** (通过 Tampermonkey 菜单访问):
- 重置控制面板位置 (刷新应用)
- 全局隐藏/展示悬浮球 (刷新应用)

#### 技术实现

**依赖库**:
```javascript
@require https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js
@require https://cdn.jsdelivr.net/npm/js-base64@3.7.4/base64.min.js
@require https://cdn.jsdelivr.net/npm/lz-string@1.5.0/libs/lz-string.min.js
@require https://cdn.jsdelivr.net/gh/Tampermonkey/utils@.../make_GM_xhr_more_parallel_again.js
```

**核心机制**:
- URL 匹配规则系统
- 20ms 轮询检测新内容
- sessionStorage 缓存翻译结果
- 百度 API 语言检测
- GM_xmlhttpRequest 并行请求优化

**权限声明**:
```javascript
@connect fanyi.baidu.com
@connect translate.google.com
@connect dict.youdao.com
@connect www.bing.com
@connect api.interpreter.caiyunai.com
@connect papago.naver.com
@connect ... (更多翻译服务域名)
```

#### 安装地址

- **更新 URL**: https://github.com/zhao004/oil_monkey_script/blob/master/translator/translator.meta.js
- **下载 URL**: https://github.com/zhao004/oil_monkey_script/blob/master/translator/translator.user.js

#### 注意事项

- 翻译请求直接发送至各翻译服务商，不经过中间服务器
- 部分翻译引擎 (腾讯/有道/彩云/Papago) 需要首次加载时获取 token
- 建议在 PC 端浏览器使用以获得最佳体验
- 如遇翻译失败，可尝试切换其他翻译引擎
- 刷新页面后应用新的配置

---

## 安装方法

### 前置要求

1. 安装浏览器扩展:
   - [Tampermonkey](https://www.tampermonkey.net/) (推荐)
   - 或 Violentmonkey、Greasemonkey

### 安装步骤

1. 访问 [translator.user.js](https://github.com/zhao004/oil_monkey_script/raw/master/translator/translator.user.js)
2. 点击「安装」确认脚本
3. 访问支持的网站即可自动使用

---

## 项目说明

- 本项目为开源油猴脚本集合
- 所有脚本均在本地浏览器运行
- 不收集任何用户数据

## 贡献

项目地址：https://github.com/zhao004/oil_monkey_script
