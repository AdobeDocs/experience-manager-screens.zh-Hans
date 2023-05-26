---
title: 脱机渠道
seo-title: Offline Channels
description: AEM Screens播放器利用ContentSync技术为渠道提供离线支持。 阅读本页内容，了解有关更新处理程序和为渠道启用脱机配置的更多信息。
seo-description: The AEM Screens player provides offline support for channels by leveraging the ContentSync technology. Follow this page to learn more about update handlers and enabling offline configuration for a channel.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 1%

---

# 脱机渠道 {#offline-channels}

Screens播放器利用 ***ContentSync*** 技术。

播放器使用本地http服务器来提供解压缩的内容。

将渠道配置为运行时 *在线*，播放器通过访问AEM服务器来提供渠道资源，但渠道配置为运行时 *离线*，播放器会从本地http服务器提供渠道资源。

该进程的工作流如下所示：

1. 解析所需页面
1. 收集所有相关资源
1. 将所有内容打包到zip文件中
1. 下载zip文件并将其解压缩到本地
1. 显示内容的本地副本

## 更新处理程序 {#update-handlers}

此 ***ContentSync*** 使用更新处理程序解析和收集特定项目的所有必要页面和资产。 AEM Screens使用以下更新处理程序：

### 常用选项 {#common-options}

* *type*：要使用的更新处理程序类型
* *路径*：资源的路径
* *[targetRootDirectory]*：zip文件中的target文件夹

<table>
 <tbody>
  <tr>
   <td><strong>类型</strong></td> 
   <td><strong>描述</strong></td> 
   <td><strong>选项</strong></td> 
  </tr>
  <tr>
   <td>渠道</td> 
   <td>收集渠道</td> 
   <td>扩展：要收集的资源的扩展<br /> [pathSuffix="]：要添加到渠道路径的后缀<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>收集指定的客户端库</td> 
   <td>[extension="]：可以是css或js，以仅收集前一个或仅收集后一个</td> 
  </tr>
  <tr>
   <td>资源趋势</td> 
   <td>收集资源演绎版</td> 
   <td>[renditions=[]]：要收集的演绎版列表。 默认为原始演绎版</td> 
  </tr>
  <tr>
   <td>复制</td> 
   <td>从路径复制指定的结构</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### 测试ContentSync配置 {#testing-contentsync-configuration}

请按照以下步骤测试ContentSync配置：

1. 打开 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 在列表中选择您的配置
1. 单击清除缓存
1. 单击更新缓存
1. 单击Download Full
1. 解压缩zip文件
1. 在提取的文件夹中启动本地服务器
1. 打开您的起始页并检查您的应用程序状态

## 启用渠道的脱机配置 {#enabling-offline-config-for-a-channel}

按照以下步骤启用渠道的脱机配置：

1. Inspect渠道内容，并检查是否从AEM实例（联机）请求该内容。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 导航到渠道仪表板并单击 **...** 在 **渠道信息** 用于更改属性的面板。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 导航到渠道属性，并确保在 **渠道** 选项卡。 单击“**保存并关闭**”。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   在将内容正确部署到设备之前，请单击 **更新离线内容**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   此 **离线** 状态在 **属性** 也会相应地更新。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect渠道内容，并检查是否从本地播放器缓存中请求该内容。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>要了解有关自定义离线资源处理程序的模板以及中的最低要求的更多信息，请参阅 `pom.xml` 有关特定项目，请参阅 [自定义处理程序的模板](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) 在 **开发AEM Screens的自定义组件**.
