# 玩转 Pixelbook 之 Linux 进阶

https://apps.gnome.org/zh-CN/

## 生产力

### zsh

```
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