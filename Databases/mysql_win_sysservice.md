## 简要准备和说明
1. 下载版本：mysql-8.0.13-winx64，解压目录定为_MYSQL_HOME.
2. 本文适用于简单的个人使用和本地开发
3. 环境为win10pro-64bit-cn

## 安装服务操作过程
### 先期准备
1. 服务配置文件my.ini  
 + 因为本人习惯把数据放在单独的硬盘，需要制定mysql的指定目录。那么如果要进行服务参数配置，可以通过一个个参数在命令行执行，也可以通过指定配置文件完成。
 + MySQL的配置文件必须是安装目录_MYSQL_HOME下的my.ini文件。放到其他目录，服务安装是可以，但是启动并不识别。
 + 配置内容初始很简单：
```properties
[mysqld]
basedir=_MYSQL_HOME\mysql-8.0.13-winx64
datadir=_DATA_HOME\MySQLData
```

### 服务安装脚本实录

```shell
#进入目标盘
F:
cd _HOME\bin
# 如果前面install安装失败，存在服务，用这个命令删除
mysqld --remove
# 通过指定配置文件的方式安装服务
# -insecure 子参数指定不生成root密码，密码留空， --console参数指示在控制台打印消息
mysqld  --defaults-file=_MYSQL_HOME\my.ini --initialize-insecure --console
# 配置成功之后，会在数据目录生成数据库文件等。接下来注册服务
mysqld --install
# 启动服务. 如果启动失败，还没找到日志该在哪里看，欢迎补充。
net start mysql
# 登陆验证服务
mysql -u root
> mysql
show databases;
```
