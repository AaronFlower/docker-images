# Centos As Dev

## From Scratch

基于 `centos:7` 来构建，并将 Centos 7 的源更新为 163 的源。

## EPEL, Extra Packages for Enterprise Linux

RHEL( Red Hat Enterprise Linux ) 以及它的衍生发行版 centos 使用的 rpm 源都是官方的。官方的源安全稳定，但是官方的 rpm 源也不够丰富，如 the_silver_searcher (Ag) 这个包官方上就没有。而自己编译又太麻烦了。好在有了 EPEL 帮我们解决了这个问题。

EPEL （Extra Packages for Enterprise Linux), EPEL是由 Fedora 社区打造，为 RHEL 及衍生发行版如 CentOS 等提供高质量软件包的项目。装上了 EPEL之后，就相当于添加了一个第三方源。

安装方法：

```
yum install -y epel-release
```

安装完成后，就相当于增加一个第三方源，很多方便的工具都可安装了。


## 安装 Ag

安装 Ag 前需要先安装 `epel-release` , 然后安装 `the_silver_searcher` 。

```
yum install the_silver_searcher
```

## 安装的工具

- epel-release
- cmake : 版本在 3.14 以上需要自己编译
- wget, curl, which, tar, sudo, ssh, rsync, gcc, gcc-c++, make, git, zsh
- vim : 支持 python3 需要自己编译
- ctags: yum install ctags-etags

## 安装 man

默认的 centos Docker 镜像有 `tsflags=nodocs` 这个配置，我需要把 `/etc/yum.conf` 中这个配置给删除或注释掉之后再安装.

```
sed -i '/tsflags=nodocs/d' /etc/yum.conf && yum install -y man-pages man-db man
```
## Build

```
$ docker build --rm -t centos-dev .
```


## Run

```
$ docker run -it --name my-centos-dev -v ~/code/github.com/AaronFlower/leetcode:/code centos-dev /bin/zsh

```
