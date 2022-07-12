### lnmp运行环境使用说明

docker compose的方式启动的php程序运行环境，采用'nginx'+'php74-fpm'+'mariadb'三个容器分离的方式执行环境。

## 修改env文件

```
mv example.env .env
vi .env
```

设定docker-compose文件；
修改数据库相关设定后“：wq”保存

## 写入nginx配置

```
vi services/nginx/app.conf
```
设定网站目录后，":wq"保存

## 数据库

# 设置数据库密码
mariadb的root用户采用随机密码启动容器，需要查看root密码，请在容器启动后，查看启动日志

用户数据库密码采用'secrets'文件导入

```
touch .DBsecrets
vi .DBsecrets
```

编写完数据库密码后，':wq'保存

数据库名，数据库用户，默认采用'panel' . 若想要修改或使用特定的用户名和数据库名，参考'composeFile'文件中数据库密码的导入方式

# 导入数据库文件

```
mkdir /services/sql
```

将相关数据库文件例如,'.sql','.sh','.sql.gz','.sql.xz','.sql.zst',文件放入'sql'文件夹；

## 启动环境

```
docker-compose up -d
```

### 本地开发环境

## 本地文件同步
本地开发环境采用[docker-sync](https://docker-sync.readthedocs.io/en/latest/)启动文件同步

[docker-sync](https://docker-sync.readthedocs.io/en/latest/)需配置部分本地服务，详情访问[docker-sync](https://docker-sync.readthedocs.io/en/latest/)

## 调整php运行环境

```
vi services/php/Dockerfile
```

参考[php](https://hub.docker.com/_/php)官方镜像说明,调整配置