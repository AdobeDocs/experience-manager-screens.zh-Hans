---
title: 使用Chrome Player作为扩展
seo-title: 使用Chrome Player作为扩展
description: 可查看本页以了解有关将chrome播放器作为浏览器扩展安装的信息。
seo-description: 'null'
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---


# 使用Chrome Player作为扩展{#using-chrome-player}

ChromeOS播放器可以在开发人员模式下作为Chrome Browser插件安装，无需使用实际的Chrome播放器设备。

>[!CAUTION]
>
> 建议将Chrome Player用作故障排除的扩展，以便快速演示、调试以及解决客户问题。 此机制不应用于需要自助终端模式和集中管理的生产部署。

可查看本页以了解有关将chrome播放器作为浏览器扩展安装的信息。

1. 单击[此处](https://download.macromedia.com/screens/)下载最新的Chrome Player。

1. 解压缩并保存到磁盘。

1. 打开Chrome浏览器，单击3点菜单，从右上角的&#x200B;**扩展**&#x200B;中选择&#x200B;**更多工具**&#x200B;或直接导航到`chrome://extensions`。

1. 从右上角打开&#x200B;**开发者**&#x200B;模式。

1. 单击左上角的&#x200B;**“加载未压缩的**”并加载已解压的Chrome Player。

1. 检查AEM Screens Chrome Player插件(如果在扩展列表中提供)。

1. 打开新选项卡，单击左上角的“应用程序”图标，或直接导航到`chrome://apps`。

1. 单击&#x200B;**AEM Screens Plugin**&#x200B;启动Chrome Player。
   >[!NOTE]
   >
   > 默认情况下，播放器以全屏模式启动。 按&#x200B;**esc**&#x200B;退出全屏模式。


## 高级调试提示{#advanced-debugging-tips}

1. 播放器在本地下载内容后，可以通过转到`http://localhost:24502`浏览本地下载的内容。

   >[!NOTE]
   >
   > 如果上述URL不起作用，则表示未为播放器分配显示屏或未成功下载内容。 检查播放器配置JSON的“网络”选项卡，查看播放器是否获得了正确的详细信息以及下载中的任何网络问题。

1. 您可以右键单击并检查铬黄播放器的三个图层
   **调试内容**:右键单击并检查内容以调试正在运行的内容(上下文菜单中应有一个名为“Inspect”的项目)

   **调试固件**:调出管理员UI，然后右键单击并检查以调试固件（播放器）代码（应该有一个选项来检查和检查后台页面以及模拟浏览器重新启动）

   **调试背景页**:调出管理员UI，然后右键单击并检查后台页面（对于后台服务，如http服务器）

## 升级Player扩展{#upgrading-player}

如果播放器的新版本已发布，请按照以下步骤升级播放器扩展。 您还可以按照以下说明测试升级方案：

1. 关闭任何正在运行的chrome和player实例
1. 使用播放器文件重命名旧文件夹
1. 将新zip解压缩到与旧文件夹相同的位置
1. 启动Chrome并导航到`chrome://extensions`
1. 选中播放器图标并单击刷新或重新加载按钮