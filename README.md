# Shimo VPN

一款 Mac 系统的 VPN 工具，支持 PPTP 协议。

## 背景

MacOS 10.15+ 版本以后系统删除了对PPTP的支持，导致 Shimo 失效，无法使用 PPTP 方式连接 VPN。

## 相关文件

shimo 软件：[Shimo_4.1.5.1_xclient.info.dmg](./Shimo_4.1.5.1_xclient.info.dmg) ，解压密码：xclient.info

PPTP 文件包：[PPTP.zip](./PPTP.zip)

## 步骤

### 1、关闭系统完整性保护（System Intregrity Protection，SIP）

- 重启电脑，按住 `Command+R` (直到出现苹果标志)进入 Recovery Mode (恢复模式)
- 左上角菜单里找到`实用工具` -> `终端`
- 输入 `$ csrutil disable` 回车
- 重启 Mac 即可
- 如果想重新启动 SIP 机制重复上述步骤改用 `$ csrutil enable` 即可

### 2、执行以下命令重新加载 Finder

```bash
 sudo mount -uw /&& killall Finder
```

### 3、依次新增、替换文件

- /usr/local/bin/pptp （新增）

- /System/Library/Extensions/PPTP.ppp （新增）

- /System/Library/Extensions/PPP.kext （替换，注意备份原文件）

### 4、执行以下命令授权文件

```bash
sudo chmod -R 755 /System/Library/Extensions
sudo chown -R root:wheel /System/Library/Extensions
```

### 5、打开 Shimo，添加配置文件，连接使用

