# zerotier-one

# 当前版本：1.6.2

代码来源（修改了安装版本和copy路径）：zerotier官网 > Download > Others > DOCKER,链接地址https://github.com/zerotier/ZeroTierOne/tree/master/ext/installfiles/linux/zerotier-containerized

## 确认内核是否有tun模块

[root@localhost ~]# modinfo tun

加载tun模块

[root@localhost ~]# modprobe tun

查看是否加载

[root@localhost ~]# lsmod | grep tun

## 运行：

docker run -d --restart restart --name zerotier-one --device /dev/net/tun --network host --cap-add NET_ADMIN --cap-add SYS_ADMIN -v $your_dir/zerotier-one:/var/lib/zerotier-one 33naisi/zerotier-one

## 加入网络:

docker exec zerotier-one zerotier-cli join $NETWORK-ID

## 离开网络

docker exec zerotier-one zerotier-cli leave $NETWORK-ID

## 查看网络连接状态：

docker exec -it zerotier-one zerotier-cli listnetworks
