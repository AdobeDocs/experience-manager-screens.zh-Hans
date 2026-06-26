---
title: 使用Chrome Player作为扩展
description: 了解如何将Chrome播放器安装为AEM Screens的浏览器扩展。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
TQID: https://experienceleague.adobe.com/ehBNwOmhu7ygOMHsEiD8DeGBEDFB0Asv7p8HVDteb8I
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 510
ht-degree: 0%

---

# 使用Chrome播放器作为扩展 {#using-chrome-player}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

在开发人员模式下，ChromeOS播放器可作为Chrome浏览器插件安装，而无需实际的Chrome播放器设备。

>[!CAUTION]
>
> 建议使用Chrome播放器作为扩展进行故障排除，以便快速演示、调试和解决客户问题。 请勿将此机制用于需要自助服务亭模式和中央管理的生产部署。

有关将Chrome播放器作为浏览器扩展进行安装的信息，请参阅此页面。

1. 单击[此处](https://download.macromedia.com/screens/)下载最新的Chrome播放器。

1. 解压缩并将其保存在磁盘上。

1. 打开Chrome浏览器，单击三点菜单，然后单击右上角&#x200B;**扩展**&#x200B;中的&#x200B;**更多工具**&#x200B;或直接导航到`chrome://extensions`。

1. 从右上角打开&#x200B;**开发人员**&#x200B;模式。

1. 从左上角单击&#x200B;**加载解压缩**，然后加载解压缩的Chrome播放器。

1. 如果扩展列表中有AEM Screens Chrome播放器插件，请选中该插件。

1. 打开新选项卡并单击左上角的“应用程序”图标，或直接导航到`chrome://apps`。

1. 单击&#x200B;**AEM Screens插件**，以便启动Chrome播放器。

   >[!NOTE]
   >
   > 默认情况下，播放器将以全屏模式启动。 按&#x200B;**Esc**&#x200B;退出全屏模式。


## 高级调试提示 {#advanced-debugging-tips}

1. 当播放器在本地下载内容时，您可以通过转到`http://localhost:24502`来浏览本地下载的内容。

   >[!NOTE]
   >
   > 如果上述URL不起作用，则表示未向播放器分配显示内容，或者内容未成功下载。 检查播放器配置JSON的“网络”选项卡，查看播放器是否获取了正确的详细信息以及下载中是否有任何网络问题。

1. 右键单击并检查Chrome播放器的三层。
   **调试内容**：右键单击并检查该内容以调试正在运行的内容（上下文菜单中应有一个名为“Inspect”的项）

   **调试固件**：调出管理UI，然后右键单击并检查以调试固件（播放器）代码。 （应该有一个选项来检查和检查后台页面，并模拟浏览器重新启动。）

   **调试后台页面**：调出管理员UI，然后右键单击并检查后台页面（对于http服务器等后台服务）。

## 升级播放器扩展 {#upgrading-player}

如果发布了播放器的新版本，请按照以下步骤升级播放器扩展。 您还可以按照以下说明测试升级方案：

1. 关闭任何正在运行的Chrome和播放器实例
1. 重命名包含播放器文件的旧文件夹
1. 在与旧文件夹相同的位置解压缩新的zip文件
1. 启动Chrome并导航到`chrome://extensions`
1. 选中播放器图标并单击刷新或重新加载按钮

