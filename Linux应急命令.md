# Linux应急常见命令-更新....
更新Linux在应急常用命令及一些tips
## 被DDOS、CC攻击检测
```bash
netstat -an | grep TIME_WAIT  # 显示网络链接状态为TIME_WAIT状态
netstat -an | grep TIME_WAIT | wc -l  # 统计TIME_WAIT条数
```
## Linux应急流量检测工具
```
iftop:
http://www.ex-parrot.com/~pdw/iftop/
```
## 防火墙封堵指定端口请求
```bash
iptables -I INPUT -p tcp --dport 80 -j DROP # 以80端口为示例进行封堵，具体端口号需要通过以上工具iftop获取哪个对应端口流量最大来进行封堵。
```
## Linux修改内核进行防护CC或DDOS攻击
Centos修改文件:
```bash
/ect/syctl.conf
* 修改超时时间为30秒，某些情况可以进一步降低该值
net.ipv4.tcp_fin_timeout = 30
* 将keepalive的发送频率降低为20分钟一次
net.ipv4.tcp_keepalive_time = 1200
* 开启SYN Cookies，当SYN队列溢出时启用Cookies
net.ipv4.tcp_syncookies = 1
* 开启TIME-WAIT sockets重用功能
net.ipv4.tcp_tw_reuse = 1
* 开启TIME-WAIT sockets快速回收功能
net.ipv4.tcp_tw_recycle = 1
* 加大SYN队列
net.ipv4.tcp_max_syn_backlog = 8192
* 最大TIME_WAIT保持数，超过将全部清除
net.ipv4.tcp_max_tw_buckets = 5000
* 修改完后执行以下命令使其生效:
sysctl -p

```
![images](https://github.com/si1ent-le/code-study/blob/master/syctl.jpg)
## 统计ssh爆破失败统计IP数量
命令
```bash
awk '/Failed password/{h[$(NF-3)]++}END{for(pol in h) print pol,h[pol]}' secure  |sort -rnk2|head
````
![images](https://github.com/si1ent-le/code-study/blob/master/awk_ssh_brute.png)
