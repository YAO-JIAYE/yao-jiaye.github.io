---
title: linux命令_for_Arch
published: 2025-08-23
description: linux命令_for_Arch
image: "https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/%E6%88%AA%E5%9B%BE%202025-08-23%2017-20-09.png"
tags: [linux]
category: [linux]
draft: false
---

### **休眠**

```
systemctl hibernate
```

### **pacman**

```bash
sudo pacman -S package_name # 安装软件包
pacman -Ss # 在同步数据库中搜索包，包括包的名称和描述
sudo pacman -Syu # 升级系统。 -y:标记刷新、-yy：标记强制刷新、-u：标记升级动作（一般使用 -Syu 即可）
sudo pacman -Rns package_name # 删除软件包，及其所有没有被其他已安装软件包使用的依赖包
sudo pacman -R package_name # 删除软件包，保留其全部已经安装的依赖关系
pacman -Qi package_name # 检查已安装包的相关信息。-Q：查询本地软件包数据库
pacman -Qdt # 找出孤立包。-d：标记依赖包、-t：标记不需要的包、-dt：合并标记孤立包
sudo pacman -Rns $(pacman -Qtdq) # 删除孤立包
sudo pacman -Fy # 更新命令查询文件列表数据库
pacman -F some_command # 当不知道某个命令属于哪个包时，用来在远程软件包中查询某个命令属于哪个包（即使没有安装）
pactree package_name # 查看一个包的依赖树
```

### **yay**

```bash
yay # 等同于 yay -Syu
yay package_name # 等同于 yay -Ss package_name && yay -S package_name
yay -Ps # 打印系统统计信息
yay -Yc # 清理不需要的依赖
```

### **vim**

```bash
# Vim 常用命令速查表

## 模式切换
- `i`  插入模式（光标前）
- `a`  插入模式（光标后）
- `o`  新行插入模式
- `Esc` 返回普通模式
- `v`  可视模式
- `:`  命令模式

## 文件操作
- `:w`      保存
- `:q`      退出
- `:wq`     保存并退出
- `:q!`     强制退出（不保存）
- `:w newfile`  另存为
- `:e filename` 打开文件

## 光标移动
- `h` 左移
- `l` 右移
- `0` 行首
- `^` 行首第一个非空字符
- `$` 行尾
- `gg` 文件开头
- `G` 文件结尾
- `:n` 跳到第 n 行
- `Ctrl+d` 下翻半屏
- `Ctrl+u` 上翻半屏

## 删除 / 剪切 / 复制 / 粘贴
- `x` 删除光标字符
- `dd` 删除整行
- `yy` 复制整行
- `p`  粘贴到光标后
- `P`  粘贴到光标前
- `d$` 删除到行尾
- `d^` 删除到行首
- `dG` 删除到文件末尾
- `y$` 复制到行尾
- `y^` 复制到行首

## 撤销 / 恢复
- `u` 撤销
- `Ctrl+r` 重做

## 搜索 / 替换
- `/keyword`  向下搜索
- `?keyword`  向上搜索
- `n` 下一个匹配
- `N` 上一个匹配
- `:%s/old/new/g`  全文替换
- `:n,m s/old/new/g` 指定范围替换

## 多行操作
- `V` 选择整行
- `>>` 向右缩进
- `<<` 向左缩进

## 分屏
- `:sp filename`  水平分屏
- `:vsp filename` 垂直分屏
- `Ctrl+w w` 切换分屏
- `Ctrl+w q` 关闭当前分屏

```

### **systemctl**

```basic
systemctl start dhcpcd # 启动服务
systemctl stop dhcpcd # 停止服务
systemctl restart dhcpcd # 重启服务
systemctl reload dhcpcd # 重新加载服务以及它的配置文件
systemctl status dhcpcd # 查看服务状态
systemctl enable dhcpcd # 设置开机启动服务
systemctl enable --now dhcpcd # 设置服务为开机启动并立即启动这个单元
systemctl disable dhcpcd # 取消开机自动启动
systemctl daemon-reload dhcpcd # 重新载入 systemd 配置。扫描新增或变更的服务单元、不会重新加载变更的配置
```

### **解压缩**

```bash
# Linux 常用文件压缩与解压缩命令

## 1. tar（最常用，支持打包 + 压缩）
# 打包压缩（tar.gz）
tar -czvf archive.tar.gz file_or_dir
# 解压 tar.gz
tar -xzvf archive.tar.gz

# 打包压缩（tar.bz2）
tar -cjvf archive.tar.bz2 file_or_dir
# 解压 tar.bz2
tar -xjvf archive.tar.bz2

# 打包压缩（tar.xz）
tar -cJvf archive.tar.xz file_or_dir
# 解压 tar.xz
tar -xJvf archive.tar.xz

# 参数说明：
# c = create 创建
# x = extract 解压
# z = gzip 压缩
# j = bzip2 压缩
# J = xz 压缩
# v = verbose 显示过程
# f = file 指定文件

---

## 2. gzip / gunzip（只压缩单个文件，不打包）
# 压缩
gzip filename
# 解压
gunzip filename.gz

---

## 3. bzip2 / bunzip2（高压缩比，单文件）
# 压缩
bzip2 filename
# 解压
bunzip2 filename.bz2

---

## 4. xz / unxz（更高压缩比）
# 压缩
xz filename
# 解压
unxz filename.xz

---

## 5. zip / unzip（跨平台常用）
# 压缩
zip archive.zip file1 file2 dir/
# 解压
unzip archive.zip

---

## 6. 7z（7-Zip 格式，超高压缩比）
# 压缩
7z a archive.7z file_or_dir
# 解压
7z x archive.7z

# 安装（Arch Linux）
sudo pacman -S p7zip

---

## 7. rar（需安装 unrar）
# 压缩（需 rar 工具）
rar a archive.rar file_or_dir
# 解压
unrar x archive.rar

# 安装（Arch Linux）
sudo pacman -S unrar

```

1. 安装 Unarchiver：（避免win压缩包乱码）

```
sudo pacman -S unarchiver
```

2. 解压压缩包：

```
unar xxx.zip
```

### df 命令

使用 `df` 命令即可显示目前在 Linux 系统上的文件系统对应的磁盘空间使用情况统计：

```
df -h # 以人类可读格式显示
```

### 磁盘空间清理

`pacman`软件包管理器会将所有下载的软件包存储在`/var/cache/pacman/pkg/`目录下，这些旧的或已卸载的包会占用空间。安装paccache

```bash
sudo pacman -S pacman-contrib
```

```bash
sudo pacman -Rns $(pacman -Qtdq) # 如上文所述，删除孤立软件包（常用）
sudo pacman -Sc # 删除当前未安装的所有缓存包和未使用的同步数据库（可选）
sudo pacman -Scc # 从缓存中删除所有文件，这是最激进的方法，不会在缓存文件夹中留下任何内容（一般不使用）
paccache -r # 删除已安装和未安装包的所有缓存版本，但最近 3 个版本除外
paccache -ruk0 # 删除所有未安装的软件包的缓存
```

如果使用了 yay 来安装 AUR 中的软件包的话，可以选择清理 yay 的缓存目录：

```bash
rm -rf ~/.cache/yay
```

**清理用户目录缓存**

使用`du -sh ~/.cache`可以查看`~/.cache`目录的大小

使用 `BleachBit` 等工具

安装BleachBit：`sudo pacman -S bleachbit`

**手动清理系统日志**

Journald可能积累大量日志，占用大量空间。修改journald.conf

```bash
sudo nano /etc/systemd/journald.conf
```

```bash
SystemMaxUse=16M  # 将日志最大占用的空间限制在16MB
```

```bash
sudo systemctl restart systemd-journald
```

### Timeshift 快照恢复

**若能够进入桌面环境**

直接打开 Timeshift，选择快照后根据提示还原即可

**若无法进入桌面环境**

1. 通过 `Ctrl` + `Alt` + `F2 ~ F6` 进入 tty 终端
2. 使用快照还原系统：

```bash
sudo timeshift --list # 获取快照列表
sudo timeshift --restore --snapshot '20XX-XX-XX_XX-XX-XX' --skip-grub # 选择一个快照进行还原，并跳过 GRUB 安装，一般来说 GRUB 不需要重新安装
```

**若无法进入系统**

使用` arch 安装盘`请连接网络和配置好源后安装` Timeshift`，然后通过命令行方式还原

### rsync 命令

```bash
# 上传本地目录到远程服务器
rsync -avz /local/path user@remote:/remote/path

# 下载远程目录到本地
rsync -avz user@remote:/remote/path /local/path
```

