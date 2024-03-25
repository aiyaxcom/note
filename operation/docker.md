安装 Docker：

1.  更新 apt 软件包索引：`sudo apt update`
2.  通过 apt 安装以下软件包，以允许 apt 通过 HTTPS 使用 Docker 仓库：`sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common`
3.  添加 Docker 的 GPG 密钥：`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
4.  添加 Docker 的 apt 仓库：`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
5.  再次更新 apt 软件包索引：`sudo apt update`
6.  安装 Docker：`sudo apt install docker-ce docker-ce-cli containerd.io`
7.  如果要让特权用户（非root）可以运行 Docker，则需要将该用户添加到 docker 组：`sudo usermod -aG docker your_username`
8.  通过运行 `docker run hello-world` 确认 Docker 安装成功。

```
#!/bin/bash

# 更新 apt 软件包索引
sudo apt update

# 安装必需的软件包
yes | sudo apt install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common

# 添加 Docker 的 GPG 密钥
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# 添加 Docker 的 apt 仓库
yes | sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# 再次更新 apt 软件包索引
sudo apt update

# 安装 Docker
yes | sudo apt install -y docker-ce docker-ce-cli containerd.io

# 如果要让特权用户（非root）可以运行 Docker，则需要将该用户添加到 docker 组
# 请将 "your_username" 替换为您的用户名
sudo usermod -aG docker your_username

# 通过运行 docker run hello-world 确认 Docker 安装成功
docker run hello-world

```

安装 Docker Compose：

1.  安装 Python pip：`sudo apt install python3-pip`
2.  安装 Docker Compose：`sudo pip install docker-compose`，如果报错可以尝试    `sudo apt-get install docker-compose`
3.  通过运行 `docker-compose --version` 确认 Docker Compose 安装成功。

--------------------

Docker 提供了 `docker prune` 命令来帮助清理不再使用的对象，包括容器（containers）、镜像（images）、网络（networks）和卷（volumes）。下面是一些常用的 `docker prune` 命令及其作用：

1. **清理停止的容器**:
   ```bash
   docker container prune
   ```
   运行此命令后，Docker 会询问你是否要删除所有停止的容器。确认后，所有停止的容器将被删除。

2. **清理悬空镜像**:
   ```bash
   docker image prune
   ```
   悬空镜像指的是那些不再有任何标签指向的镜像。这个命令会删除所有未被标记的镜像。

3. **清理全部无用镜像** (不仅仅是悬空镜像):
   ```bash
   docker image prune -a
   ```
   通过添加 `-a` 或 `--all` 参数，你可以删除所有无用的镜像，包括那些没有容器引用的镜像。

4. **清理无用的网络**:
   ```bash
   docker network prune
   ```
   这个命令会删除所有没有被容器使用的网络。

5. **清理无用的卷**:
   ```bash
   docker volume prune
   ```
   这个命令会删除所有没有被容器使用的卷。

6. **一次性清理所有无用资源**:
   ```bash
   docker system prune
   ```
   这个命令会同时清理无用的容器、网络和悬空镜像。

7. **清理所有无用资源，包括无用的卷**:
   ```bash
   docker system prune --volumes
   ```
   通过添加 `--volumes` 参数，你可以在清理无用的容器、网络和悬空镜像的同时，清理所有没有被容器引用的卷。

**注意**：使用 `prune` 命令时请谨慎，因为被删除的对象将无法恢复。此外，一些命令可以配合 `-f` 或 `--force` 参数来跳过确认步骤，实现无提示的删除。
