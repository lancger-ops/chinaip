本项目解析中国的IP，通过合并大段的ip，通过极少的路由完成大范围的中国IP覆盖。

一般来说，使用不到800条路由可以覆盖中国97%的IP，比直接使用4000+条原生少了很多。
即使是要完全覆盖，也可以节省大约1000条路由。
考虑到中国的服务提供商大多使用大范围的IP段，小范围的分给宽带用户，经过实测，使用16。

Mac OS X用户可以直接使用下面命令，下载处理好的文件，放到/etc/wireguard下(执行前请先停用VPN)。

```bash
mkdir -p /etc/wireguard
cd /etc/wireguard
curl -L -O "https://github.com/lancger-ops/chinaip/raw/master/mac/{ip-up,ip-down}"
chmod +x ip-up ip-down
```

手动添加路由--注意需要切换到管理员用户

```bash
cd /etc/wireguard
sh ip-up
sh ip-down
```

查看路由
```bash
MacBook-Pro:wireguard root# netstat -nr
Routing tables

Internet:
Destination        Gateway            Flags           Netif Expire
default            link#18            UCSg            utun3
default            192.168.31.1       UGScIg            en0
1                  link#18            UCS             utun3
2                  link#18            UCS             utun3
3                  link#18            UCS             utun3
3.209.103.60       link#18            UHWIi           utun3
4/6                link#18            UCS             utun3
8/7                link#18            UCS             utun3
8.8.4.4/32         link#18            UCS             utun3
8.8.8.8/32         link#18            UCS             utun3
8.8.8.8            link#18            UHWIi           utun3
10.8/24            10.8.0.2           UGSc            utun3
10.8.0.2           10.8.0.2           UH              utun3
10.9/16            192.168.31.1       UGSc              en0
11                 link#18            UCS             utun3
12/6               link#18            UCS             utun3
```
