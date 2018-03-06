# docker_moerun



## Realese

[v1.0.0](https://github.com/yyxndd/docker_moerun/releases)



### tomcat7.0.85镜像:

`docker pull moeee/tomcat:v7.0.85`

### tomcat9.0.5镜像:

`docker pull moeee/tomcat:v9.0.5`

## 使用说明：

### 准备：

1. pull自己需要使用的镜像下来

2. 在[github](https://github.com/yyxndd/docker_moerun)下载启动脚本

3. 自己的项目.war

4. 自己配置好的nginx

### 使用：

1. 在宿主机任意位置创建项目的文件夹，将***项目.war***放在该目录下，目录名和***项目.war***设置一样的名字，例如创建`/home/projectA`，war文件就应该在`/home/projectA/projectA.war`

2. 在该目录下创建***必需***的目录和***需要***的目录。必须创建的有`webapps`、`logs`、`temp`、`work`目录，其他的根据自己需要创建，因为该目录会成为容器的挂载目录，方便在宿主机上查看。

3. 使用启动脚本，./moerun -n 容器名字 -p nginx代理的端口 -d 一开始创建的目录，即宿主机挂载的目录 -v 使用的moeee/tomcat版本，例如`./moerun -n project -p 8086 -d /home/projectA -v 9.0.5`

### 说明：

1. 容器中tomcat启动的方式是设置`CATALINA_BASE`，容器内设置的路径为`/mnt/${项目名}`，挂载在宿主机的-d参数目录下;

2. 启动脚本只需要使用一次，后面可以通过docker start/stop控制容器启动，war包也只需要替换原来宿主挂载目录下的war包重启容器即可



