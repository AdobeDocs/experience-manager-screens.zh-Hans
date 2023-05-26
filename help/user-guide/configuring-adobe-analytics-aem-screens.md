---
title: 使用AEM Screens配置Adobe Analytics
seo-title: Configuring Adobe Analytics with AEM Screens
description: 阅读本节内容，了解有关使用离线Adobe Analytics对自定义事件进行排序和发送的更多信息
seo-description: Follow this section to learn more about sequencing and sending custom events using Offline Adobe Analytics
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 7%

---

# 使用AEM Screens配置Adobe Analytics {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>此AEM Screens功能仅在安装了AEM 6.4.2 Feature Pack 2和AEM 6.3.3 Feature Pack 4时才可用。
>
>要访问这两个功能包中的任何一个，您必须联系Adobe支持部门并请求获取访问权限。 一旦您拥有权限，就可以从包共享下载它。

本节涵盖以下主题：

* **使用AEM Screens在Adobe Analytics中排序**
* **使用离线Adobe Analytics发送自定义事件**

## 使用AEM Screens在Adobe Analytics中排序 {#sequencing-in-adobe-analytics-with-aem-screens}

此 ***测序过程*** 从激活Adobe Analytics服务的数据存储服务开始。 渠道内容使用工资单发送Adobe Analytics事件，即将数据测试捕获发送到Windows I/O，并触发保持事件。 这些事件被保存到索引数据库，并进一步放入对象存储中。 管理员根据计划设置，从对象存储中剪切数据，然后进一步在块存储中传输这些数据。 连接后，它会尝试发送最大数量的数据。

### 排序图 {#sequencing-diagram}

以下顺序图说明了Adobe Analytics与AEM Screens的集成：

![analytics_chunking](assets/analytics_chunking.png)

## 使用离线Adobe Analytics发送自定义事件 {#sending-custom-events-using-offline-adobe-analytics}

下表总结了事件的标准数据模型。 其中列出了发送到Adobe Analytics的所有字段：

<table>
 <tbody>
  <tr>
   <td><strong>分区</strong></td> 
   <td><strong>属性标签</strong></td> 
   <td><strong>属性名称/密钥</strong></td> 
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
   <td>收集事件的日期时间</td> 
   <td>event.coll_dts</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>收藏集日期时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期时间（开始）</td> 
   <td>event.dts_start</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td>时间戳 — UTC</td> 
   <td>事件开始日期时间，如果不指定此时间，则将事件时间假定为服务器收到该事件的时间</td> 
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
   <td>主数据库类别</td> 
   <td>event.category</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>主要类别（桌面、移动设备、WEB、进程、SDK、服务、生态系统） — 事件类型分组 —  <strong>我们发送播放器</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子类别</td> 
   <td>event.subcategory</td> 
   <td>推荐</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>子类别 — 工作流的部分或屏幕区域等。 （最近使用的文件、CC文件、移动设备创建等。）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件/操作类型</td> 
   <td>event.type</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件类型（渲染、点击、捏合、缩放） — 主要用户操作</td> 
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
   <td>操作脱机/联机时生成了事件(true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>用户代理</td> 
   <td>event.user_agent</td> 
   <td>推荐（Web属性）</td> 
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
   <td>用户区域设置是一个基于RFC 3066的语言标记约定的字符串（例如，en-US、fr-FR或es-ES）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>设备GUID</td> 
   <td>event.device_guid</td> 
   <td>可选</td> 
   <td>字符串<br /> </td> 
   <td>UUID</td> 
   <td>标识设备GUID（例如，计算机ID或IP地址哈希+子网掩码+网络ID +用户代理） — 我们将在此处发送在注册时生成的播放器的用户名。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>计数</td> 
   <td>event.count</td> 
   <td>可选</td> 
   <td>数字</td> 
   <td> </td> 
   <td>事件发生的次数 — 我们在此处发送视频持续时间</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>价值</td> 
   <td>event.value</td> 
   <td>可选</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>事件的值（例如，设置on/off）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>AA必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>Adobe Analytics支持自定义页面名称</td> 
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
   <td><strong><em>来源/原始产品</em></strong></td> 
   <td>名称</td> 
   <td>source.name</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>应用程序名称(AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>版本</td> 
   <td>source.version</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>固件版本</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Platform</td> 
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
   <td>必需（包含例外）</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>播放器名称</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>操作系统版本</td> 
   <td>source.os_version</td> 
   <td>必需（包含例外）</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>操作系统版本</td> 
  </tr>
  <tr>
   <td><strong><em>内容</em></strong></td> 
   <td>操作</td> 
   <td>content.action</td> 
   <td>必需</td> 
   <td>字符串</td> 
   <td> </td> 
   <td>资源（包括实际播放的演绎版）的URL</td> 
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
   <td>优选遵守UUID v4的唯一ID</td> 
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
   <td>播放持续时间</td> 
  </tr>
 </tbody>
</table>
