# OFFLINE — Cloudflare Pages 上传包

将本目录中的 dist 文件夹整个上传到 GitHub 仓库根目录。
请保留 dist 这一层：仓库中必须能找到 dist/index.html 和 dist/_worker.js。
不要上传 ZIP 本身，也不要把压缩包外层文件夹一起上传。

Cloudflare Pages 设置：
- Production branch: main（以 GitHub 实际分支为准）
- Framework preset: None
- Build command: 留空
- Build output directory: dist
- Root directory: 默认
- Environment variables: 无需填写

本包包括当前前端、3D 房间、小游戏、两个原始测试视频，以及实时新闻/促销/攻略来源查询的 Pages Worker 适配。
实时资讯仍依赖第三方来源可用性，不保证所有请求成功，不使用旧数据兜底。
视频通过 /api/video/snaptic、/api/video/player 映射到同站文件，保留原生 Range 拖动播放能力。
两个 MP4 均小于 Pages 单文件 25 MiB 限制，也小于 GitHub 网页上传单文件 25 MiB 限制。

边界：此包未部署 Spring Boot 和 MySQL。账号注册、多人聊天、用户资料和后台持久化，仍需 Java 后端服务器。
预览接口 /api/core/status 明确返回 persistent:false，不会伪装成已接入数据库。
本包不包含管理员密码、数据库配置、Steam API Key 或 Sites 凭据。

首次发布后先验证 pages.dev 地址的页面、视频和实时 API，再添加 offline.new.tg 自定义域名。
在 Pages 添加域名后，按平台给出的实际 CNAME 修改 DNSHE。不要提前猜测解析值。
以后修改 dist 内的文件并提交到 main，Cloudflare 会自动触发更新。
