# 玩转 Pixelbook 之 Ubuntu

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

使用 Clash for Windows 图形界面，但是在 Ubuntu 需要纯手动安装

* 下载：<https://github.com/Fndroid/clash_for_windows_pkg/releases>
  * Clash.for.Windows-0.20.7-x64-linux.tar.gz
* 解压：将文件内容解压到`/opt/clash-for-windows-bin`
* 运行：通过命令行进入到安装目录，直接运行`./cfw`
* 配置：TODO
  * Clash 配置
  * 系统代理配置：Settings -> Network -> Network Proxy
