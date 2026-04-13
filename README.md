# CodeG - AI 编程助手会话聚合器

一站式聚合浏览 AI 编程助手会话（Claude Code、Codex、Gemini CLI 等）。

**支持部署方式**：桌面应用、自托管服务器、Docker、LazyCat Cloud

## 原始 Docker 命令

```bash
docker run -d -p 3080:3080 \
  -v codeg-data:/data \
  -v /path/to/projects:/projects \
  -e CODEG_TOKEN=your-secret-token \
  ghcr.io/xintaofei/codeg:latest
```

## 转换要点

| Docker | LazyCat |
|--------|---------|
| `-p 3080:3080` | `upstreams` (HTTP服务) |
| `-v codeg-data:/data` | `/lzcapp/var/data:/data` |
| `-v /path/to/projects:/projects` | `/lzcapp/documents:/projects` + 文档权限 |
| `-e CODEG_TOKEN=xxx` | 用户配置参数 `{{.U.codeg_token}}` |

## 部署步骤

1. 安装 lzc-cli（需要 v2.0.0+）：
   ```bash
   npm install -g @lazycatcloud/lzc-cli@2.0.0
   ```

2. 部署应用：
   ```bash
   lzc-cli project deploy
   ```

3. 配置 CODEG_TOKEN：
   - 在应用配置界面输入你的 CodeG 令牌

## 文件结构

```
.
├── package.yml            # 静态元数据
├── lzc-manifest.yml       # 运行结构定义
├── lzc-build.yml          # 构建配置
├── lzc-deploy-params.yml  # 部署参数配置
└── README.md              # 说明文档
```

## 发布到应用商店

```bash
# 构建发布包
lzc-cli project release -o codeg.lpk

# 发布到商店
lzc-cli appstore publish codeg.lpk
```# codeg-lzcapp
