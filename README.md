# 作品集 · 刘家良

AI 应用开发 / FDE 方向个人作品集站点。

纯静态单文件页面：无框架、无构建步骤、无外部依赖，所有样式与脚本均内联在 `index.html` 中。

## 页面结构

| 区块 | 内容 |
| --- | --- |
| 关于我 | 大模型应用工程、完整工程能力、交付与部署意识 |
| 技术栈 | 大模型应用 / 后端工程 / 数据与中间件 / 前端 / 部署运维 |
| 项目作品 | 数据问数 · NL2SQL、企业智能知识库、多智能体深度搜索、智能客服系统、AI 电商运营助手、Octop 数据仓库插件 |
| 联系方式 | 项目演示请求入口 |

## 关联仓库

| 项目 | 仓库 |
| --- | --- |
| 数据问数 · NL2SQL | [zhengshi-data-agent](https://github.com/ljl3133892273-png/zhengshi-data-agent) |
| 企业智能知识库 | [zhengshi-knowledge-base](https://github.com/ljl3133892273-png/zhengshi-knowledge-base) |
| 多智能体深度搜索 | [zhengshi-agent-matrix](https://github.com/ljl3133892273-png/zhengshi-agent-matrix) |
| 智能客服系统 | [zhengshi-customer-service](https://github.com/ljl3133892273-png/zhengshi-customer-service) |
| AI 电商运营助手 | [zhengshi-operation-assistant](https://github.com/ljl3133892273-png/zhengshi-operation-assistant) |

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

```bash
git add -A
git commit -m "update: 描述本次修改"
git push
```

推送后 GitHub Pages 会自动重新构建，约 1 分钟生效。
