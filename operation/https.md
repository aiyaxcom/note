使用Let's Encrypt安装HTTPS证书的步骤如下：

1.  安装 Certbot 你需要安装 Certbot 工具来生成、设置和更新证书。可以使用以下命令在你的终端中安装 Certbot：
    
    Copy code
    
    ```
    sudo apt-get update
    apt install certbot python3-certbot-nginx
    ```
    
2.  获取证书 运行以下命令获取证书：
    
    Copy code
    
    ```
    sudo certbot --nginx -d test.aiyax.com
    ```
    
    在上面的命令中：
    
    -   `certonly` 表示 Certbot 只生成证书，而不安装它。
    -   `-d` 表示要为哪个域名生成证书。
    
    你需要将 `example.com` 替换为你的域名。
    
3.  安装证书 根据你的服务器软件，你需要使用不同的命令来安装证书。以下是一些示例命令：
    
    -   Apache：
    
    Copy code
    
    ```
    sudo apache2ctl configtest
    sudo systemctl reload apache2
    ```
    
    -   Nginx
    
    Copy code
    
    ```
    sudo nginx -t
    sudo systemctl reload nginx
    ```
    
    你需要将这些命令替换为你的服务器软件的相关命令。
    
4.  配置自动更新 Let's Encrypt 证书是 90 天有效期的，因此你需要配置自动更新证书以保持其有效性。 可以通过以下命令配置每 12 小时自动更新证书：
    
    Copy code
    
    ```
    sudo certbot renew --dry-run
    ```
    
    如果你收到了 "Congratulations, all renewals succeeded" 的消息，证明自动更新已配置成功。