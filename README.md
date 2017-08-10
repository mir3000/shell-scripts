Kcptun 服务端安装脚本
GitHub 地址：https://github.com/kuoruan/shell-scripts
理论上脚本支持大部分 Linux 发行版（x86 和 x64）
注意： 新版改动较大，我只做过简单测试，不保证没有 BUG，请及时反馈。
新版的默认安装目录移动到了 /usr/local/kcptun 而不是 /usr/share/kcptun
脚本已更新到v19，请以前版本的朋友可以直接更新，请先切换到 kcptun.sh 文件目录下运行
1
./kcptun.sh update
更新日志：
修复了当 key 含有空格时，无法正常加载的问题。
用 Putty 下中文显示可能会出现乱码一片，请自行解决乱码问题；推荐使用 Xshell，手机上可以用 JuiceSSH，都是非常好用的 SSH 客户端。
使用脚本安装服务端

注意：在配置之前请确认一下你的加速地址，大部分不能加速都是由于加速地址配置错误。
鉴于大部分朋友是用来加速 Shadowsocks，下面以 Shadowsocks 为例，Shadowsocks 正确安装运行在当前服务器上。
首先找到你的 Shadowsocks 端口，比如我的 Shadowsocks 端口为 8388，然后在命令行输入以下命令：
1
netstat -nl | grep 8388
如果提示以上命令不存在，请输入：
1
ss -nl | grep 8388
注：将 8388 替换为你的 Shadowsocks 端口。
然后你会看到类似下面的输出（着重看显示为红色的部分）：
情况一：
1
2
tcp6       0      0     :::8388                 :::*                    LISTEN     
udp6       0      0     :::8388                 :::*
情况2：
1
2
tcp       0      0     127.0.0.1:8388                 :::*                    LISTEN     
udp       0      0     127.0.0.1:8388                 :::*
情况3：
1
2
tcp       0      0     0.0.0.0:8388                 :::*                    LISTEN     
udp       0      0     0.0.0.0:8388                 :::*
情况4（假如 10.10.10.10 是当前服务器IP）：
1
2
tcp       0      0     10.10.10.10:8388                 :::*                    LISTEN     
udp       0      0     10.10.10.10:8388                 :::*
若为情况1、情况2和情况3，那么你的加速地址可以为：加速 IP 127.0.0.1，加速端口 8388（你的 Shadowsocks 端口）
若为情况4，那么你的加速地址为：加速IP 10.10.10.10（你的服务器IP），加速端口8388（你的 Shadowsocks 端口）
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
如果安装成功，应该能看到如下输出信息：

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
手动配置的方法请看这里：小内存福音，Kcptun Shadowsocks加速方案
客户端配置

1.先到下载一个启动 Kcptun 的工具。请注意，这只是用来启动 Kcptun 的工具，而不是 Kcptun 客户端。
https://github.com/dfdragon/kcptun_gclient/releases
2.然后下载服务端对应版本的 Kcptun（保存下来的提示信息里有）：
1
当前安装的 Kcptun 版本为: v20160922
https://github.com/xtaci/kcptun/releases
32位系统下载：kcptun-windows-386-20160922.tar.gz
64位系统下载：kcptun-windows-amd64-20160922.tar.gz
注意看红字的版本号和服务端版本一致。然后将它们解压到一起：

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
新建一个记事本文件，文件名随意（比如 config.txt 或者 config.json），然后将上面大括号里的内容复制到文件里边（包括大括号），确保它是标准的 json 格式（可以到这里校验格式  http://www.json.cn/）。
然后勾选“使用配置文件”，选择你新建的文件即可，下面的参数区域直接留空，点击启动。
2.手动配置参数
手动配置的时候只需要看保存下来的提示信息上面一部分（有标红部分，非常显眼）：

服务器IP:  10.10.10.10
端口:  29900
加速地址: 127.0.0.1:8388
加密方式 Crypt:  salsa20
为了规避错误，遵循较少配置原则，在配置服务端时没有修改过的选项都不需要配置。配置完毕，点击启动。
几项说明：
本地监听端口，这个端口你可以随意设置，不是必须设置为 Shadowsocsk 的端口；
KCP服务器地址为你的服务器IP地址，不是 127.0.0.1，端口为服务端 Kcptun 的端口；
如果你想使用IPv6协议，在填写服务器IP地址的时候需要用 [] 将IPv6地址括起来，如：[2000:0:0:0:0:0:0:1]；
通信密钥是你配置的 Kcptun 密码，不是 Shadowsocks 的密码；在配置 Kcptun 的时候，不用管 Shadowsocks 的配置参数；
参数区配置的时候，只需要配置你修改过的部分就行了，其他部分都不用改，除非你了解每项参数的意义；
日志区非常重要，在排查问题的时候，这是必看部分；
右下角为 Kcptun 最低需求版本，更新服务端之后，也需要更新本地客户端，只需要替换客户端文件即可。
Shadowsocks 配置

在 Shadowsocks 客户端中添加一个选项，服务器IP固定填写 127.0.0.1，服务器端口填写 Kcptun 启动工具中配置的“本地监听端口”（即这里的 8388），密码和加密配置的是 Shadowsocks 的密码和加密。
基本原则，配置 Kcptun 的时候不用管 Shadowsocks 的参数，配置 Shadowsocks 的时候不用管 Kcptun 的参数，别把它们的配置参数搞混了。
将代理切换到新建的选项上，尝试访问。查看 Kcptun 启动工具中的日志区，会有大量的如下信息输出：

2016/09/24 11:57:15 stream closed
2016/09/24 11:57:15 stream opened
2016/09/24 11:57:17 stream closed
2016/09/24 11:57:17 stream closed
2016/09/24 11:57:18 stream closed
2016/09/24 11:57:19 stream opened
2016/09/24 11:57:19 stream closed
再用 shelll 看看服务端日志，如果有相同的信息输出，说明配置正确，并能正常使用。查看服务端日志使用：
1
./kcptun.sh log
Android 端请看这里：Shadowsocks-Android客户端上的KCP配置说明
OpenWrt 上使用：OpenWrt平台Kcptun Web管理界面
关于安装错误

很多朋友发邮件告诉我说出现了安装错误
1.第一种错误日志如下：

Traceback (most recent call last):
  File "/usr/bin/easy_install", line 5, in <module>
    from pkg_resources import load_entry_point
  File "build/bdist.linux-x86_64/egg/pkg_resources.py", line 2565, in <module>
  File "build/bdist.linux-x86_64/egg/pkg_resources.py", line 519, in resolve
pkg_resources.DistributionNotFound: distribute==0.6.10
而但凡出现这种错误的都是出于某种目的，自己升级了 python 版本，但是又没处理好，那么只需要手动做一个软链接：

ln -s /usr/local/python2.7/bin/easy_install /usr/bin/easy_install
注：其中的 /usr/local/python2.7 应该为你安装的新版 python 的路径。
其他说明

请使用: kcptun.sh <option>
可使用的参数 <option> 包括:
    install          安装
    uninstall        卸载
    update           检查更新
    manual           自定义 Kcptun 版本安装
    help             查看脚本使用说明
    add              添加一个实例, 多用户使用
    reconfig <id>    重新配置实例
    show <id>        显示实例详细配置
    log <id>         显示实例日志
注: 上述参数中的 <id> 可选, 代表的是实例的序号
    可使用 1, 2, 3 ... 分别对应 kcptun, kcptun2, kcptun3 ...
    若不指定 <id>, 则默认为 1
Supervisor 命令:
    service supervisord {start|stop|restart|status}
                        {启动|关闭|重启|查看状态}
Kcptun 相关命令:
    supervisorctl {start|stop|restart|status} kcptun<id>
                  {启动|关闭|重启|查看状态}
