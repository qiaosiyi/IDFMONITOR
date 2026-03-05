# idfmonitor

A lightweight shell script that automatically detects USB serial devices and launches ESP-IDF Monitor — no manual environment setup or port guessing required.

自动检测 USB 串口设备并启动 ESP-IDF Monitor 的快捷脚本。

## 功能

- 自动加载 ESP-IDF 环境（无需手动执行 `export.sh`）
- 自动识别 `/dev/tty.usbmodem*` 设备
- 存在多个设备时，按连接时间排序并提示选择

## 前置条件

- macOS 系统
- ESP-IDF 已安装至 `~/esp/esp-idf/`

## 安装

一行命令完成下载、赋权、创建全局软链接：

```bash
curl -fsSL https://raw.githubusercontent.com/qiaosiyi/IDFMONITOR/main/idfmonitor \
  -o /usr/local/bin/idfmonitor && chmod +x /usr/local/bin/idfmonitor
```

安装完成后即可在任意目录直接使用 `idfmonitor` 命令。

如需手动安装，请clone 本repo后，赋予脚本执行权限并创建软链接：

```bash
chmod +x idfmonitor && ln -sf "$(pwd)/idfmonitor" /usr/local/bin/idfmonitor
```

## 使用方法

安装到全局后：

```bash
idfmonitor
```

### 仅一个设备时

脚本自动识别并直接启动：

```
使用端口：/dev/tty.usbmodem5AF61211261

...
...
......
```

### 多个设备

脚本列出所有候选设备（按连接时间从新到旧排列），等待手动选择：

```
找到多个 usbmodem 设备，请选择（按连接时间排序，最新的在前）：

  [1] /dev/tty.usbmodem5AF61211261  （连接时间：2026-03-03 10:25:43）
  [2] /dev/tty.usbmodem5AF61211262  （连接时间：2026-03-03 09:10:05）

请输入编号 [1-2]：
```


## 目录结构

```
idfmonitor/
├── idfmonitor   # 主脚本
└── README.md
```
