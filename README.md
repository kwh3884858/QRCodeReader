
# QR Code Reader

[English Version](#english-version)

由于最近有在PC上扫描二维码的需求，便希望有一个轻量化的软件能够实现简单，快捷的扫描并打开二维码所指向网址的功能．

找了半天没有合适的现成软件可用，因此花了半天写了这个项目


## 特点

- 开箱即用, 不需要额外配置

- 快速，只做一件时间，扫描二维码并打开．所截的图在剪贴板里，所以它也是个截图软件

- 安全，不需要安装，不发送任何数据


## 演示

![QRCodeReader.gif](QRCodeReader.gif)


## 使用说明

1. 启动软件

2. 点击Capture或者使用快捷键Control + Alt + D

3. 点击拖动覆盖二维码所在区域, 如果能够识别, 会启动默认浏览器打开网址.

## 依赖

屏幕截图:  [wanttobeno/Screenshot](https://github.com/wanttobeno/Screenshot)

二维码识别:  [nu-book/zxing-cpp](https://github.com/nu-book/zxing-cpp)

## 部署

本节将帮助您设置和构建QRCodeReader。

首先，项目使用Cmake作为构建工具，所以需要下载安装Cmake。

https://cmake.org/download/

目前只支持Windows，所以我将介绍如何使用Cmake GUI来构建解决方案。

在要存放项目的文件夹中打开 git bash。

输入以下代码：

1. 克隆项目：

```git clone https://github.com/kwh3884858/QRCodeReader```

2. 进入项目文件夹：

 ```cd QRCodeReader```


3. 初始化子模块库。

```git submodule update --init --recursive```

生成解决方案。

请确保所有子模块都拉入文件夹库中

4. 打开 Cmake GUI。将source code文件夹设置为项目的根目录，将birary文件夹设置为您喜欢的任何文件夹，这里我设置为Build文件夹。如果文件夹不存在，Cmake 会创建文件夹。点击Configurate, 选择您所需的编译项目, 然后点击Generate

5. 打开 Build/QRCodeReader.sln, Rebuild Solution，然后将 QRCodeReader 设置为启动项目。

6. 运行项目。


# English Version

Since there is a need to scan QR codes on a PC recently, I hope to have a lightweight software that can easily and quickly scan and open the URL pointed to by the QR code.

After looking for a long time, there is no suitable ready-made software available, so I spent half a day writing this project


## Features

- Out of the box, no additional configuration required

- Fast, only do one time, scan the QR code and open. The screenshot is in the clipboard, so it is also a screenshot software

- Safe, no installation required, no data sent


## Demo

![QRCodeReader.gif](QRCodeReader.gif)


## Instructions for use

1. Start the software

2. Click Capture or use the shortcut Control + Alt + D

3. Click and drag to cover the area where the QR code is located. If it can be recognized, the default browser will be launched to open the URL.

## dependencies

Screenshot: [wanttobeno/Screenshot](https://github.com/wanttobeno/Screenshot)

QR code recognition: [nu-book/zxing-cpp](https://github.com/nu-book/zxing-cpp)

## deploy

This section will help you set up and build QRCodeReader.

First, the project uses Cmake as a build tool, so you need to download and install Cmake.

https://cmake.org/download/

Currently only Windows platform is supported, so I'll describe how to use the Cmake GUI to build the solution.

Open git bash in the folder where you want to put the project.

Enter the following code:

1. Clone the project:

```git clone https://github.com/kwh3884858/QRCodeReader```

2. Go to the project folder:

```cd QRCodeReader```

3. Initialize the submodule library.

```git submodule update --init --recursive```

Generate a solution.

Make sure all submodules are pulled into the folder library

4. Open the Cmake GUI. Set the source code folder to the root of the project and the birary folder to whatever you like, here I set it as the Build folder. If the folder does not exist, Cmake will create the folder. Click Configure, select your desired build project, then click Generate

5. Open Build/QRCodeReader.sln, Rebuild Solution, and set QRCodeReader as the startup project.

6. Run the project.