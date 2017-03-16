# 入门
在开始你的第一个 ReactVR 项目之前, 你需要安装一些依赖去构建和管理你的 ReactVR 应用：Node.js 和 React VR CLI.

## 安装 Node.js
如果你已经安装了 Node.js, 请确保它至少是 4.0 版本.
- Mac: 在 Mac 上, 我们推荐通过 [Homebrew](http://brew.sh/) 来安装.
- Windows: 从[nodejs.org 下载页面](https://nodejs.org/en/download/)获取 Windows 版安装器.
- Linux: 去 [nodejs.org 包管理页面](https://nodejs.org/en/download/package-manager/) 寻找你所使用 linux 发行版的详细说明.

## 运行示例
开始之前，从 Oculus 下载 [React VR Prerelease.zip ], 为了运行示例应用, 你必须先通过 NPM 安装一些依赖包.
1. 打开终端或者命令行窗口.
2. 进入到 React VR Preelease 预览文件夹.
3. 输入:
> npm install
4. 等待 npm 完成下载和安装软件.
5. 启动服务. 输入:
> npm start
6. 如果你在 Windows 上, 当你被要求启用防火墙例外时请启用.
7. 启动服务后, 用你的浏览器打开 [http://localhost:8081/Samples](http://localhost:8081/Samples) 查看示例

## 创建你的第一个项目
我们可以使用 ReactVR 命令行工具生成一个叫做WelcomeToVR 的新项目. 它会创建一个新的目录，包含了 ReactVR 项目的骨架以及所有必须的额外依赖.
1. 如果你还在终端窗口运行 npm, 按下 `CTRL+C` 结束它.
2. 进入你想放新项目的目录.
3. 安装 ReactVR 命令行工具. 输入:
> npm install -g react-vr-cli
4. 使用 ReactVR 命令行工具在`WelcomeToVR`文件夹下创建一个新的应用并安装依赖. 输入:
> react-vr init WelcomeToVR
5. 切换到你创建的 WelcomeToVR 目录下.
6. 使用开始命令初始化你的本地服务. 输入:
> npm start
7. 用浏览器打开 [http://localhost:8081/vr/index.html](http://localhost:8081/vr/index.html), 你会看到类似下图的内容
![](https://facebookincubator.github.io/react-vr/img/hellovr.jpg)

## Hello!
在浏览器中点击并拖动整个世界, 或在移动设备上打开它以查看更多内容.

如果你在使用支持 WebVR 的浏览器, 比如 [the Carmel Developer Preview browser from Oculus](https://www.oculus.com/experiences/gear-vr/1290985657630933/), 你应该可以戴上耳机探索完整的 VR 世界. 想获取更多支持VR 的浏览器的信息, 请关注 [VR Browsers](https://facebookincubator.github.io/react-vr/docs/vrbrowsers.html) 主题

我们的下个主题是如何将这个场景带入生活
