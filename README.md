# 程序员 Mac 开光指南

## 键盘符号映射
| 按键 | 符号 |
| --- | --- |
| Command | ⌘ |
| Shift | ⇧ |
| Option | ⌥ |
| Control | ^ |
| Caps Lock | ⇪ |


## 基础设施

### 关闭 `SIP` 保护
开启：`系统偏好设置 > 安全性与隐私 > 通用`中的`任何来源`：
```shell
sudo spctl --master-disable
```


### 设置
- `系统偏好设置 > 触控板 > 光标与点按`
    `轻点来点按（勾选）`

- `系统偏好设置 > 触控板 > 更多手势`
    `App Expose（勾选）`
    `在全屏幕显示的App之间轻扫（四指左右轻扫）`

- `系统偏好设置 > 辅助功能 > 指针控制 > 鼠标与触控板 > 触控板选项`
    `启动拖移（勾选）> 三指拖移`



### 修改主机名
> 就是为了好看点
参考文章：https://shockerli.net/post/macos-hostname-scutil/
`系统偏好设置 > 共享` => 修改`电脑名称`



### Xcode Command Line Tools
> macOS 系统很多软件都需要用到的依赖工具
```shell
xcode-select --install
```



### 梯子

#### V2rayU
> 需要自己找账号
https://github.com/yanue/V2rayU


#### SetupVPN
> 谷歌插件




### Homebrew
https://brew.sh/index_zh-cn
https://github.com/Homebrew/install


#### 镜像源
清华大学开源软件镜像站及教程: https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/

```shell
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"
```


#### 安装
```shell
# 从本镜像下载安装脚本并安装 Homebrew / Linuxbrew
git clone --depth=1 https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/install.git brew-install
/bin/bash brew-install/install.sh
rm -rf brew-install
```


#### cask 等其他仓库
```shell
brew tap --custom-remote --force-auto-update homebrew/core https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
brew tap --custom-remote --force-auto-update homebrew/cask https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
brew tap --custom-remote --force-auto-update homebrew/cask-fonts https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask-fonts.git
brew tap --custom-remote --force-auto-update homebrew/cask-drivers https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask-drivers.git
brew tap --custom-remote --force-auto-update homebrew/cask-versions https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask-versions.git
brew tap --custom-remote --force-auto-update homebrew/command-not-found https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-command-not-found.git
```



### iTerm2
安装：https://www.iterm2.com

主题站点：https://iterm2colorschemes.com

主题选择：`Profiles -> Colors -> Color Presets` 选择 `Solarized Dark`

配置参考: https://www.cnblogs.com/xishuai/p/mac-iterm2.html


#### 配置左右键前后单词跳转
> 按住 `option + → or ←` 键，在命令的开始和结尾跳转切换

`Profiles → Default → Keys`，点击 `+`：

`Keyboard shortcut`: `option + →`
`Action`: `Send Escape Sequence`
`Esc + f`

`Keyboard shortcut`: `option + ←`
`Action`: `Send Escape Sequence`
`Esc + b`

![配置命令行单词跳转](media/16309837738839/16372943030276.jpg)



#### iTerm2 快速隐藏和显示
`Keys → Hotkey`，勾选`Show/hide all windows with a system-wide hotkey`，并设置快捷键，比如`command + .`




### Oh My Zsh
GitHub: https://github.com/ohmyzsh/ohmyzsh

通过`curl`安装:
```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

`Zsh` 设置为当前用户的默认 `Shell`:
```shell
chsh -s /bin/zsh
```

配置文件: `~/.zshrc`

设置主题:
支持的主题列表: https://github.com/ohmyzsh/ohmyzsh/wiki/themes
在配置文件中，修改这一行:
```shell
ZSH_THEME="robbyrussell"
```

#### 插件

##### zsh-syntax-highlighting
> 日常用的命令会高亮显示，命令错误显示红色
> 
> https://github.com/zsh-users/zsh-syntax-highlighting

```shell
brew install zsh-syntax-highlighting
```

安装完后，根据`brew`的提示，打开`~/.zshrc`添加:
```shell
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

##### zsh-autosuggestions
> 输入命令时可提示自动补全（灰色部分），按键 `→` 即可补全
> 
> https://github.com/zsh-users/zsh-autosuggestions


```shell
brew install zsh-autosuggestions
```

安装完后，根据`brew`的提示，打开`~/.zshrc`添加:
```shell
source /usr/local/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```


##### autojump
> 实现目录间快速跳转，想去哪个目录直接 `j + 目录名`
> 
> https://github.com/wting/autojump

```shell
brew install autojump
```

安装完后，根据`brew`的提示，打开`~/.zshrc`添加:
```shell
[ -f /usr/local/etc/profile.d/autojump.sh ] && . /usr/local/etc/profile.d/autojump.sh
```




## 系统工具

### 腾讯柠檬清理
> 腾讯的清理、卸载、流量、监控、开机启动管理等

官网下载：https://lemon.qq.com



### 搜狗输入法
官网下载：https://pinyin.sogou.com/mac/
输入法配置：`系统偏好设置 > 键盘 > 输入法 > 删除无用的输入法`
同步原配置：`偏好设置 > 登录账户 > 同步 > 配置同步 > 下载配置`


### Chrome
官网下载: https://www.google.cn/intl/zh-CN/chrome/

#### 扩展
- Infinity New Tab Pro: 新标签页
- FeHelper: 前端工具集
- Adblock Plus: 广告净化
- SimpRead: 最佳阅读体验
- Tampermonkey: 油猴脚本
- ImageAssistant: 图片助手，网页图片提取下载


### Alfred
- Features > Web Search > 新增自定义搜索并关闭不需要的搜索
- Features > Default Results > Setup fallback results > 设置使用搜索方式
- Features > Clipboard History > 勾选需要剪贴板存储的内容（文本、图片、文件）及保存时间
- Appearance > 选择 Alfred macOS 切换主题样式


### uTools
> 一个可替代 Alfred 大部分功能的国产辅助软件

官方下载：http://www.u.tools

#### 设置
- 快捷键
`偏好设置` > `基本设置` > `快捷键` > `显示/隐藏快捷键` > `Option + Space`


#### 插件
- hosts切换
- 编码小助手
- 计算稿纸
- 网页打开
- 剪切板


### Vim
`~/.vimrc` 简单配置：

```vim
syntax on
set runtimepath+=~/.vim_runtime
set nocompatible
set history=1000
set autoindent
set cindent
set smartindent
set tabstop=4
set shiftwidth=4
set softtabstop=4
set showmatch
set guioptions-=T
set vb t_vb=
set ruler
set incsearch
```


### autossh
> 一个简单管理远程 SSH 账号的脚本工具

- 安装
```shell
curl -o /usr/local/bin/autossh https://raw.githubusercontent.com/FeeiCN/autossh/master/autossh
chmod +x /usr/local/bin/autossh
```

- 配置
```shell
$ cat ~/.autosshrc
server_name|192.168.1.110|root|password|port|is_bastion
```

### 开发软件
- `SourceTree`：Git 可视化（免费）
- `Navicat Premium`：多种数据库管理工具
- `Sourcetrail`：源码阅读神器（[开源](https://github.com/CoatiSoftware/Sourcetrail)）
- `Jetbrains IDE 系列`
- `Postman`：接口调试（免费）
- `htop`：增强版 `top` 命令（[开源](https://github.com/htop-dev/htop)）
- `Visual Studio Code`：强大的编辑器（[开源](https://code.visualstudio.com)）


#### Sublime Text
安装`Package Control`，https://packagecontrol.io/installation
安装中文插件：`ChineseLocalizations`

- 配置 `subl` 命令行打开文件

> 在 `~/.zshrc` 添加如下配置:

```shell
alias subl="'/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl'"
```



### 其他软件
- `万年历`：日历（免费）
- `网易有道词典`：翻译（免费）
- `iShot`：截图（免费）
- `嘀嗒清单`：时间与日程管理
- `MWeb`/`Typora`/`FSNotes`：Markdown 笔记管理
- `FastZip/MacZip`：解压缩（免费）
- `NTFSTool`：NTFS格式硬盘读写（开源，但停更了，不支持 macOS >= 11.0）
- `OmniGraffle Pro`：图表/流程图等矢量图绘制
- `Sketch`：矢量图绘制
- `Axure RP`：交互原型设计
- `Reeder`：RSS 订阅
- `IINA`：音视频播放器（[开源](https://github.com/iina/iina)）
- `Beyond Compare`：文件/文本对比



## 开发环境

### Java
> Java SE Development Kit 8uXXX

下载地址：https://www.oracle.com/java/technologies/downloads/#java8-mac

下载安装，然后验证：
```shell
➜  ~ java -version
java version "1.8.0_311"
Java(TM) SE Runtime Environment (build 1.8.0_311-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.311-b11, mixed mode)
```

配置 `JAVA_HOME` 环境变量：
```shell
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_311.jdk/Contents/Home
```


### PHP
#### 安装
> 由于官方维护的 PHP 版本都是最新的几个，对于比较老的版本，就没法直接安装，需要 Tap 一个第三方源

强烈推荐: [shivammathur/php](https://github.com/shivammathur/homebrew-php)

- 添加 Tap

```shell
brew tap shivammathur/php
```

- 安装 PHP
> 此处示例安装 `PHP 7.1`
```shell
brew install shivammathur/php/php@7.1
```

> 将此版本替换为命令行默认版本
```shell
brew link --overwrite --force php@7.1
```

- 配置
> 打开配置文件修改默认时区
```ini
date.timezone = PRC
```


#### Composer
- 安装
```shell
brew install composer
```

- 降级
如果一些老项目不支持 Composer V2，那么需要回退到 V1 版本
```shell
composer self-update --1
```

- 镜像
```shell
composer config -g repo.packagist composer https://packagist.phpcomposer.com
```



### Go
#### 安装
安装最新版本
```shell
brew install go
```

或者指定版本
```shell
brew install go@1.13
```

非最新版本，需要建立个链接，这样才能用到 Go 命令
```shell
brew link --overwrite --force go@1.13
```


#### 配置
- 环境变量
```shell
export GO111MODULE=on
export GOPATH=/Users/jioby/gowork
export PATH="$GOPATH/bin:$PATH"
export GOPROXY=https://goproxy.cn,https://goproxy.io,direct
export GOPRIVATE=*.your-private-git.com
```

- 私有仓库
终端运行命令 `git config --global -e`，添加如下类似配置并保持：
```shell
[url "ssh://git@git.example.com:8182/"]
        insteadOf = https://git.example.com/
```


