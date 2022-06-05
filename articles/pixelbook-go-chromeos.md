# 玩转 Pixelbook 之 ChromeOS
最近由于“极客精神”突然发作，在二手市场购买了一台 **Pixelbook Go** 来捣鼓，由于 **Pixelbook Go** 默认采用的是 ChromeOS，于是有了这一篇文章，帮助那些未来想要把工作、娱乐、学习转移到 ChromeOS 的同学踩踩坑。

## ChromeOS 简介
ChromeOS 是 Google 推出的一款轻量级操作系统，并且它是开源的，到现在为止已经有了12个年头（2010年下半年发布）。它的默认应用都是基于 Web 的应用，核心要素和 Chrome 浏览器如出一辙：速度、简洁、安全。

整个系统是基于 Linux 的，并且操作系统界面非常类似于 Chrome 浏览器，它为了能够丰富自己的生态，ChromeOS 不仅能够运行 Chrome Web 应用，而且能够运行 Android 应用和 Linux 应用，当然 Linux 应用相对来说需要的门槛会更高，只有少数开发人员才能够精通。

## 激活你的 ChromeOS
拿到新的 Chromebook 对国内用户来说，激活是一件有门槛的事情，需要大家有通过路由或者热点`搭梯子`的能力，这个细节自行搜索。激活是通过自己的 Google 账户来激活，Google账户的用户名和密码也将成为你的 Chromebook 的登录/锁屏账户。激活完了，如果日常软件都安装的差不多了，就可以把`梯子`撤掉了，日常工作、学习、娱乐浏览国内网站、应用基本可用。

* 打开 Chromebook，选择自己的语言；
* 网络选择有`梯子`能力的 wifi；
* 根据提示选择`下一步`或者填写相关账户信息；
* 等待系统初始化操作，很快系统就激活了；
* 最好将系统更新到最新版本：
  * 更新操作：设置->关于 Chrome 操作系统->检查是否有更新

## 设置你的 ChromeOS
为了能够让系统使用体验更方便，提前做好相应的设置，对日常工作效率将有极大的提升，这里总结了以下几个修改点：

* 启动器风格：
  * 如果是笔记本形态在使用 ChromeOS 建议开启，开启它所有应用将被收纳到一个类似于`Windows 系统的开始菜单`里。
  * 浏览器地址栏打开：chrome:flags#productivity-launcher，选择开启，重启电脑
* 任务栏日历显示：
  * 同样建议笔记本形态开启，你可以通过任务栏右侧日期显示区域点击出来。
  * 浏览器地址栏：chrome:flags#calendar-view，选择开启，重启电脑
* 文件回收站：
  * ChromeOS 默认情况下是不展示回收站的，开启这个功能让误删除的文件快速找回。
  * 浏览器地址栏：chrome:flag#files-trash，选择开启，重启电脑
* 网络代理设置：
* 合上屏幕，自动锁屏
* 触控板设置：调慢数度，反向滚动
* 查看机器状况：
  * 设置->关于 Chrome 操作系统->诊断

## 如何安装 Chrome 应用
Chrome 应用系统提供了两种方式安装：一种是通过`Chrome 网上应用商店`中选择自己喜爱的软件，点击安装；另一种也是通过开发者模式，直接安装 Chrome 安装包，这就不赘述了。

## 如何安装 Android 应用
同样也提供两种安装方式：
* 使用只带 Google Play 商店安装
  * 这种方式和安装 iOS App 一样，在应用商店中选择自己喜爱的软件，点击安装即可 
* 启用`ADB调试模式`直接按照`apk`后缀文件
  * 设置->开发者->Linux 开发环境->开发 Android->启用 ADB 调试
  * 右键选择安装包->选择`软件包安装程序`

## 如何安装 Linux 应用
ChromeOS 应用生态个人感觉一般，都是基于 Web 的应用，所以借助ChromeOS 内部的 Linux 容器，我们可以安装 Linux 应用，来弥补一些工作上的需求，例如开发者常用的：VSCode、Vim、Nodejs等工具，当然 Linux 生态中也不缺乏各种办公和娱乐软件。至少它对于我这样一个开发者来说是非常重要的。

### 启动 Linux
* 设置->开发者->Linux 开发环境->点击`开启`
* 选择相关设置，如果对 Linux 应用依赖大的同学可以将磁盘大小设置大一些，我设置的是20G，当然这个大小未来可以修改
* 等待下载和启动

这样一来，我们就可以使用熟悉的 Linux 命令行，开启工程师各种玩法。

### 如何安装
* 在 ChromeOS 环境下，下载安装包安装：右键选择安装包->选择`通过 Linux 安装`
* 在 Linux 环境下，通过命令行安装：`sudo apt-get install software-name`
  * 安装软件之前确保系统是最新的：`sudo apt update` `sudo apt upgrade`

### Linux 环境输入法安装
ChromeOS 提供的 Linux 容器，默认是没有中文输入法的，当然熟悉 Linux 的玩家知道 `Fcitx`一款输入法框架，为 Linux 系统提供一个灵活的输入方案：

* 修改默认语言编码
  * 在命令行中输入 `sudo dpkg-reconfigure locales`
  * 选择 `zh_CN.UTF8 UTF8` 和 `zh_CN.GBK GBK`
* 安装 Fcitx
  * `sudo apt install fcitx`
* 配置 Fcitx
  * 命令行：`im-config`
  * 选择：确定->点击Yes->选择fcitx->确定->确定
  * 重启 Linux 系统
* 安装谷歌拼音输入法
  * 命令行：`sudo apt install fcitx-googlepinyin`
* 添加输入法
  * 命令行：`fcitx-config-gtk3`
* 自动启动 Fcitx
  * 命令行：` sudo vim ~/.sommelierrc`
  * 添加一行信息：`/usr/bin/fcitx-autostart`
* 参考：
  * https://chamboin.github.io/2019/12/25/pixelbook-linux-locale/
  * https://noob.tw/chromeos-vscode/

### Linux 环境字体安装
字体安装通常需要去相关字体官网下载，解压放到字体文件夹后，刷新字体缓存即可：

* 下载字体
* 将字体文件解压到`usr/share/fonts`文件夹
* 刷新字体缓存`fc-cache -f -v`
* TODO：如何修改应用程序字体

推荐几个不错的字体：
* Noto Sans CJK SC
  * GoogleOS 默认字体，经过精心设计，推荐
  * 下载地址：https://fonts.google.com/noto/specimen/Noto+Sans+SC
* Noto Sans Mono CJK SC
  * Google 的等宽字体，对于开发者来说强力推荐
  * 建议安装了 VSCode 的将字体设置成该字体：Text Editor->Font Famliy: 'Noto Sans Mono CJK SC', 'Droid Sans Mono', 'monospace', monospace
    * VSCode 默认字体：'Droid Sans Mono', 'monospace', monospace
* JetBrains Mono
  * Jetbrains 设计的面向编程的等款字体
  * https://www.jetbrains.com/zh-cn/lp/mono/

## 推荐应用
通过 ChromeOS 的确可以做到办公娱乐，以下是我推荐的相关应用，每个应用都标明了不同的类型（Linux、Android、Chrome），Android 和 Chrome 应用直接根据名字到相应的市场上搜索就可以安装了；Linux 应用如果需要命令行操作，会注明相关命令行。

### 系统工具
* [Linux]Neoftech
  * `sudo apt install neofetch`
* [Android]Clash
* [Chrome]Cog-System Info Viewer
* [Linux]Software
  * `sudo apt-get install gnome-software gnome-packagekit`
  * `sudo apt update`
  * [可选项]`sudo apt dist-upgrade`

### 办公应用
* [Linux]VSCode
* [Linux]Typora
  * 下载地址：https://www.typora.io/#linux
  * `wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -`
  * `sudo add-apt-repository 'deb https://typora.io/linux ./'`
  * `sudo apt-get update`
  * `sudo apt-get install typora`
* [Linux]滴答清单
  * 下载地址：https://www.dida365.com/about/download

### 娱乐应用
* [Linux]Deepin-Wechat，借助 `Wine` 套娃方式，不推荐
  * 下载地址：https://deepin-wine.i-m.dev/
  * `wget -O- https://deepin-wine.i-m.dev/setup.sh | sh`
  * `sudo apt-get install -y com.qq.weixin.deepin`
  * 图片问题：`sudo apt install libjpeg62:i386`
  * 卸载：
    * `sudo apt-get remove com.qq.wechat.deepin`
    * `dpkg -l | grep wine`
    * `sudo apt remove deepin-wine6-stable deepin-wine-helper deepin-wine6-stable-amd64 deepin-wine6-stable-i386`
* [Linux]网易云音乐
  * 下载地址：https://music.163.com/#/download
  * 字体太小问题：
    * `sudo vim /usr/share/applications/netease-cloud-music.desktop`
    * 修改这一行：`Exec=netease-cloud-music --force-device-scale-factor=1.2 %U`
* [Linux]YesPlayMusic
  * 下载地址：https://github.com/qier222/YesPlayMusic

## 其他设置
* 连接远程共享文件夹/NAS
  * 设置->高级->文件->网络文件共享->点击`添加文件共享`
  * 输入相关设置
    * 文件共享地址：smb://192.168.x.x/folder-name
    * 用户名：共享文件夹/NAS 设置的访问账户用户名
    * 密码：共享文件夹/NAS 设置的账户密码
  * 也可以通过：文件->更多->服务->SMB文件共享来设置

## 总结
Pixelbook Go 在 2019 年底发布，借助轻量级 Chrome OS，主打轻薄为卖点。硬件方面一颗 i5 4核 CPU，足以带动 Chrome OS 操作系统；1080P 的屏幕比起 Macbook 的 Retina 屏幕还差点意思（不过高配有 4K 屏），但作为轻办公来说还算凑合，然而触摸屏比起 Macbook 可以算一个有点吧；键盘是一个亮点，有别与苹果和ThinkPad的手感，键程适中而且声音很小，码字是一个不错的选择；触摸板虽然滑起来有那么点 Macbook 的意思，但是机器反馈总是比震动马达差一些，如果能够魔改成震动马达那就完美了。硬件打分7.5，如果能够把屏幕和触摸板升级可以到9分。

软件方面 ChromeOS 启动速度的确让人刮目相看，但软件生态真的是差强人意，Google 为了能够让人接受它真的是煞费苦心，硬生生把 Android 和 Linux 容器塞进去，这种方案看起来是想弥补 WebApp 生态的不足，借助 Android 的娱乐和 Linux 的生产力提升 ChromeOS 的可玩性，但个人看起来做成了一个“四不像”！希望 Google 能够在 ChromeOS 上想想其它更好的方案。其实把 Android 和 Linux 应用装进去的确可以基本使用起来，但是总是非常蹩脚。软件打分5分，用起来就是不如 Windows、MacOS 甚至 Linux，有待改进。