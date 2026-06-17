# 我的日历

个人日历应用，支持记录运动、重要事项、日程、医疗健康、行程、inLove 等多种类型，提供跑量统计图表。

## 部署信息

- **部署平台**：腾讯云 CloudBase
- **环境 ID**：`hello-coder-d3geutyjt8abd7eba`
- **访问地址**：[https://hello-coder-d3geutyjt8abd7eba-1441638915.tcloudbaseapp.com/index.html](https://hello-coder-d3geutyjt8abd7eba-1441638915.tcloudbaseapp.com/index.html)

## 技术架构

- **前端**：纯 HTML/CSS/JS 单文件应用
- **数据持久化**：CloudBase NoSQL 数据库（匿名登录）
- **部署方式**：CloudBase 静态网站托管

## 数据库结构

| 集合 | 用途 |
|---|---|
| `calendar_entries` | 日历条目，按日期键 `dateKey` 索引 |
| `calendar_meta` | 应用元数据（备注文本、地点历史） |

## 更新方式

修改 `我的日历.v19.html` 后，将其复制为 `index.html`，通过 CloudBase 工具重新上传即可。
