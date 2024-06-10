# 玩转 Pixelbook 之 Ubuntu 24.04

最近 Ubuntu 升级到了 24.04 版本，珍藏很久的 Pixelbook 也需要来一次大升级，未来将作为创作的主力机。



## 系统安装

系统安装还是老步骤，在 Ubuntu 官网下载最新安装镜像包，用`balena-etcher` 工具做好启动盘，设置好 BIOS 通过 U 盘启动，接下来就是按照提示一步一步安装就行了。本次安装选择的是中文版本，在本地化方面体验会好一些。



## 软件安装

软件安装可以通过 3 种方式：

* 应用中心安装：Ubuntu 自带应用中心，这种方式非常简单也容易管理，但是往往出现网络或者软件不能正常运行的情况
* 命令行安装：通过 `sudo apt install <app name>` 命令来安装
* 手动安装：到软件官网下载 `.deb` 软件包，然后通过 `sudo apt install <app path>` 命令来安装


# 系统设置

* gnome-shell-extensions
* gnome-tweaks

TODO:


# 常用软件

* Clash
* Chrome
* VSCode
* Zsh
* Git
* 微信
* Etcher


## Clash
TODO:
使用 Clash for Windows 图形界面，但是在 Ubuntu 需要纯手动安装。

* 下载地址：<https://archive.org/download/clash_for_windows_pkg>
  * Clash.for.Windows-0.20.39-x64-linux.tar.gz
* 解压：将文件内容解压到`/opt/clash-for-windows`
* 运行：通过命令行进入到安装目录，直接运行`./cfw` 会报错，要做成自定义程序启动图标来启动，并且标注`--no-sandbox`启动方式
  * Exec=/opt/clash-for-windows/cfw --no-sandbox %U
* Server Mode
* 配置本机代理：设置->网络->代理
  * HTTP  代理：127.0.0.1:7890
  * HTTPS 代理：127.0.0.1:7890

## Chrome

* 手动安装：
  * `wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb`
  * `sudo apt install ./google-chrome-stable_current_amd64.deb`
* 命令安装：`sudo apt install google-chrome-stable`

## VSCode

* 应用中心：
  * 通过 Ubuntu 应用中心安装的 VSCode 是阉割版本，无法输入中文汉字
* 手动安装：
  * 官网下载：<https://code.visualstudio.com/>
  * `sudo apt install code_1.90.0-1717531825_amd64.deb`

## Zsh

* 命令安装：
  * `sudo apt install zsh`
  * `chsh -s /bin/zsh`

## Git

* 命令安装：
  * `sudo apt install git`
  * `ssh-keygen -t ed25519 -C "your_email@example.com"`

## 微信

* 手动安装：
  * 下载地址：https://software.openkylin.top/openkylin/yangtze/pool/all/
  * 安装文件：wechat-beta_1.0.0.236_amd64.deb
  * `sudo dpkg -i wechat-beta_1.0.0.236_amd64.deb`

## Etcher


# 自定义应用启动图标

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
