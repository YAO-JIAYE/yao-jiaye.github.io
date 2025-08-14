---
title: geminicli编程工具介绍
published: 2025-07-14
description: geminicli
image: "https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813220922770.png"
tags: [github-repo]
category: AI
draft: false
---


## gemini是什么

Gemini CLI 是一个`开源 AI 代理`，将 Gemini 的强大功能直接带入您的终端。它提供轻量级访问 Gemini，让您从提示词到我们的模型拥有最直接的路径。

🎯 免费套餐：使用个人 Google 账号，每分钟 60 次请求，每天 1000 次请求

🧠 强大的 Gemini 2.5 Pro：访问 100 万 token 的上下文窗口

🔧 内置工具：谷歌搜索基础、文件操作、shell 命令、网页抓取

🔌 可扩展：支持 MCP（模型上下文协议）进行自定义集成

💻 终端优先：专为习惯使用命令行的开发者设计

🛡️ 开源：采用 Apache 2.0 许可证



⭐**安装要求**

Node.js 版本 20 或更高

macOS、Linux 或 Windows

## 安装

使用 npm 全局安装

```
npm install -g @google/gemini-cli
```

或者使用镜像源（国内）

```
npm install -g @google/gemini-cli --registry=https://registry.npmmirror.com
```

随后我们在命令行窗口输入`gemini`命令就能启动`geminicli`了

## 验证账户

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813230000081.png)

在这里我选择`google账户`登录

这里需要用到`魔法上网`,并切换`tun`模式

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813230753430.png)

最后我的账户也是授权成功了🎉

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813230644127.png)

> 失败的一种情况

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813231212170.png)

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813231238311.png)

随便创建一个项目，然后搜索`gemini for google cloud`

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/image-20250813231300957.png)

启用`gemini for google cloud`服务

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813231405610.png)

将项目ID作为环境变量配置进gemini里，然后重启gemini

## 界面介绍

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813231844455.png)

重新选择一个项目打开，我用了vscode编辑器，然后新建了终端窗口，重新运行`gemini`

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813232107171.png)

这里需要选择YES，安装cli需要的插件，主要用于vscode

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250813232310437.png)

哈哈😂，安装失败了，这样我们去vscode插件市场手动安装该插件`gemini cli companion`

随后在gemini面板里执行`/ide enable`命令，让geminicli和vscode相关联

![](https://cdn.jsdelivr.net/gh/YAO-JIAYE/my_imgs_repo@main/imgs/20250814152509236.png)

## 一些简单的命令

分析整个项目然后生成一个GEMINI.md文件，每次问问题时都会读取这个文件帮助gemini更好地回答

```
/init
```

清理上下文

```
/clear
```

使用特定模型如flash

```
gemini -m gemini-2.5-flash
```

压缩上下文

```
/compress
```

保存会话

```
/chat save 会话名
```

查看所有保存的会话

```
/chat list
```

进入某个保存的会话

```
/chat resume 会话名
```

