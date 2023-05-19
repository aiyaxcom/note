安装 Docker：

1.  更新 apt 软件包索引：`sudo apt update`
2.  通过 apt 安装以下软件包，以允许 apt 通过 HTTPS 使用 Docker 仓库：`sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common`
3.  添加 Docker 的 GPG 密钥：`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
4.  添加 Docker 的 apt 仓库：`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
5.  再次更新 apt 软件包索引：`sudo apt update`
6.  安装 Docker：`sudo apt install docker-ce docker-ce-cli containerd.io`
7.  如果要让特权用户（非root）可以运行 Docker，则需要将该用户添加到 docker 组：`sudo usermod -aG docker your_username`
8.  通过运行 `docker run hello-world` 确认 Docker 安装成功。

安装 Docker Compose：

1.  安装 Python pip：`sudo apt install python3-pip`
2.  安装 Docker Compose：`sudo pip install docker-compose`
3.  通过运行 `docker-compose --version` 确认 Docker Compose 安装成功。