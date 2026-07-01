# 我的日历

个人日历应用，支持记录运动、重要事项、日程、医疗健康、行程、inLove 等多种类型，提供跑量统计图表。

## 部署信息

- **访问地址**：[https://hello-coder-d3geutyjt8abd7eba-1441638915.tcloudbaseapp.com/](https://hello-coder-d3geutyjt8abd7eba-1441638915.tcloudbaseapp.com/)
- **自定义域名**：[https://mycalendar.hello-coder.cn](https://mycalendar.hello-coder.cn)
- **GitHub 仓库**：[https://github.com/wangxincyndi-dot/mycalendar](https://github.com/wangxincyndi-dot/mycalendar)
- **环境 ID**：`hello-coder-d3geutyjt8abd7eba`

## 技术架构

- **前端**：纯 HTML/CSS/JS 单文件应用
- **数据代理**：CloudBase 云函数 `cloudDataProxy`（Admin SDK，跳过 `_openid` 隔离）
- **数据持久化**：CloudBase NoSQL 数据库
- **部署方式**：CloudBase 静态网站托管 + 云函数

## 跨设备同步

使用云函数 `cloudDataProxy` 作为数据代理层。云函数使用 Admin SDK 操作数据库，无视 `_openid` 隔离，所有设备共享同一份数据。前端通过 `app.callFunction()` 读写，只需匿名登录即可。

## 数据库结构

| 集合 | 用途 |
|---|---|
| `calendar_entries` | 日历条目，按日期键 `dateKey` 索引 |
| `calendar_meta` | 应用元数据（备注文本、地点历史） |

## 云函数

| 函数名 | 用途 |
|---|---|
| `cloudDataProxy` | 数据代理，支持 load / save / deleteDate 三个 action |

## 最近部署

- **最近部署时间**：2026-07-01 13:42 CST
- **云函数**：`cloudDataProxy` (Runtime: Nodejs18.15)
- **静态托管**：index.html（纯 Web 应用）
- **变更**：UI 样式优化 — 导航按钮统一‹›风格、日期圆角背景移除、节假日标签移到日期下方、主色调微调

### 控制台入口

| 资源 | 链接 |
|---|---|
| 云函数 | [https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/scf/detail?id=cloudDataProxy&NameSpace=hello-coder-d3geutyjt8abd7eba](https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/scf/detail?id=cloudDataProxy&NameSpace=hello-coder-d3geutyjt8abd7eba) |
| 静态托管 | [https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/static-hosting](https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/static-hosting) |
| 数据库 | [https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/db/doc](https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/db/doc) |
| 环境概览 | [https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/overview](https://tcb.cloud.tencent.com/dev?envId=hello-coder-d3geutyjt8abd7eba#/overview) |

## 更新方式

修改 `index.html` 后，通过 CloudBase 工具重新上传静态托管即可。如云函数有变更，需重新部署云函数。
