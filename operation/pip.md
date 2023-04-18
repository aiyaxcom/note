更新镜像源

## 镜像源
- 官方 https://pypi.org/simple/
- 阿里云 http://mirrors.aliyun.com/pypi/simple/

## 如何更新

### 临时更新
您可以使用以下命令来临时切换 PyPI 镜像源：

phpCopy code

`pip install <package-name> -i <mirror-url>`

其中，`<package-name>` 为要安装的包名，`<mirror-url>` 为 PyPI 镜像源的 URL。例如，如果您要使用清华大学的镜像源来安装 `beautifulsoup4`，可以使用以下命令：

`pip install beautifulsoup4 -i https://pypi.tuna.tsinghua.edu.cn/simple/`

### 永久更新
如果您想要永久更改 PyPI 镜像源，可以在 `pip.conf` 配置文件中进行配置。该文件通常位于以下位置：

-   Unix/Linux/macOS 系统：`$HOME/.config/pip/pip.conf`
-   Windows 系统：`%APPDATA%\pip\pip.ini`

在该文件中，您可以添加以下配置内容来指定默认的 PyPI 镜像源：

```
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple/
```

其中，`index-url` 指定了默认的 PyPI 镜像源 URL，您可以将其设置为您需要使用的任何镜像源的 URL。