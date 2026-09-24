# Docker Quickstart Templates

开箱即用的 Docker 配置文件模板，覆盖常见技术栈，帮助你快速容器化应用。

## 目录结构

```
docker-quickstart/
├── nginx/          # Nginx 反向代理 / 静态网站
├── nodejs/         # Node.js 应用
└── python/         # Python (Flask/FastAPI) 应用
```

## 快速开始

### Nginx

```bash
cd nginx
docker build -t my-nginx .
docker run -p 8080:80 my-nginx
```

### Node.js

```bash
cd nodejs
docker build -t my-node-app .
docker run -p 3000:3000 my-node-app
```

### Python

```bash
cd python
docker build -t my-python-app .
docker run -p 8000:8000 my-python-app
```

## Nginx 模板

基础配置文件，包含：
- `nginx.conf` — 完整生产级配置（worker_connections、gzip、缓存等）
- 默认 `upstream backend` 指向 `backend:3000`，可直接用于 Node.js 反向代理

## Node.js 模板

- 基于 `node:18-alpine`，镜像体积小
- 使用多阶段 COPY 优化构建缓存
- 生产模式 `--production` 安装依赖

## Python 模板

- 基于 `python:3.11-slim`
- `requirements.txt` 预装依赖
- 适合 Flask、FastAPI 等框架

## 扩展

根据需要修改 `Dockerfile` 和配置文件，例如：

```dockerfile
# 添加环境变量
ENV NODE_ENV=production

# 挂载数据卷
VOLUME ["/app/data"]
```

## License

Apache-2.0
