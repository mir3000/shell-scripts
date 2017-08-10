
    <article class="entry-content">
<p>Kcptun 服务端安装脚本</p>
<p>GitHub 地址：<a href="https://github.com/kuoruan/shell-scripts" target="_blank" rel="external nofollow">https://github.com/kuoruan/shell-scripts</a></p>
<p>理论上脚本支持大部分 Linux 发行版（x86 和 x64）</p>
<p><span style="color: #ff0000;">注意：</span> 新版改动较大，我只做过简单测试，不保证没有 BUG，请及时反馈。</p>
<p>新版的默认安装目录移动到了 /usr/local/kcptun 而不是 /usr/share/kcptun</p>
<p>脚本已更新到v19，请以前版本的朋友可以直接更新，请先切换到 kcptun.sh 文件目录下运行</p>
		<div id="crayon-598c6d1549e88722759425" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549e88722759425-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549e88722759425-1"><span class="crayon-sy">.</span><span class="crayon-o">/</span><span class="crayon-v">kcptun</span><span class="crayon-e">.sh</span><span class="crayon-h"> </span><span class="crayon-v">update</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>更新日志：</p>
<p>修复了当 key 含有空格时，无法正常加载的问题。</p>
<p>用 Putty 下中文显示可能会出现乱码一片，请自行解决乱码问题；推荐使用 Xshell，手机上可以用 JuiceSSH，都是非常好用的 SSH 客户端。</p>
<h2>使用脚本安装服务端</h2>
<p><span style="color: #ff0000;">注意：在配置之前请确认一下你的加速地址，大部分不能加速都是由于加速地址配置错误。</span></p>
<p>鉴于大部分朋友是用来加速 Shadowsocks，下面以 Shadowsocks 为例，Shadowsocks 正确安装运行在当前服务器上。</p>
<p>首先找到你的 Shadowsocks 端口，比如我的 Shadowsocks 端口为 8388，然后在命令行输入以下命令：</p>
		<div id="crayon-598c6d1549e91804665784" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549e91804665784-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549e91804665784-1"><span class="crayon-v">netstat</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-v">nl</span><span class="crayon-h"> </span><span class="crayon-o">|</span><span class="crayon-h"> </span><span class="crayon-i">grep</span><span class="crayon-h"> </span><span class="crayon-cn">8388</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>如果提示以上命令不存在，请输入：</p>
		<div id="crayon-598c6d1549e94553754735" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549e94553754735-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549e94553754735-1"><span class="crayon-v">ss</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-v">nl</span><span class="crayon-h"> </span><span class="crayon-o">|</span><span class="crayon-h"> </span><span class="crayon-i">grep</span><span class="crayon-h"> </span><span class="crayon-cn">8388</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p><span style="color: #ff0000;">注</span>：将 8388 替换为<span style="color: #ff0000;">你的 Shadowsocks 端口</span>。</p>
<p>然后你会看到类似下面的输出（着重看显示为红色的部分）：</p>
<hr />
<p>情况一：</p>
		<div id="crayon-598c6d1549e97299807969" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549e97299807969-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549e97299807969-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549e97299807969-1"><span class="crayon-i">tcp6</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e">LISTEN&nbsp;&nbsp;&nbsp;&nbsp; </span></div><div class="crayon-line" id="crayon-598c6d1549e97299807969-2"><span class="crayon-i">udp6</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>情况2：</p>
		<div id="crayon-598c6d1549e9a386274932" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549e9a386274932-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549e9a386274932-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549e9a386274932-1"><span class="crayon-i">tcp</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">127.0.0.1</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e">LISTEN&nbsp;&nbsp;&nbsp;&nbsp; </span></div><div class="crayon-line" id="crayon-598c6d1549e9a386274932-2"><span class="crayon-i">udp</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">127.0.0.1</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>情况3：</p>
		<div id="crayon-598c6d1549e9d143833708" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549e9d143833708-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549e9d143833708-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549e9d143833708-1"><span class="crayon-i">tcp</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0.0.0.0</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e">LISTEN&nbsp;&nbsp;&nbsp;&nbsp; </span></div><div class="crayon-line" id="crayon-598c6d1549e9d143833708-2"><span class="crayon-i">udp</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0.0.0.0</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>情况4（假如 10.10.10.10 是当前服务器IP）：</p>
		<div id="crayon-598c6d1549e9f109810356" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549e9f109810356-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549e9f109810356-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549e9f109810356-1"><span class="crayon-i">tcp</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">10.10.10.10</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e">LISTEN&nbsp;&nbsp;&nbsp;&nbsp; </span></div><div class="crayon-line" id="crayon-598c6d1549e9f109810356-2"><span class="crayon-i">udp</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-cn">0</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-cn">10.10.10.10</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span class="crayon-o">::</span><span class="crayon-o">:</span><span class="crayon-o">*</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p></p>
<hr />
<p>若为情况1、情况2和情况3，那么你的加速地址可以为：加速 IP 127.0.0.1，加速端口 8388（<span style="color: #ff0000;">你的 Shadowsocks 端口</span>）</p>
<p>若为情况4，那么你的加速地址为：加速IP 10.10.10.10（<span style="color: #ff0000;">你的服务器IP</span>），加速端口8388（<span style="color: #ff0000;">你的 Shadowsocks 端口</span>）</p>
<p>使用方法：</p>
		<div id="crayon-598c6d1549ea2181660843" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ea2181660843-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ea2181660843-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549ea2181660843-3">3</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ea2181660843-1"><span class="crayon-v">wget</span><span class="crayon-h"> </span><span class="crayon-o">--</span><span class="crayon-v">no</span><span class="crayon-o">-</span><span class="crayon-v">check</span><span class="crayon-o">-</span><span class="crayon-e">certificate </span><span class="crayon-v">https</span><span class="crayon-o">:</span><span class="crayon-o">/</span><span class="crayon-o">/</span><span class="crayon-v">github</span><span class="crayon-e">.com</span><span class="crayon-o">/</span><span class="crayon-v">kuoruan</span><span class="crayon-o">/</span><span class="crayon-v">shell</span><span class="crayon-o">-</span><span class="crayon-v">scripts</span><span class="crayon-o">/</span><span class="crayon-v">raw</span><span class="crayon-o">/</span><span class="crayon-v">master</span><span class="crayon-o">/</span><span class="crayon-v">kcptun</span><span class="crayon-o">/</span><span class="crayon-v">kcptun</span><span class="crayon-e">.sh</span></div><div class="crayon-line" id="crayon-598c6d1549ea2181660843-2"><span class="crayon-r">chmod</span><span class="crayon-h"> </span><span class="crayon-o">+</span><span class="crayon-i">x</span><span class="crayon-h"> </span><span class="crayon-sy">.</span><span class="crayon-o">/</span><span class="crayon-v">kcptun</span><span class="crayon-e">.sh</span></div><div class="crayon-line" id="crayon-598c6d1549ea2181660843-3"><span class="crayon-sy">.</span><span class="crayon-o">/</span><span class="crayon-v">kcptun</span><span class="crayon-e">.sh</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>1.设置 Kcptun 的服务端端口：</p>
		<div id="crayon-598c6d1549ea5223893887" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ea5223893887-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ea5223893887-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ea5223893887-1">请输入<span class="crayon-h"> </span><span class="crayon-e">Kcptun </span><span class="crayon-i">Server</span><span class="crayon-h"> </span>端口<span class="crayon-h"> </span><span class="crayon-sy">[</span><span class="crayon-cn">1</span><span class="crayon-o">-</span><span class="crayon-cn">65535</span><span class="crayon-sy">]</span><span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549ea5223893887-2"><span class="crayon-sy">(</span>默认<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">29900</span><span class="crayon-sy">)</span><span class="crayon-o">:</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>请输入一个未被占用的端口，Kcptun 运行时将使用此端口。</p>
<p>2.设置加速的 IP：</p>
		<div id="crayon-598c6d1549ea7495882972" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ea7495882972-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ea7495882972-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ea7495882972-1">请输入需要加速的地址<span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549ea7495882972-2"><span class="crayon-sy">(</span>默认<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">127.0.0.1</span><span class="crayon-sy">)</span><span class="crayon-o">:</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>填入上面获取到的<span style="color: #ff0000;">加速 IP</span>。如果你想使用 IPv6，请直接填写 IPv6 地址，不需要加 []，脚本会自动添加。</p>
<p>3.设置需要加速的端口：</p>
		<div id="crayon-598c6d1549eaa993088373" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549eaa993088373-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549eaa993088373-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549eaa993088373-1">请输入需要加速的端口<span class="crayon-h"> </span><span class="crayon-sy">[</span><span class="crayon-cn">1</span><span class="crayon-o">-</span><span class="crayon-cn">65535</span><span class="crayon-sy">]</span><span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549eaa993088373-2"><span class="crayon-sy">(</span>默认<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">12948</span><span class="crayon-sy">)</span><span class="crayon-o">:</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>填入上面获取到的<span style="color: #ff0000;">加速端口</span>。</p>
<p>程序会检查当前是不是有程序占用着此端口，如果你的 Shadowsocks 没在运行，或者没有软件使用此端口，会弹出如下提示：</p>
		<div id="crayon-598c6d1549ead709833582" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ead709833582-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ead709833582-1">当前没有软件使用此端口<span class="crayon-sy">,</span><span class="crayon-h"> </span>确定加速此端口<span class="crayon-sy">?</span><span class="crayon-sy">(</span><span class="crayon-v">y</span><span class="crayon-o">/</span><span class="crayon-v">n</span><span class="crayon-sy">)</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>如果你确认 Shadowsocks 运行时会使用此端口，那么输入 “y” 回车即可。</p>
<p>4.设置 Kcptun 密码：</p>
		<div id="crayon-598c6d1549eaf202559392" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549eaf202559392-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549eaf202559392-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549eaf202559392-1">请输入<span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>密码<span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549eaf202559392-2"><span class="crayon-sy">(</span>如果不想使用密码请留空<span class="crayon-sy">)</span><span class="crayon-o">:</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>这就是说，你可以为 Kcptun 单独设置一个密码，防止被他人恶意使用。这个密码和 SS 的密码没有半毛钱关系，请不要把它们混淆了。</p>
<p>再提一句，<span style="color: #ff0000;">Kcptun 和 Shadowsocks 没有任何关系</span>，请不要脑补它们之间存在任何联系，Kcptun 你可以理解为一款网络加速软件，只不过它是通过将 TCP 协议转换为 UDP 协议，然后再通过大量的发送数据包，浪费了带宽以换取网速的提升。它能加速所有以 TCP 协议传输数据的软件，不单单是 Shadowsocks。只是大家都用来……你懂的</p>
<p>回到上面的密码设置问题，如果你这里选择直接回车，也就是代表你不自定义密码。但是 Kcptun 有一个默认的密码，这个密码是：
			<span id="crayon-598c6d1549eb2251080027" class="crayon-syntax crayon-syntax-inline crayon-syntax-inline-nowrap crayon-theme-github crayon-theme-github-inline crayon-font-consolas" style="font-size: 14px !important; line-height: 24px !important;font-size: 14px !important;"><span class="crayon-pre crayon-code" style="font-size: 14px !important; line-height: 24px !important;font-size: 14px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><span class="crayon-i">it</span>'<span class="crayon-i">s</span><span class="crayon-h"> </span><span class="crayon-i">a</span><span class="crayon-h"> </span><span class="crayon-v">secrect</span></span></span> 。</p>
<p>5.<span style="color: #ff0000;">禁用压缩</span></p>
		<div id="crayon-598c6d1549eb4910164243" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549eb4910164243-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549eb4910164243-2">2</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549eb4910164243-1">是否禁用数据压缩<span class="crayon-sy">?</span></div><div class="crayon-line" id="crayon-598c6d1549eb4910164243-2"><span class="crayon-sy">(</span>默认<span class="crayon-o">:</span><span class="crayon-h"> </span>不禁用<span class="crayon-sy">)</span><span class="crayon-h"> </span><span class="crayon-sy">[</span><span class="crayon-v">y</span><span class="crayon-o">/</span><span class="crayon-v">n</span><span class="crayon-sy">]</span><span class="crayon-o">:</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>Kcptun 默认是启用压缩的。如果你这里设置为 y，也就是配置为 nocomp:true，那么就是禁用压缩。</p>
<p>许多朋友这里设置的是保持默认（启用压缩），而偏偏在软件之中设置为禁用压缩，当然就连不上咯。</p>
<p>其他配置项不用我说了，如果你了解它是干什么的，可以自定义配置。<span style="color: #ff0000;">如果不知道，那么直接回车使用默认参数</span>。</p>
<p>但是，使用默认参数，是有可能浪费大量流量的，你会发现你的流量像泄洪一样快速减少，你需要会调节参数，套用官方的说明</p>
<p>简易自我调优方法：</p>
<ol>
<li>同时在两端逐步增大 client rcvwnd 和 server sndwnd ;</li>
<li>尝试下载，观察如果带宽利用率（服务器＋客户端两端都要观察）接近物理带宽则停止，否则跳转到第一步。</li>
</ol>
<p>任何事物都是有两面性的，选择了速度，就只有放弃流量。那么有没有既快得像火箭，燃料又省得像煤油灯的方法呢？呵呵！</p>
<p>各参数详细信息请查看：https://github.com/xtaci/kcptun</p>
<p>如果你用国内服务器安装，可能会出现文件下载失败。这是由于脚本会到 Github 下载文件，而 Github 的某些下载地址在国内你懂的……所以文件下载失败真不是我的锅。</p>
<p>如果安装成功，应该能看到如下输出信息：</p>
		<div id="crayon-598c6d1549eb7865286110" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-3">3</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-4">4</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-5">5</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-6">6</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-7">7</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-8">8</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-9">9</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-10">10</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-11">11</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-12">12</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-13">13</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-14">14</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-15">15</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-16">16</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-17">17</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-18">18</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-19">19</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-20">20</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-21">21</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-22">22</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-23">23</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-24">24</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-25">25</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-26">26</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-27">27</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-28">28</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-29">29</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-30">30</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-31">31</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-32">32</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-33">33</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-34">34</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-35">35</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-36">36</div><div class="crayon-num" data-line="crayon-598c6d1549eb7865286110-37">37</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549eb7865286110-1">恭喜<span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>服务端配置完毕！</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-2">&nbsp;</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-3">正在获取当前安装的<span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>版本<span class="crayon-sy">.</span><span class="crayon-sy">.</span><span class="crayon-sy">.</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-4">&nbsp;</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-5">服务器<span class="crayon-v">IP</span><span class="crayon-o">:</span><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-cn">10.10.10.10</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-6">端口<span class="crayon-o">:</span><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-cn">29900</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-7">加速地址<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">127.0.0.1</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-8">密码<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">123456</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-9">加密方式<span class="crayon-h"> </span><span class="crayon-v">Crypt</span><span class="crayon-o">:</span><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-i">salsa20</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-10">&nbsp;</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-11">当前安装的<span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>版本为<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-i">v20160922</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-12">&nbsp;</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-13">推荐的客户端配置为<span class="crayon-o">:</span><span class="crayon-h"> </span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-14"><span class="crayon-sy">{</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-15"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"localaddr"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">":8388"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-16"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"remoteaddr"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"10.10.10.10:29900"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-17"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"key"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"123456"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-18"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"crypt"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"salsa20"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-19"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"mode"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"fast"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-20"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"mtu"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1350</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-21"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"sndwnd"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1024</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-22"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"rcvwnd"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1024</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-23"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"datashard"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">10</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-24"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"parityshard"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">3</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-25"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"dscp"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">0</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-26"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"conn"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-27"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"autoexpire"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">60</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-28"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"nocomp"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-t">false</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-29"><span class="crayon-sy">}</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-30">&nbsp;</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-31">手机端参数可以使用：</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-32"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-o">*</span><span class="crayon-o">*</span><span class="crayon-o">*</span><span class="crayon-o">*</span><span class="crayon-o">*</span><span class="crayon-o">*</span><span class="crayon-o">*</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-33">&nbsp;</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-34">其他参数请自行计算或设置<span class="crayon-sy">,</span><span class="crayon-h"> </span>详细信息可以查看<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-v">https</span><span class="crayon-o">:</span><span class="crayon-c">//github.com/xtaci/kcptun</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-35">&nbsp;</div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-36"><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>安装目录<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-o">/</span><span class="crayon-v">usr</span><span class="crayon-o">/</span><span class="crayon-v">share</span><span class="crayon-o">/</span><span class="crayon-e">kcptun</span></div><div class="crayon-line" id="crayon-598c6d1549eb7865286110-37"><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>日志文件目录<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-o">/</span><span class="crayon-t">var</span><span class="crayon-o">/</span><span class="crayon-v">log</span><span class="crayon-o">/</span><span class="crayon-v">kcptun</span><span class="crayon-o">/</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>请将以上的提示信息复制保存下来，后面配置客户端会用到这些提示信息。</p>
<p>安装之后，Kcptun 服务交由 Supervisor 管理。</p>
<p>Supervisor 相关命令：</p>
		<div id="crayon-598c6d1549eba587528131" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549eba587528131-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549eba587528131-1"><span class="crayon-e">service</span><span class="crayon-h"> </span><span class="crayon-e">supervisord</span><span class="crayon-h"> </span><span class="crayon-sy">{</span><span class="crayon-v">start</span><span class="crayon-o">|</span><span class="crayon-v">stop</span><span class="crayon-o">|</span><span class="crayon-v">restart</span><span class="crayon-o">|</span><span class="crayon-v">status</span><span class="crayon-sy">}</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>Kcptun 相关命令：</p>
		<div id="crayon-598c6d1549ebc260701927" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ebc260701927-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ebc260701927-1"><span class="crayon-e">supervisorctl</span><span class="crayon-h"> </span><span class="crayon-sy">{</span><span class="crayon-v">start</span><span class="crayon-o">|</span><span class="crayon-v">stop</span><span class="crayon-o">|</span><span class="crayon-v">restart</span><span class="crayon-o">|</span><span class="crayon-v">status</span><span class="crayon-sy">}</span><span class="crayon-h"> </span><span class="crayon-v">kcptun</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>Supervisor 启动的时候会同时启动 Kcptun，运行 kcptun 相关命令时先确保 Supervisor 已启动。</p>
<p>手动配置的方法请看这里：<a href="https://blog.kuoruan.com/102.html" target="_blank">小内存福音，Kcptun Shadowsocks加速方案</a></p>
<h2>客户端配置</h2>
<p>1.先到下载一个启动 Kcptun 的工具。请注意，这只是用来启动 Kcptun 的工具，而不是 Kcptun 客户端。</p>
<p><a href="https://github.com/dfdragon/kcptun_gclient/releases" target="_blank" rel="external nofollow">https://github.com/dfdragon/kcptun_gclient/releases</a></p>
<p>2.然后下载<span style="color: #ff0000;">服务端对应版本</span>的 Kcptun（保存下来的提示信息里有）：</p>
		<div id="crayon-598c6d1549ebf037001796" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ebf037001796-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ebf037001796-1">当前安装的<span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>版本为<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-v">v20160922</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p><a href="https://github.com/xtaci/kcptun/releases" target="_blank" rel="external nofollow">https://github.com/xtaci/kcptun/releases</a></p>
<p>32位系统下载：kcptun-windows-386-<span style="color: #ff0000;">20160922</span>.tar.gz</p>
<p>64位系统下载：kcptun-windows-amd64-<span style="color: #ff0000;">20160922</span>.tar.gz</p>
<p>注意看红字的版本号和服务端版本一致。然后将它们解压到一起：</p>
		<div id="crayon-598c6d1549ec2971857538" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ec2971857538-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ec2971857538-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549ec2971857538-3">3</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ec2971857538-1"><span class="crayon-v">kcptun_gclient</span><span class="crayon-sy">.</span><span class="crayon-v">exe</span><span class="crayon-h"> </span><span class="crayon-o">--</span><span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>启动工具</div><div class="crayon-line" id="crayon-598c6d1549ec2971857538-2"><span class="crayon-v">client_windows_amd64</span><span class="crayon-sy">.</span><span class="crayon-v">exe</span><span class="crayon-h"> </span><span class="crayon-o">--</span><span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>客户端程序</div><div class="crayon-line" id="crayon-598c6d1549ec2971857538-3"><span class="crayon-v">server_windows_amd64</span><span class="crayon-sy">.</span><span class="crayon-v">exe</span><span class="crayon-h"> </span><span class="crayon-o">--</span><span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>服务端程序</div></div></td>
					</tr>
				</table>
			</div>
		</div><p>打开 Kcptun 启动工具，界面如下，请按序号操作。</p>
<p><a href="https://blog.kuoruan.com/wp-content/uploads/2016/08/Kcptun_GUI_config.png" data-lightbox="image_lg" target="_blank"><img title="[v19]Kcptun 服务端一键安装脚本，支持输出新版手机端参数 - 第1张  | 扩软博客" alt="[v19]Kcptun 服务端一键安装脚本，支持输出新版手机端参数 - 第1张  | 扩软博客" class="alignnone size-medium wp-image-385" src="https://blog.kuoruan.com/wp-content/uploads/grey.gif" data-src="https://blog.kuoruan.com/wp-content/uploads/2016/08/Kcptun_GUI_config-550x330.png" width="550" height="330" /></a></p>
<p>1.直接导入配置文件</p>
<p>我们可以将推荐参数保存为文件，找到如下这部分：</p>
		<div id="crayon-598c6d1549ec4691985133" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-3">3</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-4">4</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-5">5</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-6">6</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-7">7</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-8">8</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-9">9</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-10">10</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-11">11</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-12">12</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-13">13</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-14">14</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-15">15</div><div class="crayon-num" data-line="crayon-598c6d1549ec4691985133-16">16</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ec4691985133-1"><span class="crayon-sy">{</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-2"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"localaddr"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">":8388"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-3"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"remoteaddr"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"10.10.10.10:29900"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-4"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"key"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"123456"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-5"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"crypt"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"salsa20"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-6"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"mode"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-s">"fast"</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-7"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"mtu"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1350</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-8"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"sndwnd"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1024</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-9"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"rcvwnd"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1024</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-10"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"datashard"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">10</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-11"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"parityshard"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">3</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-12"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"dscp"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">0</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-13"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"conn"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">1</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-14"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"autoexpire"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">60</span><span class="crayon-sy">,</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-15"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-s">"nocomp"</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-t">false</span></div><div class="crayon-line" id="crayon-598c6d1549ec4691985133-16"><span class="crayon-sy">}</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>新建一个记事本文件，文件名随意（比如 config.txt 或者 config.json），然后将上面大括号里的内容复制到文件里边（包括大括号），确保它是标准的 json 格式（可以到这里校验格式  <a href="http://www.json.cn/" target="_blank" rel="external nofollow">http://www.json.cn/</a>）。</p>
<p>然后勾选“使用配置文件”，选择你新建的文件即可，下面的<span style="color: #ff0000;">参数区域直接留空</span>，点击启动。</p>
<p>2.手动配置参数</p>
<p>手动配置的时候只需要看保存下来的提示信息上面一部分（有标红部分，非常显眼）：</p>
		<div id="crayon-598c6d1549ec7484701159" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ec7484701159-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ec7484701159-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549ec7484701159-3">3</div><div class="crayon-num" data-line="crayon-598c6d1549ec7484701159-4">4</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ec7484701159-1">服务器<span class="crayon-v">IP</span><span class="crayon-o">:</span><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-cn">10.10.10.10</span></div><div class="crayon-line" id="crayon-598c6d1549ec7484701159-2">端口<span class="crayon-o">:</span><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-cn">29900</span></div><div class="crayon-line" id="crayon-598c6d1549ec7484701159-3">加速地址<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-cn">127.0.0.1</span><span class="crayon-o">:</span><span class="crayon-cn">8388</span></div><div class="crayon-line" id="crayon-598c6d1549ec7484701159-4">加密方式<span class="crayon-h"> </span><span class="crayon-v">Crypt</span><span class="crayon-o">:</span><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-v">salsa20</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>为了规避错误，遵循较少配置原则，在配置服务端时没有修改过的选项都不需要配置。配置完毕，点击启动。</p>
<p>几项说明：</p>
<ol>
<li>本地监听端口，这个端口你可以<span style="color: #ff0000;">随意设置</span>，不是必须设置为 Shadowsocsk 的端口；</li>
<li>KCP服务器地址为<span style="color: #ff0000;">你的服务器IP地址</span>，不是 127.0.0.1，端口为<span style="color: #ff0000;">服务端 Kcptun 的端口</span>；</li>
<li>如果你想使用IPv6协议，在填写服务器IP地址的时候需要用 [] 将IPv6地址括起来，如：[2000:0:0:0:0:0:0:1]；</li>
<li>通信密钥是你配置的 Kcptun 密码，<span style="color: #ff0000;">不是 Shadowsocks 的密码</span>；在配置 Kcptun 的时候，不用管 Shadowsocks 的配置参数；</li>
<li>参数区配置的时候，<span style="color: #ff0000;">只需要配置你修改过的部分就行了</span>，其他部分都不用改，除非你了解每项参数的意义；</li>
<li>日志区<span style="color: #ff0000;">非常重要</span>，在排查问题的时候，这是必看部分；</li>
<li>右下角为 Kcptun 最低需求版本，更新服务端之后，也需要更新本地客户端，只需要替换客户端文件即可。</li>
</ol>
<h2>Shadowsocks 配置</h2>
<p>在 Shadowsocks 客户端中添加一个选项，服务器IP固定填写 127.0.0.1，服务器端口填写 Kcptun 启动工具中配置的“本地监听端口”（即这里的 8388），密码和加密配置的是 <span style="color: #ff0000;">Shadowsocks 的密码和加密</span>。</p>
<p>基本原则，配置 Kcptun 的时候不用管 Shadowsocks 的参数，配置 Shadowsocks 的时候不用管 Kcptun 的参数，别把它们的配置参数搞混了。</p>
<p>将代理切换到新建的选项上，尝试访问。查看 Kcptun 启动工具中的日志区，会有大量的如下信息输出：</p>
		<div id="crayon-598c6d1549eca708368040" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549eca708368040-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549eca708368040-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549eca708368040-3">3</div><div class="crayon-num" data-line="crayon-598c6d1549eca708368040-4">4</div><div class="crayon-num" data-line="crayon-598c6d1549eca708368040-5">5</div><div class="crayon-num" data-line="crayon-598c6d1549eca708368040-6">6</div><div class="crayon-num" data-line="crayon-598c6d1549eca708368040-7">7</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549eca708368040-1"><span class="crayon-cn">2016</span><span class="crayon-o">/</span><span class="crayon-cn">09</span><span class="crayon-o">/</span><span class="crayon-cn">24</span><span class="crayon-h"> </span><span class="crayon-cn">11</span><span class="crayon-o">:</span><span class="crayon-cn">57</span><span class="crayon-o">:</span><span class="crayon-cn">15</span><span class="crayon-h"> </span><span class="crayon-e">stream </span><span class="crayon-i">closed</span></div><div class="crayon-line" id="crayon-598c6d1549eca708368040-2"><span class="crayon-cn">2016</span><span class="crayon-o">/</span><span class="crayon-cn">09</span><span class="crayon-o">/</span><span class="crayon-cn">24</span><span class="crayon-h"> </span><span class="crayon-cn">11</span><span class="crayon-o">:</span><span class="crayon-cn">57</span><span class="crayon-o">:</span><span class="crayon-cn">15</span><span class="crayon-h"> </span><span class="crayon-e">stream </span><span class="crayon-i">opened</span></div><div class="crayon-line" id="crayon-598c6d1549eca708368040-3"><span class="crayon-cn">2016</span><span class="crayon-o">/</span><span class="crayon-cn">09</span><span class="crayon-o">/</span><span class="crayon-cn">24</span><span class="crayon-h"> </span><span class="crayon-cn">11</span><span class="crayon-o">:</span><span class="crayon-cn">57</span><span class="crayon-o">:</span><span class="crayon-cn">17</span><span class="crayon-h"> </span><span class="crayon-e">stream </span><span class="crayon-i">closed</span></div><div class="crayon-line" id="crayon-598c6d1549eca708368040-4"><span class="crayon-cn">2016</span><span class="crayon-o">/</span><span class="crayon-cn">09</span><span class="crayon-o">/</span><span class="crayon-cn">24</span><span class="crayon-h"> </span><span class="crayon-cn">11</span><span class="crayon-o">:</span><span class="crayon-cn">57</span><span class="crayon-o">:</span><span class="crayon-cn">17</span><span class="crayon-h"> </span><span class="crayon-e">stream </span><span class="crayon-i">closed</span></div><div class="crayon-line" id="crayon-598c6d1549eca708368040-5"><span class="crayon-cn">2016</span><span class="crayon-o">/</span><span class="crayon-cn">09</span><span class="crayon-o">/</span><span class="crayon-cn">24</span><span class="crayon-h"> </span><span class="crayon-cn">11</span><span class="crayon-o">:</span><span class="crayon-cn">57</span><span class="crayon-o">:</span><span class="crayon-cn">18</span><span class="crayon-h"> </span><span class="crayon-e">stream </span><span class="crayon-i">closed</span></div><div class="crayon-line" id="crayon-598c6d1549eca708368040-6"><span class="crayon-cn">2016</span><span class="crayon-o">/</span><span class="crayon-cn">09</span><span class="crayon-o">/</span><span class="crayon-cn">24</span><span class="crayon-h"> </span><span class="crayon-cn">11</span><span class="crayon-o">:</span><span class="crayon-cn">57</span><span class="crayon-o">:</span><span class="crayon-cn">19</span><span class="crayon-h"> </span><span class="crayon-e">stream </span><span class="crayon-i">opened</span></div><div class="crayon-line" id="crayon-598c6d1549eca708368040-7"><span class="crayon-cn">2016</span><span class="crayon-o">/</span><span class="crayon-cn">09</span><span class="crayon-o">/</span><span class="crayon-cn">24</span><span class="crayon-h"> </span><span class="crayon-cn">11</span><span class="crayon-o">:</span><span class="crayon-cn">57</span><span class="crayon-o">:</span><span class="crayon-cn">19</span><span class="crayon-h"> </span><span class="crayon-e">stream </span><span class="crayon-v">closed</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>再用 shelll 看看服务端日志，如果有相同的信息输出，说明配置正确，并能正常使用。查看服务端日志使用：</p>
		<div id="crayon-598c6d1549ecc503755550" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ecc503755550-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ecc503755550-1"><span class="crayon-sy">.</span><span class="crayon-o">/</span><span class="crayon-v">kcptun</span><span class="crayon-sy">.</span><span class="crayon-e">sh </span><span class="crayon-v">log</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>Android 端请看这里：<a href="https://blog.kuoruan.com/111.html" target="_blank">Shadowsocks-Android客户端上的KCP配置说明</a></p>
<p>OpenWrt 上使用：<a href="https://blog.kuoruan.com/113.html" target="_blank">OpenWrt平台Kcptun Web管理界面</a></p>
<h2>关于安装错误</h2>
<p>很多朋友发邮件告诉我说出现了安装错误</p>
<p>1.第一种错误日志如下：</p>
		<div id="crayon-598c6d1549ecf011056998" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ecf011056998-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ecf011056998-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549ecf011056998-3">3</div><div class="crayon-num" data-line="crayon-598c6d1549ecf011056998-4">4</div><div class="crayon-num" data-line="crayon-598c6d1549ecf011056998-5">5</div><div class="crayon-num" data-line="crayon-598c6d1549ecf011056998-6">6</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ecf011056998-1"><span class="crayon-e">Traceback</span><span class="crayon-h"> </span><span class="crayon-sy">(</span><span class="crayon-e">most </span><span class="crayon-e">recent </span><span class="crayon-e">call </span><span class="crayon-v">last</span><span class="crayon-sy">)</span><span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549ecf011056998-2"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-i">File</span><span class="crayon-h"> </span><span class="crayon-s">"/usr/bin/easy_install"</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-i">line</span><span class="crayon-h"> </span><span class="crayon-cn">5</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-st">in</span><span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">module</span><span class="crayon-o">&gt;</span></div><div class="crayon-line" id="crayon-598c6d1549ecf011056998-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e">from </span><span class="crayon-e">pkg_resources </span><span class="crayon-e">import </span><span class="crayon-e">load_entry_point</span></div><div class="crayon-line" id="crayon-598c6d1549ecf011056998-4"><span class="crayon-e">&nbsp;&nbsp;</span><span class="crayon-i">File</span><span class="crayon-h"> </span><span class="crayon-s">"build/bdist.linux-x86_64/egg/pkg_resources.py"</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-i">line</span><span class="crayon-h"> </span><span class="crayon-cn">2565</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-st">in</span><span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">module</span><span class="crayon-o">&gt;</span></div><div class="crayon-line" id="crayon-598c6d1549ecf011056998-5"><span class="crayon-h">&nbsp;&nbsp;</span><span class="crayon-i">File</span><span class="crayon-h"> </span><span class="crayon-s">"build/bdist.linux-x86_64/egg/pkg_resources.py"</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-i">line</span><span class="crayon-h"> </span><span class="crayon-cn">519</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-st">in</span><span class="crayon-h"> </span><span class="crayon-e">resolve</span></div><div class="crayon-line" id="crayon-598c6d1549ecf011056998-6"><span class="crayon-v">pkg_resources</span><span class="crayon-sy">.</span><span class="crayon-v">DistributionNotFound</span><span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-v">distribute</span><span class="crayon-o">==</span><span class="crayon-cn">0.6.10</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>而但凡出现这种错误的都是出于某种目的，自己升级了 python 版本，但是又没处理好，那么只需要手动做一个软链接：</p>
		<div id="crayon-598c6d1549ed2843928848" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ed2843928848-1">1</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ed2843928848-1"><span class="crayon-v">ln</span><span class="crayon-h"> </span><span class="crayon-o">-</span><span class="crayon-v">s</span><span class="crayon-h"> </span><span class="crayon-o">/</span><span class="crayon-v">usr</span><span class="crayon-o">/</span><span class="crayon-v">local</span><span class="crayon-o">/</span><span class="crayon-v">python2</span><span class="crayon-sy">.</span><span class="crayon-cn">7</span><span class="crayon-o">/</span><span class="crayon-v">bin</span><span class="crayon-o">/</span><span class="crayon-v">easy_install</span><span class="crayon-h"> </span><span class="crayon-o">/</span><span class="crayon-v">usr</span><span class="crayon-o">/</span><span class="crayon-v">bin</span><span class="crayon-o">/</span><span class="crayon-v">easy_install</span></div></div></td>
					</tr>
				</table>
			</div>
		</div><p>注：其中的 /usr/local/python2.7 应该为你安装的新版 python 的路径。</p>
<p>其他说明</p>
		<div id="crayon-598c6d1549ed4383333822" class="crayon-syntax crayon-theme-github crayon-font-consolas crayon-os-pc print-yes notranslate" data-settings=" no-popup minimize scroll-always disable-anim wrap" style=" margin-top: 12px; margin-bottom: 12px; font-size: 14px !important; line-height: 24px !important;">
		
			<div class="crayon-plain-wrap"></div>
			<div class="crayon-main" style="">
				<table class="crayon-table">
					<tr class="crayon-row">
				<td class="crayon-nums " data-settings="show">
					<div class="crayon-nums-content" style="font-size: 14px !important; line-height: 24px !important;"><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-1">1</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-2">2</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-3">3</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-4">4</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-5">5</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-6">6</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-7">7</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-8">8</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-9">9</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-10">10</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-11">11</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-12">12</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-13">13</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-14">14</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-15">15</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-16">16</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-17">17</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-18">18</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-19">19</div><div class="crayon-num" data-line="crayon-598c6d1549ed4383333822-20">20</div></div>
				</td>
						<td class="crayon-code"><div class="crayon-pre" style="font-size: 14px !important; line-height: 24px !important; -moz-tab-size:2; -o-tab-size:2; -webkit-tab-size:2; tab-size:2;"><div class="crayon-line" id="crayon-598c6d1549ed4383333822-1">请使用<span class="crayon-o">:</span><span class="crayon-h"> </span><span class="crayon-v">kcptun</span><span class="crayon-sy">.</span><span class="crayon-v">sh</span><span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">option</span><span class="crayon-o">&gt;</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-2">可使用的参数<span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">option</span><span class="crayon-o">&gt;</span><span class="crayon-h"> </span>包括<span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-3"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-i">install</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>安装</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-4"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-i">uninstall</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>卸载</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-5"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-i">update</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>检查更新</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-6"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-i">manual</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>自定义<span class="crayon-h"> </span><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>版本安装</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-7"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-i">help</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>查看脚本使用说明</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-8"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-i">add</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>添加一个实例<span class="crayon-sy">,</span><span class="crayon-h"> </span>多用户使用</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-9"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">reconfig</span><span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">id</span><span class="crayon-o">&gt;</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span>重新配置实例</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-10"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">show</span><span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">id</span><span class="crayon-o">&gt;</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>显示实例详细配置</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-11"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-v">log</span><span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">id</span><span class="crayon-o">&gt;</span><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>显示实例日志</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-12">注<span class="crayon-o">:</span><span class="crayon-h"> </span>上述参数中的<span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">id</span><span class="crayon-o">&gt;</span><span class="crayon-h"> </span>可选<span class="crayon-sy">,</span><span class="crayon-h"> </span>代表的是实例的序号</div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-13"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span>可使用<span class="crayon-h"> </span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">2</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-cn">3</span><span class="crayon-h"> </span><span class="crayon-sy">.</span><span class="crayon-sy">.</span><span class="crayon-sy">.</span><span class="crayon-h"> </span>分别对应<span class="crayon-h"> </span><span class="crayon-v">kcptun</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-v">kcptun2</span><span class="crayon-sy">,</span><span class="crayon-h"> </span><span class="crayon-i">kcptun3</span><span class="crayon-h"> </span><span class="crayon-sy">.</span><span class="crayon-sy">.</span><span class="crayon-sy">.</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-14"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span>若不指定<span class="crayon-h"> </span><span class="crayon-o">&lt;</span><span class="crayon-v">id</span><span class="crayon-o">&gt;</span><span class="crayon-sy">,</span><span class="crayon-h"> </span>则默认为<span class="crayon-h"> </span><span class="crayon-cn">1</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-15"><span class="crayon-i">Supervisor</span><span class="crayon-h"> </span>命令<span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-16"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e">service</span><span class="crayon-h"> </span><span class="crayon-e">supervisord</span><span class="crayon-h"> </span><span class="crayon-sy">{</span><span class="crayon-v">start</span><span class="crayon-o">|</span><span class="crayon-v">stop</span><span class="crayon-o">|</span><span class="crayon-v">restart</span><span class="crayon-o">|</span><span class="crayon-v">status</span><span class="crayon-sy">}</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-17"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-sy">{</span>启动<span class="crayon-o">|</span>关闭<span class="crayon-o">|</span>重启<span class="crayon-o">|</span>查看状态<span class="crayon-sy">}</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-18"><span class="crayon-i">Kcptun</span><span class="crayon-h"> </span>相关命令<span class="crayon-o">:</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-19"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-e">supervisorctl</span><span class="crayon-h"> </span><span class="crayon-sy">{</span><span class="crayon-v">start</span><span class="crayon-o">|</span><span class="crayon-v">stop</span><span class="crayon-o">|</span><span class="crayon-v">restart</span><span class="crayon-o">|</span><span class="crayon-v">status</span><span class="crayon-sy">}</span><span class="crayon-h"> </span><span class="crayon-e">kcptun</span><span class="crayon-o">&lt;</span><span class="crayon-e">id</span><span class="crayon-o">&gt;</span></div><div class="crayon-line" id="crayon-598c6d1549ed4383333822-20"><span class="crayon-h">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="crayon-sy">{</span>启动<span class="crayon-o">|</span>关闭<span class="crayon-o">|</span>重启<span class="crayon-o">|</span>查看状态<span class="crayon-sy">}</span></div></div></td>
					</tr>
				</table>
			</div>
