## YApi  可视化接口管理平台

体验地址：

[https://yapi.baidu.com](https://yapi.baidu.com)

文档：
<p><a target="_blank" href="https://hellosean1025.github.io/yapi">hellosean1025.github.io/yapi</a></p>


### 特性
*  基于 Json5 和 Mockjs 定义接口返回数据的结构和文档，效率提升多倍
*  扁平化权限设计，即保证了大型企业级项目的管理，又保证了易用性
*  类似 postman 的接口调试
*  自动化测试, 支持对 Response 断言
*  MockServer 除支持普通的随机 mock 外，还增加了 Mock 期望功能，根据设置的请求过滤规则，返回期望数据
*  支持 postman, har, swagger 数据导入
*  免费开源，内网部署，信息再也不怕泄露了


### 安装
下面以`/www/wwwroot/yapi` 项目目录 为示例

```
mkdir /www/wwwroot/yapi
cd /www/wwwroot/yapi
git clone https://github.com/iofun/yapi.git vendors
cp vendors/config/config.json ./config.json
cd vendors
npm install --production
npm run install-server
```
### 启动服务器
```
node server/app.js
```

安装程序会初始化数据库索引和管理员账号，管理员账号名可在 config.json 配置

默认密码为`123456`

### 服务管理
利用pm2方便服务管理维护。
```
npm install pm2 -g  //安装pm2
cd  {项目目录}
pm2 start "vendors/server/app.js" --name yapi //pm2管理yapi服务
pm2 info yapi //查看服务信息
pm2 stop yapi //停止服务
pm2 restart yapi //重启服务
```

### 开机自启动
centos
```
pm2 save
pm2 startup
systemctl enable pm2-root
```

### 升级
升级项目版本是非常容易的，并且不会影响已有的项目数据，只会同步 vendors 目录下的源码文件。

cd {项目目录}

下面以`/www/wwwroot/yapi` 为示例
```
cd /www/wwwroot/yapi
rm -rf ./vendors
git clone https://github.com/iofun/yapi.git vendors
cd vendors
npm install --production
```
### 教程
* [使用 YApi 管理 API 文档，测试， mock](https://juejin.im/post/5acc879f6fb9a028c42e8822)
* [自动更新 Swagger 接口数据到 YApi 平台](https://juejin.im/post/5af500e251882567096140dd)
* [自动化测试](https://juejin.im/post/5a388892f265da430e4f4681)

### YApi 插件
* [yapi sso 登录插件](https://github.com/YMFE/yapi-plugin-qsso)
* [yapi cas 登录插件](https://github.com/wsfe/yapi-plugin-cas) By wsfe
* [yapi gitlab集成插件](https://github.com/cyj0122/yapi-plugin-gitlab)
* [oauth2.0登录](https://github.com/xwxsee2014/yapi-plugin-oauth2)
* [rap平台数据导入](https://github.com/wxxcarl/yapi-plugin-import-rap)
* [dingding](https://github.com/zgs225/yapi-plugin-dding) 钉钉机器人推送插件
* [export-docx-data](https://github.com/inceptiongt/Yapi-plugin-export-docx-data) 数据导出docx文档
* [interface-oauth-token](https://github.com/shouldnotappearcalm/yapi-plugin-interface-oauth2-token) 定时自动获取鉴权token的插件
* [import-swagger-customize](https://github.com/follow-my-heart/yapi-plugin-import-swagger-customize) 导入指定swagger接口

### 代码生成
* [yapi-to-typescript：根据 YApi 的接口定义生成 TypeScript 的请求函数](https://github.com/fjc0k/yapi-to-typescript)
* [yapi-gen-js-code: 根据 YApi 的接口定义生成 javascript 的请求函数](https://github.com/hellosean1025/yapi-gen-js-code)

### YApi docker部署（非官方）
* [使用 alpine 版 docker 镜像快速部署 yapi](https://www.jianshu.com/p/a97d2efb23c5)
* [docker-yapi: 基于官方yapi-cli的docker-compose方案](https://github.com/Ryan-Miao/docker-yapi)
* [docker-compose一键部署yapi](https://github.com/jinfeijie/yapi)
* [docker-YApi: 更易用的 YApi 镜像](https://github.com/fjc0k/docker-YApi)
* [使用DockerCompose构建部署Yapi](https://github.com/MyHerux/daily-code/blob/master/Program/%E5%B7%A5%E5%85%B7%E7%AF%87/Yapi/%E4%BD%BF%E7%94%A8DockerCompose%E6%9E%84%E5%BB%BA%E9%83%A8%E7%BD%B2Yapi.md)

### YApi 一些工具
* [Api Generator](https://github.com/Forgus/api-generator) 接口文档自动生成插件（零入侵）
* [mysql服务http工具,可配合做自动化测试](https://github.com/hellosean1025/http-mysql-server)
* [idea 一键上传接口到yapi插件](https://github.com/diwand/YapiIdeaUploadPlugin)
* [idea 接口上传调试插件 easy-yapi](https://easyyapi.com/)
* [执行 postgres sql 的服务](https://github.com/shouldnotappearcalm/http-postgres-server)


### Authors
* [hellosean1025](https://github.com/hellosean1025)
* [gaoxiaomumu](https://github.com/gaoxiaomumu)
* [zwjamnsss](https://github.com/amnsss)
* [dwb1994](https://github.com/dwb1994)
* [fungezi](https://github.com/fungezi)


### License
Apache License 2.0

