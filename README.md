# MoviePilot-Plugins

> **📌 本仓库说明（Fork）**
>
> 本仓库 fork 自 **[JinxJie/MoviePilot-Plugins](https://github.com/JinxJie/MoviePilot-Plugins)**，原作者 **JinxJie**，在此感谢原作者的工作。
>
> 本 fork 修复了 **NodeSeek 自动签到** 插件的一个关键 bug：原版本在所有请求路径中错误地剔除了 Cookie 里的 `session` 字段，而 `session` 正是 NodeSeek 的登录态凭证——缺失时签到接口必然返回 `USER NOT FOUND`，导致插件永远误报「Cookie 已失效」。修复后（v1.0.2 / v3.0.1）完整发送全部 Cookie 字段，签到恢复正常。

JinxJie 的 [MoviePilot](https://github.com/jxxghp/MoviePilot) 第三方插件库。

## 插件列表

| 插件 | 目录 | 版本 | 说明 |
|------|------|------|------|
| NodeSeek 自动签到 | [`plugins.v2/nodeseek`](plugins.v2/nodeseek) | 1.0.2（V3 版 3.0.1） | NodeSeek 论坛每日自动签到、鸡腿收益统计、消息通知（已修复 session Cookie 被剔除导致误报失效的问题） |
## 📖 使用说明

**1. 添加仓库地址**

在 MoviePilot 「插件管理」中添加仓库地址：
```
[https://github.com/zf-ui/MoviePilot-Plugins-1]
```

**2. 安装与配置**

- 在 MoviePilot 中安装插件。
- 根据插件说明配置相关参数。
- 启用插件并设置定时任务（如需要）。

## 🧩 插件详情

点击插件名展开查看功能与更新历史。
</details>
**v1.0.1 · 签到自动化 · NodeSeek 论坛**

**功能：**
NodeSeek 论坛每日自动签到，使用 curl_cffi 模拟 Chrome 浏览器指纹绕过 Cloudflare 拦截，支持鸡腿收益统计、签到历史记录和消息通知。

**标签：**
论坛签到、每日定时、自动化、数据统计、消息通知

**特点：**
- 📅 支持 Cron 定时自动签到（默认每天 00:30，可自定义）
- 🛡️ 使用 curl_cffi 模拟 Chrome 指纹，绕过 Cloudflare 拦截
- 🍗 鸡腿收益统计：累计签到天数、累计鸡腿、本月签到
- 📋 签到历史记录（最近 12 条）
- 🔔 通知：签到成功 / 今日已签到 / 签到失败 / Cookie 失效
- ⌨️ 命令 `/nodeseek` 与 API `/nodeseek/sign` 手动签到

**使用说明：**
1. 在 MoviePilot 插件管理中添加本仓库地址并安装插件。
2. 浏览器登录 NodeSeek，F12 → Application → Cookies 复制 `nodeseek.com` Cookie 值，填入插件配置。
3. 配置签到时间（默认每天 00:30；触发后会内置随机等待约 1 分钟再开始签到）。
4. 确保安装 `curl_cffi` 依赖，否则会被 Cloudflare 拦截（插件会自动回退 requests 并提示）。

**免责声明：**
本插件仅通过站点现有接口执行签到操作，不会修改任何站点数据。站点规则、接口或防护策略变更可能导致功能异常，请自行评估后使用；因使用本插件产生的任何问题，开发者不承担责任。

**更新说明：**
- v1.0.1：修复今日已签到状态识别，调整页面布局与设置说明。
- v1.0.0：首发版本，支持每日定时自动签到、curl_cffi 过 Cloudflare、鸡腿收益统计、签到历史、消息通知、手动签到命令与 API。
- v3.0.1【fork 修复】修复签到请求错误剔除 session Cookie 导致接口必然返回 USER NOT FOUND（误报 Cookie 已失效）的问题，现在完整发送全部 Cookie 字段。
</details>


## ⚠️ 注意事项

- 本插件库中的插件均为个人维护，使用前请仔细阅读说明。
- 部分插件需要特定权限或配置才能正常使用。
- 如遇到问题，请先查看插件说明或提交 Issue。
- 建议定期更新插件以获取最新功能和修复。

## 目录结构

```text
MoviePilot-Plugins/
├── docs/                       # 官方文档
├── icons/                      # 插件图标
├── plugins/                    # V1 插件
├── plugins.v2/                 # V2 插件
│   ├── hhlottery/              # HHCLUB 自动抽奖
│   ├── nodeseek/               # NodeSeek 自动签到
│   ├── pluginresidueclean/     # 插件残留清理
│   └── dian115sign/            # 癫影自动签到
├── scripts/                    # 官方脚本
├── tests/                      # 官方测试
├── package.json                # V1 插件索引
├── package.v2.json             # V2 插件索引
├── package.v3.json             # V3 插件索引
└── README.md                   # 仓库说明
```

## 开发新插件

参考 [官方插件开发文档](https://wiki.movie-pilot.org/)。

## 致谢

- [MoviePilot](https://github.com/jxxghp/MoviePilot)
- [jxxghp/MoviePilot-Plugins](https://github.com/jxxghp/MoviePilot-Plugins)
