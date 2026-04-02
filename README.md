# Astrionyx-deploy

`Astrionyx-deploy` 是 **Astrionyx 的公开发布部署仓库**。

它的职责不是承载业务源码，而是承载 **GitHub Actions 工作流与发布部署配置**，用于配合私有主仓库 `Astrionyx` 完成以下流程：

1. 从私有仓库接收触发请求
2. 拉取私有仓库指定提交的源码
3. 构建后端 API Docker 镜像
4. 推送镜像到 GHCR
5. 通过 SSH 部署到目标服务器

---

## 为什么单独存在这个仓库

这个仓库存在的主要原因是：

- 私有仓库的 Actions 免费时长数不够用
- 公开仓库不受 Actions 免费时长限制

因此当前方案是：

- **私有仓库 `Astrionyx`** 只负责轻量触发
- **公开仓库 `Astrionyx-deploy`** 负责 hosted build、镜像推送与部署

这样可以把长时间的构建过程放在公开仓库完成，同时保留私有仓库源码不公开。
