使用方法：
1
2
3
wget --no-check-certificate https://github.com/kuoruan/shell-scripts/raw/master/kcptun/kcptun.sh
chmod +x ./kcptun.sh
./kcptun.sh
1.设置 Kcptun 的服务端端口：
1
2
请输入 Kcptun Server 端口 [1-65535]:
(默认: 29900):
请输入一个未被占用的端口，Kcptun 运行时将使用此端口。
2.设置加速的 IP：
1
2
请输入需要加速的地址:
(默认: 127.0.0.1):
填入上面获取到的加速 IP。如果你想使用 IPv6，请直接填写 IPv6 地址，不需要加 []，脚本会自动添加。
3.设置需要加速的端口：
1
2
请输入需要加速的端口 [1-65535]:
(默认: 12948):
填入上面获取到的加速端口。
程序会检查当前是不是有程序占用着此端口，如果你的 Shadowsocks 没在运行，或者没有软件使用此端口，会弹出如下提示：
1
当前没有软件使用此端口, 确定加速此端口?(y/n)
如果你确认 Shadowsocks 运行时会使用此端口，那么输入 “y” 回车即可。
4.设置 Kcptun 密码：
1
2
请输入 Kcptun 密码:
(如果不想使用密码请留空):
这就是说，你可以为 Kcptun 单独设置一个密码，防止被他人恶意使用。这个密码和 SS 的密码没有半毛钱关系，请不要把它们混淆了。
再提一句，Kcptun 和 Shadowsocks 没有任何关系，请不要脑补它们之间存在任何联系，Kcptun 你可以理解为一款网络加速软件，只不过它是通过将 TCP 协议转换为 UDP 协议，然后再通过大量的发送数据包，浪费了带宽以换取网速的提升。它能加速所有以 TCP 协议传输数据的软件，不单单是 Shadowsocks。只是大家都用来……你懂的
回到上面的密码设置问题，如果你这里选择直接回车，也就是代表你不自定义密码。但是 Kcptun 有一个默认的密码，这个密码是：  it's a secrect 。
5.禁用压缩
1
2
是否禁用数据压缩?
(默认: 不禁用) [y/n]:
Kcptun 默认是启用压缩的。如果你这里设置为 y，也就是配置为 nocomp:true，那么就是禁用压缩。
许多朋友这里设置的是保持默认（启用压缩），而偏偏在软件之中设置为禁用压缩，当然就连不上咯。
其他配置项不用我说了，如果你了解它是干什么的，可以自定义配置。如果不知道，那么直接回车使用默认参数。
但是，使用默认参数，是有可能浪费大量流量的，你会发现你的流量像泄洪一样快速减少，你需要会调节参数，套用官方的说明
简易自我调优方法：
同时在两端逐步增大 client rcvwnd 和 server sndwnd ;
尝试下载，观察如果带宽利用率（服务器＋客户端两端都要观察）接近物理带宽则停止，否则跳转到第一步。
任何事物都是有两面性的，选择了速度，就只有放弃流量。那么有没有既快得像火箭，燃料又省得像煤油灯的方法呢？呵呵！
各参数详细信息请查看：https://github.com/xtaci/kcptun
如果你用国内服务器安装，可能会出现文件下载失败。这是由于脚本会到 Github 下载文件，而 Github 的某些下载地址在国内你懂的……所以文件下载失败真不是我的锅。
如果安装成功，应该能看到如下输出信

恭喜, Kcptun 服务端配置完毕！
 
正在获取当前安装的 Kcptun 版本...
 
服务器IP:  10.10.10.10
端口:  29900
加速地址: 127.0.0.1:8388
密码: 123456
加密方式 Crypt:  salsa20
 
当前安装的 Kcptun 版本为: v20160922
 
推荐的客户端配置为: 
{
  "localaddr": ":8388",
  "remoteaddr": "10.10.10.10:29900",
  "key": "123456",
  "crypt": "salsa20",
  "mode": "fast",
  "mtu": 1350,
  "sndwnd": 1024,
  "rcvwnd": 1024,
  "datashard": 10,
  "parityshard": 3,
  "dscp": 0,
  "conn": 1,
  "autoexpire": 60,
  "nocomp": false
}
 
手机端参数可以使用：
  *******
 
其他参数请自行计算或设置, 详细信息可以查看: https://github.com/xtaci/kcptun
 
Kcptun 安装目录: /usr/share/kcptun
Kcptun 日志文件目录: /var/log/kcptun/

请将以上的提示信息复制保存下来，后面配置客户端会用到这些提示信息。
安装之后，Kcptun 服务交由 Supervisor 管理。
Supervisor 相关命令：
1
service supervisord {start|stop|restart|status}
Kcptun 相关命令：
1
supervisorctl {start|stop|restart|status} kcptun
Supervisor 启动的时候会同时启动 Kcptun，运行 kcptun 相关命令时先确保 Supervisor 已启动。
