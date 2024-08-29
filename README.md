# cloudflare-docker-proxy

![deploy](https://github.com/ciiiii/cloudflare-docker-proxy/actions/workflows/deploy.yaml/badge.svg)

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/ciiiii/cloudflare-docker-proxy)

> 如果您正在寻找 docker 的代理，也许您可​​以尝试cloudflare-helm-proxy。 [cloudflare-helm-proxy](https://github.com/ciiiii/cloudflare-helm-proxy).

## 部署

1. 点击“使用 Workers 部署”按钮
2. 按照说明进行分叉和部署
3. 根据需要更新路线

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/ciiiii/cloudflare-docker-proxy)

## 路线配置教程

1. 使用 cloudflare worker host：仅支持代理一个注册表
   ```javascript
   const routes = {
     "${workername}.${username}.workers.dev/": "https://registry-1.docker.io",
   };
   ```
2. 使用自定义域名：支持通过主机代理多个注册中心路由
   - 在 cloudflare 上托管您的域名 DNS
   - 'A'将xxx.example.com 的记录添加到'192.0.2.1'
   - 将该项目部署到cloudflare worker
   - 添加'xxx.example.com/*'到工作者的HTTP路由
   - 根据需要添加更多记录并修改配置
   ```javascript
   const routes = {
     "docker.libcuda.so": "https://registry-1.docker.io",
     "quay.libcuda.so": "https://quay.io",
     "gcr.libcuda.so": "https://k8s.gcr.io",
     "k8s-gcr.libcuda.so": "https://k8s.gcr.io",
     "ghcr.libcuda.so": "https://ghcr.io",
   };
   ```

