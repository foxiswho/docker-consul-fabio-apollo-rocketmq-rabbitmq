# docker-consul-fabio-apollo-rocketmq-rabbitmq
docker-consul-fabio-apollo-rocketmq-rabbitmq


# 环境说明
第一次 `docker-compose up`时候，
`apollo`容器是无法启动成功的，
需要你根据下面的步骤把 `scripts/sql`下的2个SQL文件导入到数据库中，
导入完成后，自动创建`ApolloPortalDB`，`ApolloConfigDB`库，这时候再启动 `apollo` 容器，即可成功



```shell
cd docker

docker-compose up

```


# mysql 数据库 默认用户名和密码

账号/密码：root/root

端口：3306


# apollo 分布式配置中心
如果要使用，请先 创建几个数据库 ，打开如下链接 创建数据库
```angular2html
https://github.com/ctripcorp/apollo/tree/master/scripts/sql
```

数据库库指导  https://github.com/ctripcorp/apollo/wiki/分布式部署指南#21-创建数据库

Apollo（阿波罗）是携程框架部门研发的分布式配置中心，能够集中化管理应用不同环境、不同集群的配置，配置修改后能够实时推送到应用端，并且具备规范的权限、流程治理等特性，适用于微服务配置管理场景。
```SHELL
https://github.com/ctripcorp/apollo
```
## apollo 账号和密码
账号/密码: apollo/admin

## apollo访问地址
默认端口:8070
```SHELL
http://localhost:8070
```

# rocketmq console 控制台
端口：8180

```SHELL
http://localhost:8180
```
## consul 管理中心
端口：8500

```SHELL
http://localhost:8500
```
## rocketmq No route info of this topic
原因 Broker禁止自动创建Topic，且用户没有通过手工方式创建Topic，请自行创建 topic

# 数据库管理
```SHELL
http://localhost:3300
```
参数填写说明
>`服务器`: mysql
>                 这里的mysql是容器虚拟host，你也可以填写IP地址
>`用户名`: admin
>`密码`: admin
>`数据库`: 可以为空

## FAQ 报错
SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client
解决：用其他数据库管理软件，到数据库命令行格式下，执行如下命令。创建新用户`admin`,使用新用户和密码登录即可成功

```SQL
CREATE USER 'admin'@'%' IDENTIFIED WITH mysql_native_password BY 'admin';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';
FLUSH PRIVILEGES;
```



