## 安装和启动

### 下载安装PhpStorm

如果还没有安装可以点击 [下载地址](https://www.jetbrains.com/phpstorm/download/#section=windows) 进行下载最新版本的PhpStorm（选择自己的版本）
根据自己的版本选择安装：

> Windows : 运行 `.exe` 文件并根据 PhpStorm 安装向导的指引操作。
>
> OS X : 打开 `.dmg` 包，然后拖动 PhpStorm 到应用文件夹。
>
> Linux ： 解压 `.tar.gz` 到你的目录的文件夹中。

多平台启动PhpStorm

1、Windows 下启动 PhpStorm

如果安装时选择了在桌面创建快捷方式就双击图标就行；否则，就进入PhpStorm文件夹加下的bin文件夹中的PhpStorm.exe应用程序
例如：E:\Program Files (x86)\JetBrains\PhpStorm 2016.2.1\bin\PhpStorm.exe

2、OS X下启动PhpStorm :

当第一次启动PhpStorm时，完成安装的对话框会打开。然后有一个从之前版本导入偏好设置和许可证的选项。

选择以下选项之一并点击OK：
>
- 我想从之前版本导入设置(\)： 如果这个选项出现在对话框中,包含PhpStorm设置目录和许可信息在其默认位置被发现。(相应的路径显示选项名称在括号内)最有可能的是,这是你想要的选项。
- 我想从自定义位置导入设置： 你可能有设置目录和许可信息但不是在其默认位置。如果上面讨论的选项消失,PhpStorm并不知道这个目录在哪里;字段所示的路径最初只是一种猜测,不能保证必要的文件夹是真的。在这种情况下导入设置,您可以指定的配置文件(如果你知道它在哪里),或者一个先前PhpStorm版本的安装文件夹。要做到这一点,点击.按钮并在打开的对话框中选择文件夹。
- 我没有之前版本的PhpStorm或者我不想导入我的设置： 如果你属于这种情况，选择该选项。而且，如果您想改变PhpStorm的运行JDK，使用Switch Boot JDK操作，为了调用该操作，使用 Searching Everywhere 或 Find Action。

3、Linux下启动PhpStorm

在linux下启动PhpStorm，按照以下步骤：
> 1、从下载页面下载的 `PhpStorm-*.tar.gz` 文件。
>
> 2、使用以下命令解压文件至一个空目录下运行 `tar xfz PhpStorm-*.tar.gz`
>
> 3、因为从下载文件的位置运行PhpStorm可能不方便，可以使用mv命令将下载的文件或解压后的文件夹移动到方便的位置：
- mv `path to PhpStorm-*.tar.gz`  `new archive folder`
- 或
- mv `path to extracted archive folder`  `new archive folder`
- 例如:
- mv /downloads/PhpStorm-*.tar.gz  my/desired/location
- 或
- mv /downloads/PhpStorm-*  my/desired/location
>
> 4、切换到新位置的bin/目录下：
>
- cd  new archive folder/PhpStorm-*/bin
- 如：
- cd my/desired/location/PhpStorm-*/bin
>
> 5、在bin文件夹中执行 `phpstorm.sh`

### 激活PhpStorm

可以进行注册PhpStorm 的账号，也可以自己百度找一些激活码。

## 快捷键

PhpStorm，一个以快捷键为中心的IDE，对它的大部分动作建议使用快捷键。在这个主题中，你可以发现一个简短的但是不可或缺的列表，能使你使用PhpStorm的第一步更加容易。

在Keyboard Shortcuts Reference(快捷键参考)中查看详细的默认快捷键列表，在Configuring Keyboard Shortcuts(配置快捷键)章节中学习如何定制化你偏爱的快捷键。

完整的快捷键参考在主菜单(Help | Keymap Reference )中可用。





参考文件：

参考原版地址：
[https://www.jetbrains.com/help/phpstorm/reference.html](https://www.jetbrains.com/help/phpstorm/reference.html)：

参考中文版地址：
[http://phpstorm.book.jellychen.cn/](http://phpstorm.book.jellychen.cn/)
