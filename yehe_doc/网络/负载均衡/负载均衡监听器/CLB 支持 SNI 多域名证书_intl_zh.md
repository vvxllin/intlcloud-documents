## 什么是 SNI
服务器名称指示（Server Name Indication，SNI）是用来改善服务器与客户端 SSL/TLS，主要解决一台服务器只能使用一个证书的问题，支持 SNI 表示服务器支持绑定多个证书。客户端使用 SNI，则需在与服务器建立 SSL/TLS 连接之前指定要连接的域名，服务器会根据这个域名返回一个合适的证书。

## 使用场景
腾讯云 CLB 的七层 HTTPS 监听器支持 SNI，即支持绑定多个证书，监听规则中的不同域名可使用不同证书。如在同一个 CLB 的`HTTPS:443`监听器中，`*.test.com`使用证书1，将来自该域名的请求转发至一组服务器上；`*.example.com`使用证书2，将来自该域名的请求转发至另一组服务器上。

## 前提条件
已 [购买负载均衡实例](https://buy.cloud.tencent.com/lb)。
> 传统型负载均衡不支持基于域名和 URL 的转发，因此传统型负载均衡不支持 SNI。

## 操作步骤
1. 创建 HTTPS 监听器时，开启 SNI。
![](https://main.qcloudimg.com/raw/eb6958c5f3772c3b55ab3a2a1e92d341.png)
2. 在该监听器中添加转发规则时，针对不同的域名配置不同的服务器证书，单击【下一步】，继续完成健康检查和会话保持的配置。
![](https://main.qcloudimg.com/raw/bf5150f1f263a133770f1ad5694f501c.png)
