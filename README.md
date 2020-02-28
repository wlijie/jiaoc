### 客户端模式
##### 下载连接: https://snapcraft.io/v2ray-core

 Linux利用上面的这个地方就可以完成客户端的下载和安装了,当然你也可以选择通过命令行安装 snap 命令,然后再用 snap 的命令去安装.

 这个办法我没试过,因为墙,所以不保证一定能行.

#### 命令行操作
先到这里 https://www.v2ray.com/download/ 下载 Core 包

解压, 配置好 config.json
进入解压目录,运行:
##### config.json
```
{
  "inbounds": [
    {
      "port": 1080,
      "listen": "127.0.0.1",
      "protocol": "socks",
      "sniffing": {
        "enabled": true,
        "destOverride": ["http", "tls"]
      },
      "settings": {
        "auth": "noauth",
        "udp": false
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "vmess",
      "settings": {
        "vnext": [
          {
            "address": "服务器线路地址",
            "port": 443,
            "users": [
              {
                "id": "分配您的UUID",
                "alterId": 10,
                "security": "auto",
                "level": 1
              }
            ]
          }
        ]
      },
      "streamSettings": {
        "network": "ws",
        "security": "tls",
        "wsSettings": {
          "path": "/index"
        }
      }
    }
  ]
}
```
```
$ ./v2ray

```
别试图用命令行执行 go.sh , 因为 GitHub 也是被墙了的.

浏览器插件安装
我用的是 chrome 浏览器,如果要翻墙就要设代理,最好是安装好那个 SwitchyOmega 插件,可是我的浏览器翻不了墙才需要装这个插件的,这就是没有鸡怎么生蛋的问题了,所以必须有办法安装上这个插件,一种办法是上网找别人提供的下载位置,还不能是Github的位置,这个有点难,还一个办法就是我要说的办法了.

通过命令让浏览器挂代理:

打开 cmd ,然后运行:
```
google-chrome-stable --proxy-server="socks5://127.0.0.1:1080"
```
这里的1080是端口,一般都是这个,根据你自己的代理客户端设置决定.

如果你用的不是 chrome 那就该下名字就好了.

这样打开的浏览器是过代理的,然后你再去下载插件安装插件即可.

至于配置,网上太多了,去搜吧.

5. 终端或其他应用翻墙
5.1 命令翻墙方法
别小看命令翻墙的方式,你可以通过命令行来启动程序从而达到被调用的程序实现翻墙哦!

命令行终端要翻墙我们一般是用 proxychains-ng 来翻墙,项目主页地址:https://github.com/rofl0r/proxychains-ng

本文日期时间的下载地址:http://ftp.barfooze.de/pub/sabotage/tarballs/proxychains-ng-4.13.tar.xz
```
$ sha512sum proxychains-ng-4.13.tar.xz 
686ad90d01f21afa161e35a6fc142a9c9e87c419113c0e54ae4c0ba748be917f34ab17b30a876b825bd4b3f32f15b0793ba8c79a5fafc3b106b3762572349757  proxychains-ng-4.13.tar.xz
```

关于安装和使用请看macos系统下的操作,其实基本都是类似的,我也是看压缩包里的README来学习使用的.



5.2 代理工具翻墙
推荐 SocksCap 目前还没被墙,可以下载.
sockscap64-homepage.jpg
实在下载不了了,可以联系我,我必须存一份存货啊.
