### 一、下载 Maven

从 `Maven` 官方地址：[http://maven.apache.org/download.cgi](http://maven.apache.org/download.cgi) 下载最新版本，如：`apache-maven-xxx-bin.tar.gz`。



### 二、配置环境变量 Maven 

首先将下载好的资源，解压之后，放到自己想放到的目录，如：`/Users/lyc/Desktop/D/de/maven/apache-maven-3.8.3`。



然后在终端通过命令 `open ~/.bash_profile` 打开文件（如不存在，则新建），添加如下信息。

```shell
# 添加 Maven 到环境变量
export M3_HOME=/Users/lyc/Desktop/D/de/maven/apache-maven-3.8.3
export PATH=$M3_HOME/bin:$PATH
```



最后通过通过命令 `source ~/.bash_profile` 使环境变量生效。



### 三、验证 Maven 安装是否成功

首先检查环境变量信息，通过命令 `echo $M3_HOME` ，输出类似信息。

```shell
/Users/lyc/Desktop/D/de/maven/apache-maven-3.8.3
```



然后通过命令 `mvn -version`，如果输出类似信息，代表安装成功。

```shell
Apache Maven 3.8.3 (ff8e977a158738155dc465c6a97ffaf31982d739)
Maven home: /Users/lyc/Desktop/D/de/maven/apache-maven-3.8.3
Java version: 1.8.0_251, vendor: Oracle Corporation, runtime: /Library/Java/JavaVirtualMachines/jdk1.8.0_251.jdk/Contents/Home/jre
Default locale: zh_CN, platform encoding: UTF-8
OS name: "mac os x", version: "10.16", arch: "x86_64", family: "mac"
```