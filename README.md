# cf-worker-cors-proxy
利用Cloudflare Worker进行API接口反代理并配置允许跨域，方便你在前端调用各种AI、MCP等接口

## 用途
在前端连接使用MCP服务的时候，发现MCP服务器只允许跨域传递指定的头（不包括`Authorization`）    
这就导致我无法自定义配置认证key，无法正常在前端直接连接使用MCP服务。    
所以弄了这个脚本做反代理，原来的在前端中连接MCP的逻辑无需修改，只需要在MCP服务地址前面加上部署好的脚本服务地址即可。

比如，原来的MCP服务器为：`https://mcp.deepwiki.com/mcp` （无法在前端跨域传递`Authorization`）
加上代理后，地址为：`https://proxy.com/https://mcp.deepwiki.com/mcp`，这样就可以传递`Authorization`以及其他自定义头信息了

## 部署
1. 前往`Cloudflare控制台`
2. 新建`Worker`，粘贴`worker.js`脚本，部署
3. 绑定域名，访问即可。

