---
title: 使用Adobe Analytics配置AEM Screens
seo-title: 使用Adobe Analytics配置AEM Screens
description: '请阅读本节内容，了解有关使用离线Adobe Analytics排序和发送自定义事件的更多信息 '
seo-description: '请阅读本节内容，了解有关使用离线Adobe Analytics排序和发送自定义事件的更多信息 '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
feature: 管理屏幕
role: Administrator, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 9%

---

# 使用AEM Screens配置Adobe Analytics {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>仅当您安装了AEM 6.4.2功能包2和AEM 6.3.3功能包4时，才提供此AEM Screens功能。
>
>要访问这些功能包中的任何一个，您必须联系Adobe支持并请求获取访问权限。 您获得权限后，就可以从“包共享”下载它。

本节涵盖以下主题：

* **Adobe Analytics与AEM Screens测序**
* **使用离线发送自定义事件Adobe Analytics**

## 在Adobe Analytics中与AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}进行排序

***排序过程***&#x200B;从激活Adobe Analytics服务的数据存储服务开始。 渠道内容通过工资单发送Adobe Analytics事件，即数据测试捕获到Windows I/O并触发逗留事件。 事件将保存到索引数据库中，并进一步放入对象存储中。 管理员根据计划设置，从对象存储中剪切数据，然后在区块存储中进一步传输数据。 连接后，会尝试发送最大数据量。

### 排序图{#sequencing-diagram}

以下顺序图介绍了Adobe Analytics与AEM Screens的集成：

![analytics_chunking](assets/analytics_chunking.png)

## 使用离线Adobe Analytics {#sending-custom-events-using-offline-adobe-analytics}发送自定义事件

下表汇总了事件的标准数据模型。 其中列出了发送到Adobe Analytics的所有字段：

<table>
 <tbody>
  <tr>
   <td><strong>区域</strong></td> 
   <td><strong>属性标签</strong></td> 
   <td><strong>属性名称/键</strong></td> 
   <td><strong>必填</strong></td> 
   <td><strong>数据类型</strong></td> 
   <td><strong>属性类型</strong><br /> </td> 
   <td><strong>描述</strong></td> 
  </tr>
  <tr>
   <td><strong><em>核心/事件</em></strong></td> 
   <td>事件GUID</td> 
   <td>event.guid</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td>UUID</td> 
   <td>标识事件实例的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件收集的日期时间</td> 
   <td>event.coll_dts</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>收集日期时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期时间（开始）</td> 
   <td>event.dts_start</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>事件开始日期时间，如果未指定此时间，则事件时间将假定为服务器收到该时间的时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期时间（结束）</td> 
   <td>event.dts_end</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>事件完成日期时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>工作流</td> 
   <td>event.workflow</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>工作流名称（屏幕）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>主要DMe类别</td> 
   <td>event.category</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>主类别（桌面、移动设备、WEB、进程、SDK、服务、生态系统） — 事件类型的分组 — <strong>我们发送播放器</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子类别</td> 
   <td>event.subcategory</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>子类别 — 工作流的部分或屏幕的区域等。 （近期文件、抄送文件、移动设备创建等。）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件/操作类型</td> 
   <td>event.type</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件类型（渲染、单击、捏合、缩放） — 主要用户操作</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子类型</td> 
   <td>event.subtype</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件子类型（创建、更新、删除、发布等）  — 用户操作的其他详细信息</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>离线</td> 
   <td>event.offline</td> 
   <td>可选</td> 
   <td>布尔型</td> 
   <td> </td> 
   <td>操作处于离线/在线状态时生成事件(true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>用户代理</td> 
   <td>event.user_agent</td> 
   <td>推荐（web属性）</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>用户代理</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>语言/区域设置</td> 
   <td>event.language</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>用户区域设置是基于RFC 3066的语言标记约定（例如，en-US、fr-FR或es-ES）的字符串</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>设备GUID</td> 
   <td>event.device_guid</td> 
   <td>可选</td> 
   <td>字符串<br /> </td> 
   <td>UUID</td> 
   <td>标识设备GUID（例如，计算机ID或IP地址+子网掩码+网络ID +用户代理的哈希） — 在此，我们将发送在注册时生成的播放器用户名。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>计数</td> 
   <td>event.count</td> 
   <td>可选</td> 
   <td>数字</td> 
   <td> </td> 
   <td>事件发生次数 — 此处我们发送视频持续时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>值</td> 
   <td>event.value</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件的值（例如，打开/关闭设置）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>AA所需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>Adobe Analytics对自定义页面名称的支持</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>Web属性或移动架构的URL — 必须包含完全限定的URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>错误代码</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>字符串</td> 
   <td> </td> 
   <td>失败代码</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>错误类型</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>字符串</td> 
   <td> </td> 
   <td>失败类型</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>错误描述</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>字符串</td> 
   <td> </td> 
   <td>失败描述<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>来源/来源产品</em></strong></td> 
   <td>名称</td> 
   <td>source.name</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>应用程序名称(AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>版本号</td> 
   <td>source.version</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>固件版本</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>平台</td> 
   <td>source.platform</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>设备</td> 
   <td>source.device</td> 
   <td>必需的例外</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>播放器名称</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>操作系统版本</td> 
   <td>source.os_version</td> 
   <td>必需的例外</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>O/S版本</td> 
  </tr>
  <tr>
   <td><strong><em>内容</em></strong></td> 
   <td>操作</td> 
   <td>content.action</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>资产的URL，包括实际播放的演绎版</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Mime类型</td> 
   <td>content.mimetype</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>内容的MIME类型</td> 
  </tr>
  <tr>
   <td><strong><em>交易</em></strong></td> 
   <td>交易编号</td> 
   <td>trn.number</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td>UUID</td> 
   <td>最好符合UUID v4的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>产品描述</td> 
   <td>trn.product</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>资产的URL（不包括演绎版）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>数量</td> 
   <td>trn.quantity</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>播放的持续时间</td> 
  </tr>
 </tbody>
</table>
