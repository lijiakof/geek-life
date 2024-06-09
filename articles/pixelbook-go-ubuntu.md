# 玩转 Pixelbook 之 Ubuntu

## 系统安装

系统安装比较简单，做好镜像后通过 U 盘启动，按照提示一步一步设置就可以了。

## 软件安装

软件安装可以通过 3 种方式：

* Ubuntu Software：Ubuntu 自带软件市场，这种方式非常简单也容易管理，但是往往出现网络或者软件不能正常运行的情况
* 命令行安装：通过 `sudo apt install <app name>` 命令来安装
* 手动安装：到软件官网下载 `.deb` 软件包，然后通过 `sudo apt install <app path>` 命令来安装

## 中文输入法

Ubuntu 在输入法的支持上做得还不错，非常方便。

* Settings
  * Language -> Manage Installed Laguages -> Install/Remove Languages... -> Chinese
  * Keyboard -> Input Sources -> + Add an Input Source -> Chinese -> Chinese(Intelligent Pinyin)
* 切换到中文输入法 -> Topbar 右侧选中输入法 -> Perferences
  * Fuzzy syllable: 模糊拼音
  * Shortcuts: 中英文切换 `<Control>space`

## 操作习惯&体验

### Tweaks

* 安装：apt install gnome-tweaks
* 设置：
  * Mac cmd键：Keyboard & Mouse -> Additional Layout Options -> Alt and Win behavior -> Ctrl is mapped to Alt, Alt to Win
  * Mac 窗口按钮：Window Titlebars -> Placement -> Left

### Gnome 扩展插件

* 安装：Ubuntu Software -> Extensions
* 官网：<https://extensions.gnome.org/>
* Chrome 插件：GNOME Shell integration
* 插件：
  * ArcMenu：<https://extensions.gnome.org/extension/3628/arcmenu/>
  * Proxy Switcher：<https://extensions.gnome.org/extension/771/proxy-switcher/>
  * Transparent Top Bar：<https://extensions.gnome.org/extension/3960/transparent-top-bar-adjustable-transparency/>
  * Dash to Dock：<https://extensions.gnome.org/extension/307/dash-to-dock/>

## Clash

使用 Clash for Windows 图形界面，但是在 Ubuntu 需要纯手动安装。

* 下载：<https://github.com/Fndroid/clash_for_windows_pkg/releases>
  * Clash.for.Windows-0.20.7-x64-linux.tar.gz
* 解压：将文件内容解压到`/opt/clash-for-windows-bin`
* 运行：通过命令行进入到安装目录，直接运行`./cfw`

### 配置：TODO

Clash 在 Ubuntu 上的配置比较复杂，不仅要对 Clash 进行配置，而且要对系统的网络代理进行配置

* Clash 配置
* 系统代理配置：Settings -> Network -> Network Proxy
* 命令行运行/关闭代理
  * gsettings set org.gnome.system.proxy mode 'manual'
  * gsettings set org.gnome.system.proxy mode 'none'

## 常用软件

* Chrome：
  * 手动安装：
    * `wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb`
    * `sudo apt install ./google-chrome-stable_current_amd64.deb`
  * 命令安装：`sudo apt install google-chrome-stable`
* VSCode
  * Ubuntu Software：
    * 通过 Ubuntu 商店安装的 VSCode 是阉割版本，无法输入中文汉字
  * 手动安装：
    * 官网下载：<https://code.visualstudio.com/>
    * `sudo apt install code_1.73.1-1667967334_amd64.deb`
* Git
  * sudo apt install git
  * ssh-keygen -t ed25519 -C "your_email@example.com"
* zsh
  * `sudo apt install zsh`
  * `chsh -s /bin/zsh`
* 微信
  * https://software.openkylin.top/openkylin/yangtze/pool/all/
    * wechat-beta_1.0.0.236_amd64.deb
    * sudo dpkg -i wechat-beta_1.0.0.236_amd64.deb
  * <https://www.ubuntukylin.com/applications/106-cn.html>
  * 微信（Wine）:<https://www.ubuntukylin.com/applications/119-cn.html>
* Flameshot 截屏
  * `sudo apt install flameshot`
* MPV 播放器
  * `sudo apt install mpv`
* Etcher
  * <https://github.com/balena-io/etcher>
  * sudo apt update
  * sudo apt upgrade
  * sudo apt install wget apt-transport-https gnupg2
  * curl -1sLf 'https://dl.cloudsmith.io/public/balena/etcher/setup.deb.sh' | sudo -E bash
  * sudo apt update
  * sudo apt install balena-etcher-electron
* Neofetch 命令行系统显示
  * sudo apt install neofetch
* QQ 音乐
  * 官网下载：https://y.qq.com/download/download.html
  * sudo apt install ./qqmusic_1.1.5_amd64.deb
  * 闪退问题：
    * cd /sudo vi /usr/share/applications/qqmusic.desktop
    * 在 Exec 后面增加 --no-sandbox
    * Exec=/opt/qqmusic/qqmusic --no-sandbox %U

## 字体

* 系统
  * Tweaks -> Fonts
* VSCode
  * 位置：Setting -> Editor:Font Family
  * 默认：'Droid Sans Mono', 'monospace', monospace
  * 改为：'Noto Sans Mono CJK SC'
* Chrome
  * 位置：Setting -> Appearance -> Customize fonts
  * 改为：Noto Sans Mono CJK SC

## 自定义应用启动图标

有一些应用不能通过 `apt` 命令来安装，这样每次启动应用需要我们通过命令行来操作，使用起来不太方便，但是我们可以通过自定义程序启动图标来让这些应用和普通桌面应用一样。

* 进入应用程序文件夹 `cd /usr/share/applications/`
* 创建应用桌面文件 `your_app.desktop` ,文件内容如下
* 设置权限 `sudo chmod 744 your_app.desktop`
* 重启系统

your_app.desktop 文件内容：

```text
[Desktop Entry]
Encoding=UTF-8
Name=Clash
Comment=Clash for Windows
Exec=/opt/clash-for-windows-bin/cfw 
Icon=/opt/clash-for-windows-bin/clash-icon.png
Terminal=false
StartupNotify=true
Type=Application
```

## 解决声卡等问题

<https://github.com/yusefnapora/pixelbook-linux>
