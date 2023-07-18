## Https证书
### 生成证书
sudo certbot --nginx -d aiyax.com
### Stop nginx server of certbox
nginx -s stop


### linux 命令行客户端

1. 从 [github](https://github.com/v2ray/v2ray-core/releases) 上下载 linux 版本
2. 从手机或电脑上导出一个配置, 保存成 [config.json](./v2ray/config.json)
3. `/data/devp/cli/v2ray/v4.31.0/v2ray --config=/data/devp/workspace/alex/wiki/wiki/gfw/v2ray/config.json`

## chatGPT 被封的解决办法

使用  `cloudflare-warp` 来解决, 具体执行的命令

[1.1.1.1 — The free app that makes your Internet faster. (cloudflarewarp.com)](https://cloudflarewarp.com/)

```bash
# 安装 cloudflare-warp
# [Cloudflare Package Repository (cloudflareclient.com)](https://pkg.cloudflareclient.com/install)
curl https://pkg.cloudflareclient.com/pubkey.gpg | sudo gpg --yes --dearmor --output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list
apt update
apt install cloudflare-warp -y

# 注册 cloudflare-warp, 不需要账号, 直接注册就行, 应该是按机器的信息注册的
warp-cli register
# 添加例外, 否则在 connect 之后会拦截所有的 ip (172 的没有被拦截, 如果忘了添加例外的话, 阿里云网站上 ssh 还可以进去)
warp-cli add-excluded-route 0.0.0.0/0
# 连接
warp-cli connect
# 测试 chatgpt 连接, 返回一堆 html 表示成功, 返回 http code 1020 表示失败
curl https://chat.openai.com/chat
```


参考
- 教程: [如何绕过ChatGPT针对服务器提供商的IP封禁 - Developer F (swiftflamel.com)](https://swiftflamel.com/2023/04/04/%E5%A6%82%E4%BD%95%E7%BB%95%E8%BF%87chatgpt%E9%92%88%E5%AF%B9%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%8F%90%E4%BE%9B%E5%95%86%E7%9A%84ip%E5%B0%81%E7%A6%81/)
- 官网: [1.1.1.1 — The free app that makes your Internet faster. (cloudflarewarp.com)](https://cloudflarewarp.com/)
    - 添加 ubuntu repository: [Cloudflare Package Repository (cloudflareclient.com)](https://pkg.cloudflareclient.com/install)