# 作品集 · 刘家良

AI 应用开发 / FDE 方向个人作品集站点。

纯静态单文件页面：无框架、无构建步骤、无外部依赖，所有样式与脚本均内联在 `index.html` 中。

**在线地址：** https://ljl3133892273-png.github.io/portfolio/

## 页面结构

| 区块 | 内容 |
| --- | --- |
| 关于我 | 大模型应用工程、完整工程能力、交付与部署意识 |
| 技术栈 | 大模型应用 / 后端工程 / 数据与中间件 / 前端 / 部署运维 |
| 项目作品 | 数据问数 · NL2SQL、企业智能知识库、智能客服系统、AI 电商运营助手、Octop 数据仓库插件 |
| 联系方式 | 项目演示请求入口 |

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
- **自有服务器**：将 `index.html` 覆盖到 nginx 静态目录即可，无需重启容器。

## 更新流程

> `index.html` 是生成产物，不要直接手改。内容定义在生成脚本的 `SITE` / `PROJECTS` 数据块中，
> 改完重新运行脚本产出 `index.html`，再同步到本仓库与服务器。

```bash
git add -A
git commit -m "update: 描述本次修改"
git push
```

推送后 GitHub Pages 会自动重新构建，约 1 分钟生效。
