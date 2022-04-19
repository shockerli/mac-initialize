# Mac 开光指南
> 一份新 Mac 快速食用方法
> 
> 长期更新地址: https://github.com/shockerli/mac-initialize


## 键盘符号与快捷键
### 符号映射
| 按键 | 符号 |
| --- | --- |
| Command（Cmd） | ⌘ |
| Shift | ⇧ |
| Option（Alt） | ⌥ |
| Control（Ctrl） | ^ |
| Caps Lock | ⇪ |


### 常用快捷键
大部分情况下，Command 键等同于 Windows 的 Ctrl 键，以下仅列出部分常用或与 Windows 不一样的快捷键，更多参考官方 [Mac 键盘快捷键](https://support.apple.com/zh-cn/HT201236)

- **Command-Z**：撤销，Shift-Command-Z：重做
- **Command-Tab**：在多个打开的 App 之间切换到下一个最近使用的 App
- **Command-逗号 (,)**：打开最前面的应用的偏好设置
- **Control-Command-Q**：立即锁定屏幕
- **Command-D**：复制所选文件
- **Option-Command-D**：显示或隐藏“程序坞”
- **Command–上箭头**：打开包含当前文件夹的文件夹
- **Command–左中括号 ([)**：前往上一文件夹
- **Command–右中括号 (])**：前往下一个文件夹
- **Command-Delete**：将所选项移到废纸篓
- **Control–下箭头**：显示最前面的应用的所有窗口
- **Control-Command-D**：显示或隐藏所选字词的定义
- **Control–A**：移至行或段落的开头
- **Control–E**：移至行或段落的末尾

其他快捷键：选取苹果菜单 > “系统偏好设置”，点按“键盘”，然后点按“快捷键”。


## 基础设施

### 触摸板操作设置
触控板的设置及使用教程，可查看 `系统偏好设置 > 触控板`。

> 让你的触摸板变的跟鼠标不同，治疗你的手指关节炎😄

- `系统偏好设置 > 触控板 > 光标与点按`
    * `轻点来点按（勾选）`
    * <u>可单指轻点=鼠标左键点击，可双指轻点=鼠标右键点击</u>

- `系统偏好设置 > 触控板 > 更多手势`
    * `App Expose（勾选）`
    * `在全屏幕显示的App之间轻扫（四指左右轻扫）`
    * <u>以上两个选项，将三指操作改为四指操作，是为了给「三指拖移」让路</u>

- `系统偏好设置 > 辅助功能 > 指针控制 > 鼠标与触控板 > 触控板选项`
    * `启动拖移（勾选）> 三指拖移`
    * <u>与鼠标左键按住拖动一样，三个手指同时在触摸板滑动，可拖动任何窗口的菜单栏进行移动，也可以选择范围内容</u>



### 开启任何来源
现在的 macOS 都有 SIP 保护，需要执行以下命令关闭：

```shell
sudo spctl --master-disable
```

然后才可以打开`任何来源`：`系统偏好设置 > 安全性与隐私 > 通用 > 任何来源`

关于其他一些软件无法安装的问题，可参考这篇文章：

https://www.macwk.com/article/macos-file-damage


### 修改主机名
> 就是为了好看点

参考文章：https://shockerli.net/post/macos-hostname-scutil/

`系统偏好设置 > 共享` => 修改`电脑名称`



### Xcode Command Line Tools
> macOS 系统很多软件都需要用到的依赖工具，不安装的话连 Git 都没法用🙄

```shell
xcode-select --install
```



### Homebrew
macOS 最强大的软件包安装管理器。

官网：https://brew.sh
GitHub：https://github.com/Homebrew/brew


因国内访问 GitHub 不稳定，可以直接参考清华大学镜像站的安装教程，简单快速。

清华大学开源软件镜像站及安装、镜像教程: https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/



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


#### iTerm2 快速隐藏和显示
`Keys → Hotkey`，勾选 `Show/hide all windows with a system-wide hotkey`，并设置快捷键，比如 `⌘ + .`



### Oh My Zsh
`Oh My Zsh` 让 zsh 变得更好用、配置更简单。

GitHub: https://github.com/ohmyzsh/ohmyzsh

- 通过`curl`安装
```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- 设置 zsh 为当前用户的默认 `Shell`:
```shell
chsh -s /bin/zsh
```

- 配置文件: `~/.zshrc`

- 设置主题

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

官网免费下载：https://lemon.qq.com

如果不放心的话，可以用 `App Cleaner & Uninstaller Pro`。


### 搜狗输入法
官网下载：https://pinyin.sogou.com/mac/

输入法配置：`系统偏好设置 > 键盘 > 输入法`：删除无用的输入法

同步原配置：`偏好设置 > 登录账户 > 同步 > 配置同步 > 下载配置`


### Chrome
官网下载: https://www.google.cn/intl/zh-CN/chrome/

#### 扩展
- [Infinity New Tab Pro](http://cn.infinitynewtab.com): 新标签页
- [FeHelper](https://www.baidufe.com/fehelper): 前端工具集（内含 JSON 美化对比、时间转换、编码转换等十几个小工具）
- [Adblock Plus](https://adblockplus.org): 广告净化
- [SimpRead](http://ksria.com/simpread): 最佳阅读体验
- [Tampermonkey](https://www.tampermonkey.net): 油猴脚本管理
- [ImageAssistant](http://www.pullywood.com/ImageAssistant): 图片助手，网页图片提取下载
- [SourceGraph.com](https://sourcegraph.com): GitHub 源码浏览神器


#### 油猴脚本
油猴脚本（用户脚本）是一段代码，它们能够优化您的网页浏览体验。安装之后，有些脚本能为网站添加新的功能，有些能使网站的界面更加易用，有些则能隐藏网站上烦人的部分内容。

[Tampermonkey](https://www.tampermonkey.net) 是一个可运行在 Chrome、Firefox、Safari、Edge 等浏览器的用户脚本管理扩展。

[Greasy Fork](https://greasyfork.org) 则是一个油猴脚本免费商店，绝大部分用户脚本都在上面有发布，方便查找、安装使用。

推荐脚本：
- [Bilibili-Evolved](https://github.com/the1812/Bilibili-Evolved) - B站增强
- [CSDNGreener](https://github.com/adlered/CSDNGreener) - CSDN 网站绿化


### Alfred
效率工具神器，可以快速的搜索本地应用、搜索本地文件、执行终端命令、浏览器搜索、打开网址、剪切板管理、翻译、文件管理、音乐控制等，也可以自定义工作流，与其他软件深度配合。

软件小巧、性能强悍、高级功能需付费，配置同步可用 iCloud 或 Git 或自己想办法。

官网：https://www.alfredapp.com

#### 常用配置
- `Features` > `Web Search` > 新增自定义搜索、关闭不需要的搜索
- `Features` > `Default Results` > `Setup fallback results` > 设置使用搜索方式
- `Features` > `Clipboard History` > 勾选需要剪贴板存储的内容（文本、图片、文件）及保存时间
- `Appearance` > 选择 `Alfred macOS` 切换主题样式

#### Workflows
可参考下面两个收藏集合内的配置：
- [learn-anything/alfred-workflows](https://github.com/learn-anything/alfred-workflows)
- [zenorocha/alfred-workflows](https://github.com/zenorocha/alfred-workflows)


### uTools
一个可替代 Alfred 大部分功能的国产效率工具，基于 Electron 构建（劣势）、自带插件市场（优势）、配置同步需开通会员订阅。

如果是轻度用户，可选择 uTools，简单。当然，Alfred 与 uTools 同时安装并不冲突。

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
- `Charles` / `Proxyman`：代理抓包工具


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
- `MWeb` / `Typora` / `FSNotes`：Markdown 笔记管理
- `FastZip/MacZip`：解压缩（免费）
- `NTFSTool`：NTFS 格式硬盘读写（开源，但停更了，不支持 macOS >= 11.0）
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


