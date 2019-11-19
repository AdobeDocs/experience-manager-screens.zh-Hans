---
title: 脱机渠道
seo-title: 脱机渠道
description: 'AEM Screens播放器通过利用ContentSync技术为渠道提供离线支持。 可查看本页以了解有关更新处理程序和为渠道启用脱机配置的更多信息。  '
seo-description: 'AEM Screens播放器通过利用ContentSync技术为渠道提供离线支持。 可查看本页以了解有关更新处理程序和为渠道启用脱机配置的更多信息。  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 脱机渠道 {#offline-channels}

Screens播放器通过利用 ***ContentSync技术为渠道提供离线支*** 持。

播放器使用本地http服务器来提供解压缩的内容。

将渠道配置为联机运行时 **，播放器会通过访问AEM服务器来提供渠道资源，但将渠道配置为脱机运行时 **，播放器会从本地http服务器提供渠道资源。

该流程的工作流如下：

1. 解析所需页面
1. 收集所有相关资产
1. 将所有内容打包到一个zip文件中
1. 下载zip文件并将其解压缩到本地
1. 显示内容的本地副本

## 更新处理程序 {#update-handlers}

ContentSync ****** 使用更新处理程序来分析和收集特定项目的所有必要页面和资产。 AEM Screens使用以下更新处理程序：

### 常用选项 {#common-options}

* *类型*:要使用的更新处理函数类型
* *路径*:资源路径
* *[targetRootDirectory]*:zip文件中的目标文件夹

<table>
 <tbody>
  <tr>
   <td><strong>类型</strong></td> 
   <td><strong>描述</strong></td> 
   <td><strong>选项</strong></td> 
  </tr>
  <tr>
   <td>频道</td> 
   <td>收集渠道</td> 
   <td>扩展：要收集的资源的扩展<br /> [pathSuffix="]:添加到渠道路径的后缀<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>收集指定的客户端库</td> 
   <td>[extension="]:可以是css或js，以仅收集前者，或仅收集后者</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>收集资产演绎版</td> 
   <td>[再现=[]]:要收集的演绎版列表。 默认为原始再现</td> 
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
1. 单击“清除缓存”
1. 单击“更新缓存”
1. 单击“下载完整版”
1. 解压缩zip文件
1. 在解压缩的文件夹中启动本地服务器
1. 打开开始页面并检查应用程序状态

## 为渠道启用脱机配置 {#enabling-offline-config-for-a-channel}

请按照以下步骤为渠道启用脱机配置：

1. 检查渠道内容并检查是否从AEM实例（联机）请求它。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. **导航到渠道功能板，然后单**&#x200B;击……在“渠 **道信息** ”面板中更改属性。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 导航到渠道属性，并确保在渠道选项卡下禁用了该 **复选框** 。 单击 **保存并关闭**。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   在将内容正确部署到设备之前，单击“更新脱 **机内容”**。

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   “属 **性** ”下的“ **脱机** ”状态也会相应更新。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. 检查渠道内容并检查是否从本地播放器缓存请求它。

   ![chlimage_1-26](assets/chlimage_1-26.png)

