# 更新与重置面板

:::tip
如果你担心更新导致数据丢失，先将 web/data，daemon/data 移动到其他上层目录。更新完毕后再移动回来即可保证数据安全性。

若您的版本在 2024/09/29 前发布，请在更新前先删除 lib 文件夹内所有 pty 程序，以便修复 pty 僵尸进程问题。
:::

## 更新须知

因为采用守护进程分布式部署，如果你的节点超过 5 个，那么更新将有点麻烦，建议保留观望，待累积更新到一定程度后再一并更新。

如果你的节点很少，那么可以更新到最新版本。

## 开始更新

### Windows 版更新

1. [前往官方网站](https://mcsmanager.com)，下载最新的压缩文件。

2. **覆盖**代码文件即可。

### Linux 版脚本更新

如果你**当初是使用的一键脚本**安装，那么你只需执行以下命令即可，一键安装脚本支持自动更新，不会损害本地数据。

执行脚本之后，不需要再做其他事情，你的 MCSManager 应该会自动到最新版本。

```bash
sudo su -c "wget -qO- https://script.mcsmanager.com/setup_cn.sh | bash"
```

### Linux 版手动更新

如果你**当初是手动安装**的 MCSManager 面板，那么一键安装脚本将不适用于你，因为这会导致安装两份程序。

你必须前往官方[发行记录](https://github.com/MCSManager/MCSManager/releases/latest)，下载最新的代码并且覆盖你的 MCSManager 所有文件。

覆盖文件之后，还需要更新依赖库，进入 `web` 和 `daemon` 目录，分别执行一次 `npm install --production` 命令来确保依赖库得到更新，否则你可能无法启动面板！

## 重置管理账号

如果你忘记了管理员密码，你可以将 `<Web 面板安装位置>/data/User` 目录移动到其他目录，接下来重启面板，这会让面板进入`面板第一次安装`的状态，你可以重新设置你的管理员账号密码，再将原先里面的 `json` 文件原封不动的移动回去即可，需要再重启一次面板。

## 完全重置面板

你只需要删除 `data` 目录，即可重置所有数据。
