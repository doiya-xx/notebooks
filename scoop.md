# Scoop

`windows`的包管理工具，类似`unix`的`apt-get`或者`ubuntu`的`apt`工具。

可以进行统一的包管理。

## Installation

```shell
# in pwoershell
# prerequisites
# 查看 PowerShell 版本，如果版本低于5.1则需要下载5.1版本
$PSVersionTable
# 查看 .NET framework 版本，需要 4.5 版本
$PSVersionTable.CLRVersion
#
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
# advanced installation
mkdir D:/Scoop/
cd D:/Scoop/
# 安装下载脚本，如果无法解析域名，则需要挂代理
irm get.scoop.sh -outfile 'install.ps1'
# 自定义安装路径
.\install.ps1 -ScoopDir 'D:\Scoop' -ScoopGlobalDir 'D:\Scoop\GlobalScoopApps' -NoProxy
# 目录结构
D:\Scoop\apps\ # 软件安装目录
D:\Scoop\buckets\ # 软件下载源目录
D:\Scoop\shims\ # 软件启动目录
# 配置系统环境变量
Path = "D:\Scoop\shims\" # 安装的app的启动程序.exe都会放在这里
```

scoop 命令行

```shell
# install apps
scoop install <app>
scoop install -g <app> # 全局安装，D:\Scoop\GlobalScoopApps


```