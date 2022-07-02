# 玩转 Pixelbook 之 Linux 进阶

* https://apps.gnome.org/zh-CN/
* https://www.zhihu.com/search?type=content&q=manjaro%20git%20%E5%BA%94%E7%94%A8

## 生产力

### zsh

```bash
# 安装 zsh
sudo pacman -S zsh

# 修改默认 shell
sudo chsh -s /bin/zsh
[sudo] password for jay: 
Changing shell for root.
Shell changed.

# 安装 Oh My Zsh
# https://github.com/ohmyzsh/ohmyzsh
wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh
sh install.sh
```

## 插件

* Unite：Top bar（顶部面板） 与应用菜单栏 融为一体，增加工作区域

## 美化

https://www.gnome-look.org/browse/

* latte-dock
* Font-Downloader：fontdownloader
  * Noto Sans SC
* Font Manager：font-manager
* gnome-terminal-transparency

## 设置

* 触摸板：Tweaks -> Keyboard & Mouse -> Mouse Click Emulation -> Fingers

### VSCode

* git
  * Access Token
    * GitHub -> Setting -> Developer settings -> Personal access tokens
  * 提交过程中会提示
    * Access Token：此处填写生成的 access tokens
    * Username：此处填写GitHub账户名称
    * Password：此处填写生成的 access tokens
  * 记住每次提交、同步操作时要输入用户名密码过程：git config --global credential.helper store

## 开机速度优化
