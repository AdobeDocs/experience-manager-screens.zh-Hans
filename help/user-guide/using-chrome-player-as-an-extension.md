---
title: 将Chrome播放器用作扩展
description: 了解如何将Chrome播放器安装为AEM Screens的浏览器扩展。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# 将Chrome播放器用作扩展 {#using-chrome-player}

在开发人员模式下，ChromeOS播放器可作为Chrome浏览器插件安装，而无需实际的Chrome播放器设备。

>[!CAUTION]
>
> 建议使用Chrome播放器作为扩展进行故障排除，以便快速演示、调试和解决客户问题。 请勿将此机制用于需要自助服务亭模式和中央管理的生产部署。

有关将Chrome播放器作为浏览器扩展进行安装的信息，请参阅此页面。

1. 单击 [此处](https://download.macromedia.com/screens/) 以下载最新的Chrome播放器。

1. 解压缩并将其保存在磁盘上。

1. 打开Chrome浏览器，单击3个圆点菜单，然后单击 **更多工具** 从 **扩展** 或直接导航到 `chrome://extensions`.

1. 打开 **开发人员** 模式。

1. 单击 **加载已解压缩** 从左上角，加载解压的Chrome播放器。

1. 如果扩展列表中有AEM Screens Chrome播放器插件，请选中该插件。

1. 打开新选项卡，然后单击左上角的“应用程序”图标，或直接导航到 `chrome://apps`.

1. 单击 **AEM Screens插件** 以便启动Chrome播放器。

   >[!NOTE]
   >
   > 默认情况下，播放器将以全屏模式启动。 按 **Esc** 退出全屏模式。


## 高级调试提示 {#advanced-debugging-tips}

1. 当播放器在本地下载内容时，您可以通过转到 `http://localhost:24502`.

   >[!NOTE]
   >
   > 如果上述URL不起作用，则表示未向播放器分配显示内容，或者内容未成功下载。 检查播放器配置JSON的“网络”选项卡，查看播放器是否获取了正确的详细信息以及下载中是否有任何网络问题。

1. 右键单击并检查Chrome播放器的三层。
   **调试内容**：右键单击并检查内容以调试正在运行的内容(上下文菜单中应有一个名为“Inspect”的项目)

   **调试固件**：调出管理员UI，然后右键单击并检查以调试固件（播放器）代码。 （应该有一个选项来检查和检查后台页面，并模拟浏览器重新启动。）

   **调试后台页面**：调出管理员UI，然后右键单击并检查后台页面（对于后台服务，如http服务器）。

## 升级播放器扩展 {#upgrading-player}

如果发布了播放器的新版本，请按照以下步骤升级播放器扩展。 您还可以按照以下说明测试升级方案：

1. 关闭任何正在运行的chrome和播放器实例
1. 重命名包含播放器文件的旧文件夹
1. 在与旧文件夹相同的位置解压缩新的zip文件
1. 启动Chrome并导航到 `chrome://extensions`
1. 选中播放器图标并单击刷新或重新加载按钮
