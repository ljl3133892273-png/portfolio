# 作品集 · 刘家良

AI 应用开发 / FDE 方向个人作品集站点。

纯静态页面：无框架、无构建步骤，样式与脚本均内联在 `index.html` 中；项目截图放在 `screenshots/`，用相对路径引用。

**在线地址：** https://ljl3133892273-png.github.io/portfolio/

## 页面结构

| 区块 | 内容 |
| --- | --- |
| 首页 | 一句话定位 + 项目 / 技术栈统计 |
| 关于我 | 大模型应用工程、完整工程能力、交付与部署意识 |
| 项目作品 | 5 个项目，每个项目带 3 图轮播（左右按钮 / 圆点 / 触屏滑动） |
| 阅读与思考 | 论文与工程实践阅读清单 |
| 技术栈 | 大模型应用 / 后端工程 / 数据与中间件 / 前端 / 部署运维 |
| 联系方式 | 邮件与 GitHub 入口 |

## 截图资源

`screenshots/` 下的文件按项目前缀命名，改图时按前缀替换即可（WebP，宽 1440）：

| 前缀 | 对应项目 |
| --- | --- |
| `nl2sql-1..3.webp` | 01 数据问数 · NL2SQL |
| `rag-1..3.webp` | 02 企业智能知识库 |
| `cs-1..3.webp` | 03 智能客服系统 |
| `ops-1..2.webp` | 04 AI 电商运营助手 |

> 05 Octop 数据仓库插件暂无截图，页面用占位块展示。

## 页面展示的项目

| # | 项目 | 技术要点 | 源码 / 入口 |
| --- | --- | --- | --- |
| 01 | 数据问数 · NL2SQL | FastAPI · LangGraph · Qdrant · Elasticsearch · MySQL · TEI/BGE | [data-agent](https://github.com/ljl3133892273-png/data-agent) |
| 02 | 企业智能知识库 | FastAPI · LangGraph · Milvus · MongoDB · MinIO · BGE | [knowledge_base](https://github.com/ljl3133892273-png/knowledge_base) |
| 03 | 智能客服系统 | FastAPI · LangChain · SQLAlchemy · MySQL · Pydantic | [customer-service-backend](https://github.com/ljl3133892273-png/customer-service-backend) |
| 04 | AI 电商运营助手 | FastAPI · Celery · LangGraph · Redis · PostgreSQL · Next.js | [ecommerce-operation-assistant](https://github.com/ljl3133892273-png/ecommerce-operation-assistant) |
| 05 | Octop 数据仓库插件 | Octop 平台二开 · Plugin SDK · Docker · SQLite | [访问线上系统](http://81.70.85.14:8088/) |

> 前 4 个项目的演示服务按需启动（本地 Docker 环境），需要在线演示时联系我开启；
> Octop 插件已在自有服务器上长期运行，可直接点击访问。

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
