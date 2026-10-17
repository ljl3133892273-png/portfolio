# 作品集 · 刘家良

AI 应用开发 / FDE 方向个人作品集站点。

纯静态页面：无框架、无构建步骤，样式与脚本均内联在 `index.html` 中；项目截图放在 `screenshots/`，用相对路径引用。

**在线地址：** https://ljl3133892273-png.github.io/portfolio/

## 页面结构

| 区块 | 内容 |
| --- | --- |
| 首页 | 一句话定位 + 项目 / 技术栈统计 |
| 关于我 | 大模型应用工程、完整工程能力、交付与部署意识 |
| 项目作品 | 5 个项目（顺序见下），每个带轮播截图 + 演示服务在线状态 |
| 技术栈 | 大模型应用 / 后端工程 / 数据与中间件 / 前端 / 部署运维 |
| 联系方式 | 邮件与 GitHub 入口 |

项目顺序按「常用 / 常驻在线」排列：**01 运营助手（服务器常驻）→ 02 智能客服 → 03 RAG 知识库 → 04 数据问数 → 05 Octop 插件**。

## 演示状态（在线 / 按需启动）

每个项目卡片右上角有状态胶囊，演示按钮跟着状态走：

- 服务在线 → 胶囊显示「在线」（绿点脉动），按钮为可点的「访问线上系统」。
- 服务离线 → 胶囊显示「按需启动」，按钮变灰不可点（`aria-disabled`），鼠标悬停提示需要联系我开启。

状态来自同目录的 `status.json`（键：`operation-assistant` / `customer-service` / `knowledge-base` / `data-agent` / `octop-plugin`，
外加 `updated_at` 时间戳），读取顺序：同源 `status.json` → `raw.githubusercontent.com` 兜底 → 都失败时按钮保持默认（可点）。

**数据过期就自动放开**：页面用 `updated_at` 判断新鲜度，超过 90 分钟（`FRESH = 5400` 秒）就认为探测停了，
按钮一律保持可点、胶囊改为「状态未知」。避免「探测任务被限流 → 在线服务被显示成灰按钮」这种最坏情况。

`status.json` 由两端分别生成：

| 环境 | 生成方式 | 探测目标 | 刷新节奏 |
| --- | --- | --- | --- |
| GitHub Pages | `.github/workflows/probe-demos.yml` | `http://81.70.85.14:8092` / `8093` / `8094` / `8095` / `8088` | 每 10 分钟探测；状态变化或满 30 分钟心跳才提交 |
| 自有服务器 | 根用户 crontab 调用 `/opt/portfolio-probe.sh` | `http://127.0.0.1:8092` / `8093` / `8094` / `8095` / `8088` | 每 5 分钟，数据最新最准 |

> **注意**：GitHub 的 `schedule` 触发不可靠，免费 runner 上 `*/5` 实测会被拖到 2 小时一次。
> 所以别把 Pages 上的状态当成实时信号——要准就看 8090；改了代码推上来时 `push` 事件也会立刻触发一次探测。

端口含义：8093 运营助手（服务器常驻）、8092 智能客服隧道、8095 RAG 知识库隧道、8094 问数隧道、8088 Octop。
8092 / 8094 / 8095 是 SSH 反向隧道，**本机或隧道进程不在时自动判为「按需启动」**，属预期行为。

## 截图资源

`screenshots/` 下的文件按项目前缀命名，改图时按前缀替换即可（WebP，宽 1440）：

| 前缀 | 对应项目 |
| --- | --- |
| `ops-1..2.webp` | 01 AI 电商运营助手（原图 2、3 重复，暂用 2 张） |
| `cs-1..3.webp` | 02 智能客服系统 |
| `rag-1..3.webp` | 03 企业智能知识库 |
| `nl2sql-1..3.webp` | 04 数据问数 · NL2SQL |

> 05 Octop 数据仓库插件暂无截图，页面用占位块展示。

## 页面展示的项目

| # | 项目 | 技术要点 | 源码 / 演示入口 |
| --- | --- | --- | --- |
| 01 | AI 电商运营助手 | FastAPI · Celery · LangGraph · Redis · PostgreSQL · Next.js | [源码](https://github.com/ljl3133892273-png/ecommerce-operation-assistant) · [演示 8093](http://81.70.85.14:8093/) |
| 02 | 智能客服系统 | FastAPI · LangChain · SQLAlchemy · MySQL · Pydantic | [源码](https://github.com/ljl3133892273-png/customer-service-backend) · [演示 8092](http://81.70.85.14:8092/) |
| 03 | 企业智能知识库 | FastAPI · LangGraph · Milvus · MongoDB · MinIO · BGE | [源码](https://github.com/ljl3133892273-png/knowledge_base) · [演示 8095](http://81.70.85.14:8095/) |
| 04 | 数据问数 · NL2SQL | FastAPI · LangGraph · Qdrant · Elasticsearch · MySQL · TEI/BGE | [源码](https://github.com/ljl3133892273-png/data-agent) · [演示 8094](http://81.70.85.14:8094/) |
| 05 | Octop 数据仓库插件 | Octop 平台二开 · Plugin SDK · Docker · SQLite | [演示 8088](http://81.70.85.14:8088/) |

> 01 运营助手与 05 Octop 常驻服务器，其余三个走本地 Docker + SSH 反向隧道，需要演示时联系我开启。

## 其他公开仓库

| 项目 | 说明 | 仓库 |
| --- | --- | --- |
| 合同智能审批 | 合同草拟—审查—审批—回写全流程：文档解析、条款审查、模板推荐、报告生成 | [contract_approval](https://github.com/ljl3133892273-png/contract_approval) |

## 本地预览

页面不依赖任何服务端能力，直接双击 `index.html` 用浏览器打开即可。或起一个静态服务：

```bash
python -m http.server 8090
```

然后访问 http://localhost:8090

## 部署

- **GitHub Pages**：仓库 `Settings → Pages`，Source 选择 `Deploy from a branch`，分支 `main`、目录 `/(root)`。
  访问地址：https://ljl3133892273-png.github.io/portfolio/
- **自有服务器**：`index.html` 与 `screenshots/` 一起覆盖到 nginx 静态目录（`/opt/portfolio`），无需重启容器。

```bash
scp index.html ubuntu@81.70.85.14:/opt/portfolio/index.html
scp -r screenshots ubuntu@81.70.85.14:/opt/portfolio/
```

## 更新流程

1. 改 `index.html`（样式 / 文案）或按前缀替换 `screenshots/` 里的图（新图先转成 WebP、宽 1440）。
2. 本地 `git add` → `commit` → `push`，GitHub Pages 约 1 分钟自动生效。
3. 再按上面两条 `scp` 同步到自有服务器（http://81.70.85.14:8090 ）。

```bash
git add index.html README.md screenshots
git commit -m "update: 描述本次修改"
git push
```

> 仓库里的 `.github/workflows/probe-demos.yml` 每 5 分钟探测各演示服务端口并回写 `status.json`，
> 新版页面暂未读取该文件（旧版用它显示在线状态），数据保留备用。
