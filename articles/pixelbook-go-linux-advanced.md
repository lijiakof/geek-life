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
* 左上角：Settings -> Multitasking -> General -> Hot Corner
* 开启Snap：Software -> Performances -> Third Party -> Snap
  * 这样软件就能够更新小版本了

### VSCode

* git
  * Access Token
    * GitHub -> Setting -> Developer settings -> Personal access tokens
  * 提交过程中会提示
    * Access Token：此处填写生成的 access tokens
    * Username：此处填写GitHub账户名称
    * Password：此处填写生成的 access tokens
  * 记住每次提交、同步操作时要输入用户名密码过程：git config --global credential.helper store
* Power Mode
  * Powermode Enabled：打开
  * Powermode>Shake Enabled：关闭

## 截屏

* flameshot
  * 设置快捷键：Custom Shotcuts
    * Name: Screen Shot
    * Commond: flameshot gui
    * Shotcut

### 微信

A JavaScript error occurred in the main process
Error: spawn /usr/bin/scrot ENOENT
at ChildProcess._handle.onexit(node:internal/child_process:283:19)
at onErrorNT(node:internal/child_process:478:16)
at process.processTicksAndRejections(node:internal/process/task_queues:83:21)

## 开机速度优化

## coreboot

## 开机LOGO

* 安装
  * sudo pacman -S plymouth 新版本自带
* 将 plymouth 添加到 mkinitcpio.conf 的 HOOKS
  * `sudo vim /etc/mkinitcpio.conf`
  * `HOOKS="base udev plymouth autodetect modconf block keyboard keymap consolefont plymouth filesystems fsck"`
* 配置 grub
  * `sudo vim /etc/default/grub`
  * 'GRUB_TIMEOUT=1'
* 重新生成引导配置：`grub-mkconfig -o /boot/grub/grub.cfg`
* 重建 initrd 镜像：`mkinitcpio -p linux<version>`
* 配置 plymouth
  * `sudo plymouth-set-default-theme -l`
  * `sudo plymouth-set-default-theme -R spinfinity`
  * `/etc/plymouth/plymouthd.conf`

<https://www.jianshu.com/p/a908153d1a4d>
<https://wiki.archlinux.org/title/plymouth>
<https://www.youtube.com/watch?v=eTk2yG1JFsE>
