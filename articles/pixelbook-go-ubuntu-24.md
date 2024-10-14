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

# 快捷键设置

* Mac 键映射
  * 优化（Tweaks）：Keyboard & Mouse -> Additional Layout Options -> Alt and Win behavior -> Ctrl is mapped to Alt, Alt to Win
* 设置 -> 键盘 -> 键盘快捷键
  * 声音和媒体：
    * 播放（或播放/暂停）
    * 减少音量
    * 增大音量
    * 音量静音/取消静音
* 屏幕亮度

# 常用软件

* Clash 
* Chrome
* VSCode
* Zsh
* Git
* Nodejs
* 微信
* QQ
* MPV 播放器
* Etcher

## Clash
使用 Clash for Windows 带图形界面的科学上网工具，但是在 Ubuntu 需要纯手动安装。

* 下载地址：<https://archive.org/download/clash_for_windows_pkg>
  * Clash.for.Windows-0.20.39-x64-linux.tar.gz
* 解压程序：将文件内容解压到`/opt/clash-for-windows`
* 运行程序：通过命令行进入到安装目录，直接运行`./cfw` 会报错，要做成自定义程序启动图标来启动，并且标注`--no-sandbox`启动方式
  * Exec=/opt/clash-for-windows/cfw --no-sandbox %U
  * 如何制作程序启动图标，查看文档“自定义应用启动图标”这一章节
* 虚拟网卡安装：General->Server Mode->Manage->Install
* 配置代理：设置->网络->代理
  * HTTP  代理：127.0.0.1:7890
  * HTTPS 代理：127.0.0.1:7890
* 参考文档：https://docs.gtk.pw/

## Chrome

* 手动安装：
  * 下载地址：https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
  * 命令安装：`sudo apt install ./google-chrome-stable_current_amd64.deb`
* 命令安装：`sudo apt install google-chrome-stable`

## VSCode

* 手动安装：
  * 官网下载：<https://code.visualstudio.com/>
  * 命令安装：`sudo apt install code_1.90.0-1717531825_amd64.deb`
* 应用中心：
  * 通过 Ubuntu 应用中心安装的 VSCode 是阉割版本，无法输入中文汉字

## Zsh

* 命令安装：
  * `sudo apt install zsh`
  * `chsh -s /bin/zsh`
* 终端美化
  * 终端首选项 -> 颜色 -> 文本和背景颜色 -> 内置方案：GNOME 暗色

### Oh My Zsh

* 官网地址：https://ohmyz.sh/
* 命令安装：sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
* 修改皮肤：vim ~/.zshrc
  * ZSH_THEME="afowler"

### Neofetch 命令行系统显示

* 命令安装：
  * `sudo apt install neofetch`
* 设置启动时运行：
  * echo "" >> ~/.zshrc
  * echo "# Automatically run neofetch on startup" >> ~/.zshrc
  * echo "neofetch" >> ~/.zshrc
  * source ~/.zshrc 

## Git

* 命令安装：
  * `sudo apt install git`
  * `ssh-keygen -t ed25519 -C "your_email@example.com"`

## Nodejs

* 命令安装：
  * `sudo apt install nodejs`

### NVM

* 手动安装：
  * 官网地址：https://github.com/nvm-sh/nvm
  * `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash`
  * export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
  * [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads 
* 常用命令：
  * nvm list
  * nvm install 18.20.2
  * nvm use 18.20.2
  * nvm alias default 20.14

## 微信

* 手动安装：
  * 下载地址：https://software.openkylin.top/openkylin/yangtze/pool/all/
  * 安装文件：wechat-beta_1.0.0.236_amd64.deb
  * 命令安装：`sudo dpkg -i wechat-beta_1.0.0.236_amd64.deb`

## QQ

* 手动安装：
  * 下载地址：https://im.qq.com/linuxqq/index.shtml
  * 安装文件：QQ_3.2.9_240606_amd64_01.deb
  * 命令安装：`sudo apt install ./QQ_3.2.9_240606_amd64_01.deb`

## QQ 音乐

* 手动安装
  * 下载地址：https://y.qq.com/download/download.html
  * 安装文件：qqmusic_1.1.5_amd64_.deb
  * 安装命令：`sudo apt install ./qqmusic_1.1.5_amd64_.deb`
  * 注意：需要修改配置 `/usr/share/applications/qqmusic.desktop` 文件才能启动

```
[Desktop Entry]
Name=QQMusic
Exec=/opt/qqmusic/qqmusic --no-sandbox %U
Terminal=false
Type=Application
Icon=qqmusic
StartupWMClass=qqmusic
Comment=Tencent QQMusic
Categories=AudioVideo;Audio;Player;
MimeType=application/x-ogg;application/ogg;audio/x-vorbis+ogg;audio/vorbis;audio/x-vorbis;audio/x-scpls;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-mpegurl;audio/x-flac;audio/mp4;audio/x-it;audio/x-mod;audio/x-s3m;audio/x-stm;audio/x-xm;
Keywords=Audio;Song;MP3;CD;Podcast;MTP;iPod;Playlist;Last.fm;UPnP;DLNA;Radio;
```

## CMUS 音乐播放器
* 命令安装
  * `sudo apt install cmus`
* 常用命令
  * 运行软件：cmus
  * 添加音乐：:a /your/music/path
  * 切换模式：tab（在专辑/歌曲之间切换）
  * 播放音乐：x 或者 Enter
  * 暂停音乐：c

## MPV 播放器

* 应用中心安装

## Etcher

* 手动安装
  * 下载地址：https://etcher.balena.io/
  * 命令安装：`sudo dpkg -i ./balena-etcher_1.19.21_amd64.deb`


# 自定义应用启动图标

有一些应用不能通过 `apt` 命令来安装，这样每次启动应用需要我们通过命令行来操作，使用起来不太方便，但是我们可以通过自定义程序启动图标来让这些应用和普通桌面应用一样。

* 进入应用程序文件夹 `cd /usr/share/applications/`
* 创建应用桌面文件 `your_app.desktop` ,文件内容如下
  * 程序图标：Icon=
  * Dock 图标：StartupWMClass=
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
StartupWMClass=Clash for Windows
```

# 声卡问题

非常感谢 GitHub 的 Geeker，这位叫做 WeirdTreeThing 的解决方案，完美解决 Chromebook 安装 Linux 的声卡问题，再次感恩。 https://github.com/WeirdTreeThing/chromebook-linux-audio

TODO：
另外，由于

# 其它

## flac 转 mp3

* find -name "*.flac" -exec ffmpeg -i {} -acodec libmp3lame -ab 128k {}.mp3 \;
* rename 's/\.flac//' *.mp3