---
title: 使用Chrome播放器作为扩展
seo-title: 使用Chrome播放器作为扩展
description: 可查看本页以了解有关将Chrome播放器作为浏览器扩展进行安装的信息。
seo-description: 'null'
feature: 管理屏幕
role: Administrator
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 使用Chrome播放器作为扩展{#using-chrome-player}

在开发人员模式下，ChromeOS播放器可以作为Chrome浏览器插件安装，而无需使用实际的Chrome播放器设备。

>[!CAUTION]
>
> 建议将Chrome Player用作疑难解答扩展，以便快速演示、调试以及对客户问题进行疑难解答。 不应将此机制用于需要kiosk模式和中央管理的生产部署。

可查看本页以了解有关将Chrome播放器作为浏览器扩展进行安装的信息。

1. 单击[此处](https://download.macromedia.com/screens/)下载最新的Chrome播放器。

1. 解压缩并将其保存在磁盘上。

1. 打开Chrome浏览器，单击3个圆点菜单，然后从右上角的&#x200B;**Extensions**&#x200B;中选择&#x200B;**更多工具**&#x200B;或直接导航到`chrome://extensions`。

1. 从右上角切换&#x200B;**开发人员**&#x200B;模式。

1. 单击左上角的&#x200B;**Load Unpacked** ，然后加载已解压的Chrome播放器。

1. 检查AEM Screens Chrome Player插件（如果扩展列表中可用）。

1. 打开新选项卡，然后单击左上角的应用程序图标，或直接导航到`chrome://apps`。

1. 单击&#x200B;**AEM Screens插件**&#x200B;以启动Chrome播放器。
   >[!NOTE]
   >
   > 默认情况下，播放器以全屏模式启动。 按&#x200B;**esc**&#x200B;退出全屏模式。


## 高级调试提示{#advanced-debugging-tips}

1. 播放器在本地下载内容后，您可以通过转到`http://localhost:24502`浏览本地下载的内容。

   >[!NOTE]
   >
   > 如果上述URL不起作用，则表示未为播放器分配显示屏或内容未成功下载。 检查播放器配置JSON的网络选项卡，以查看播放器是否获取了正确的详细信息以及下载中是否存在任何网络问题。

1. 您可以右键单击并检查Chrome播放器的三个层
   **调试内容**:右键单击并检查内容以调试正在运行的内容(上下文菜单中应该有一个名为“Inspect”的项目)

   **调试固件**:调出管理员UI，然后右键单击并检查以调试固件（播放器）代码（应该有一个选项来检查和检查后台页面以及模拟浏览器重新启动）

   **调试后台页面**:调出管理员UI，然后右键单击并检查后台页面（对于后台服务，如http服务器）

## 升级播放器扩展{#upgrading-player}

如果发布了播放器的新版本，请按照以下步骤升级播放器扩展。 您还可以按照以下说明来测试升级方案：

1. 关闭任何正在运行的Chrome和播放器实例
1. 使用播放器文件重命名旧文件夹
1. 在与旧文件夹相同的位置解压新zip文件
1. 启动Chrome并导航到`chrome://extensions`
1. 选中播放器图标，然后单击刷新或重新加载按钮
