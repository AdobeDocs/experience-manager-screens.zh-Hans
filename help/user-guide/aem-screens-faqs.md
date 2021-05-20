---
title: AEM Screens常见问题解答
seo-title: AEM Screens常见问题解答
description: 可查看本页以获取有关AEM Screens项目的常见问题解答。
seo-description: 可查看本页以获取有关AEM Screens项目的常见问题解答。
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
feature: 数字标牌、内容
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 1%

---

# AEM Screens常见问题解答{#aem-screens-faqs}

以下部分对几个与AEM Screens项目相关的常见问题解答提供了答案。

## 空白屏幕问题{#blank-screen}

>[!NOTE]
>列出的强制性检查，在提出问题之前，应由主要支持或客户端支持尝试。

### 1.对于任何面向黑屏或非播放内容的客户，应采取哪些急救疑难解答步骤？{#troubleshooting-blank-screen}

* 检查渠道预览是否正常工作。
* 检查显示预览是否正常工作
* 尝试将播放器注册为系统上的浏览器扩展，使其显示到该显示屏，然后检查它是否正常工作。
* 在系统上运行播放器后，导航到`http://localhost:24502`。 检查所有内容下载是否正确。
* 检查已创建相应演绎版且正在播放正确的演绎版的资产。
* 检查任何计划内容以及时间是否正确。 检查播放器中设置的时间是否正确。
* Inspect播放器控制台会记录并检查是否存在任何错误。 右键单击并检查以查看控制台日志。 如果使用windows播放器，请按`CTRL + ALT +I`调出开发控制台以查看日志。

### 2.如何通过创建默认渠道或计划来解决AEM Screens中的灰屏问题？

要避免字段中出现空白或灰色的屏幕，请创建默认的全局渠道或计划，并将其分配给优先级最低的每个显示屏1。 如果内容更新出现问题（由于网络、播放器、服务器或复制原因），因为播放器已将此内容缓存在磁盘上，因此该内容应该可以正常播放并避免出现灰屏。

所有其他内容（如渠道或计划）的优先级将大于1，因此其他内容具有优先级，而全局渠道或计划内容（优先级为1）将仅作为回退选项播放。

## 渠道管理{#channel-management}

### 1.线上和线下渠道之间有何区别？{#what-is-the-difference-between-an-online-and-an-offline-channel}

“联机渠道”******&#x200B;将会在实时环境中显示更新的内容，而“脱机渠道”******&#x200B;则会显示缓存的内容。

### 2.如何在线创建渠道？{#how-do-i-make-a-channel-online}

选择渠道，然后从操作栏中导航到渠道属性。 选中&#x200B;**开发人员模式（强制使渠道联机）** **渠道**&#x200B;选项卡下的以使渠道联机。

### 3.渠道角色字段的用法是什么？{#what-is-the-use-of-the-channel-role-field}

渠道角色是实际运行渠道的抽象，以便作者可以直接专注于通用体验。 您可以将其视为一种标记，用于在其上下文（显示或计划）中唯一标识渠道。

### 4.如何实现实际的通道分辨率？{#how-does-actual-channel-resolution-happen}

对于&#x200B;*静态引用*，分辨率仅遵循指定的路径。

对于&#x200B;*动态引用*，在将渠道分配给显示屏（而非计划）后，会出现解析。 显示路径将成为渠道的上下文，其分辨率按以下方式（优先级从高到低）进行：

1. 显示屏有一个与引用的渠道名称匹配的子节点
1. 显示屏有一个与引用的渠道名称匹配的同级节点
1. 显示屏的父位置有一个与引用的渠道名称匹配的子节点
1. 显示屏的父级位置有一个与引用的渠道名称匹配的子节点

等等，直到您到达位置文件夹并立即停止该位置（因此，您无法引用渠道文件夹中的渠道，例如，仅引用位置子树中的渠道）。

## 设备注册 {#device-registration}

### 1.如果我发现了设备载入和注册请求等端点，我可以编写大量设备的脚本并注册这些设备。 除了将其锁定到分支Wi-Fi之外，是否还可以保护这些请求？{#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

当前只能在创作实例上注册。 虽然注册服务未经过身份验证，但它只会在AEM中创建待处理设备，而不会实际注册设备或分配任何显示屏。

要注册设备(这意味着在AEM中为设备创建用户)，您仍需要对AEM进行身份验证，并且当前需要手动按照注册向导完成注册。 从理论上讲，恶意用户可能会创建多个挂起的设备，但如果没有AEM登录，则无法注册任何设备。

### 2.是否可以通过某种身份验证形式，将HTTPGET请求转换为HTTPPOST?{#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

注册请求是POST请求。

建议从会话中获取设备ID，而不是作为参数传递。 这将清理服务器日志、浏览器缓存等。 当前不是安全问题。 请注意，当服务器上没有状态更改时，将使用语义GET，当状态更改时，将使用POST。

### 3.是否有方法拒绝设备注册请求？{#is-there-a-way-to-decline-a-device-registration-request}

您无法拒绝注册请求。 注册请求应会在[Adobe Experience Manager Web Console](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)中配置的超时后过期。 默认情况下，此值设置为一天，并存储在内存缓存中。

## 设备监控和运行状况报告{#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens播放器显示空白屏幕，如何进行故障诊断？{#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

请检查以下可能性，以解决空白屏幕问题：

* AEM无法推送离线内容
* 渠道没有任何内容
* 当前未计划显示任何资产

### 2.如果AEM Screens播放器无法注册且其状态显示为“失败”，我该怎么做？{#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

您需要启用Apache Sling反向链接过滤器允许为空。 这是在AEM Screens Player和AEM Screens服务器之间优化控制协议操作所必需的。

1. 导航到&#x200B;**Adobe Experience Manager Web控制台配置**
1. 选中&#x200B;**allow.empty**&#x200B;选项。
1. 单击&#x200B;**保存**。

### 3.如果在注册AEM Screens播放器时，设备显示失败，控制台日志显示ENAME_NOT_FOUND错误，则如何进行故障诊断？{#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens Server DNS，则可能会出现此问题。 您可以尝试使用IP地址进行连接。 要获取服务器的IP，请使用：*arp &lt;server_dns_name>*。

### 4. AMS是否建议在所有设备上实施Android监视程序？ 监视工具(Cordova)插件是否作为APK的一部分包含在内？{#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用纯Android API的跨平台Android监视程序已经是APK的一部分。 无需其他软件，但根据您使用的设备，您可能需要放弃apk才能获得完全电源周期(Powermanager api)的系统权限。 如果它没有使用制造商密钥辞职，它将退出并重新启动应用程序，但不会重新启动电源。

有关如何实施Android播放器的更多信息，请参阅&#x200B;[**实施Android播放器**](implementing-android-player.md)。

### 5.Adobe/AMS建议使用哪些第三方远程监控和警报工具（软件）来监控每台设备？ {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根据您对监控和警报的需求，新增的AEM Screens通知服务会在设备一段时间内未ping通知您。 第三方工具将取决于您的操作系统(OS)、其功能和客户的特定需求。

有关可监视设备活动的位置的更多信息，请参阅&#x200B;[**AEM Screens通知服务**](screens-notifications-service.md)。

## AEM Screens 播放器 {#aem-screens-player}

### 1.如何将ChromeOS播放器安装为Chrome浏览器插件？{#how-to-install-chromeos-player-as-chrome-browser-plugin}

在开发人员模式下，ChromeOS播放器可以作为Chrome浏览器插件安装，而无需使用实际的Chrome播放器设备。 要进行安装，请执行以下步骤：

1. 单击[此处](https://download.macromedia.com/screens/)下载最新的Chrome播放器。
1. 解压缩并将其保存在磁盘上。
1. 打开Chrome浏览器并从菜单中选择&#x200B;**扩展**，或直接导航到&#x200B;***chrome://extensions***。
1. 从右上角切换&#x200B;**开发人员模式**。
1. 单击左上角的&#x200B;**Load Unpacked** ，然后加载已解压的Chrome播放器。
1. 检查&#x200B;**AEM Screens Chrome Player**&#x200B;插件（如果扩展列表中可用）。
1. 打开新选项卡，然后单击左上角的&#x200B;**Apps**&#x200B;图标，或直接导航到&#x200B;***chrome://apps***。
1. 单击&#x200B;**AEM Screens**&#x200B;插件以启动Chrome播放器。 默认情况下，播放器以全屏模式启动。 按&#x200B;**esc**&#x200B;退出全屏模式。

### 2.如果Screens播放器无法通过使用自定义错误处理程序的发布实例进行身份验证，如何进行故障诊断？{#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

当AEM Screens播放器启动时，它会向&#x200B;***/content/screens/svc.ping.json***&#x200B;发出请求，此时播放器会收到404错误。 播放器会发起身份验证请求以针对发布实例进行身份验证。 如果发布实例中存在自定义错误处理程序，请确保在&#x200B;***/content/screens/svc.ping.json***&#x200B;上返回匿名用户的404状态代码。

### 3.如何在Android播放器中设置设备屏幕保持打开状态？{#how-to-set-the-device-screen-stay-on-in-an-android-player}

请按照以下步骤在任何Android播放器上打开保持清醒：

1. 导航到Android播放器设置 — > **关于**
1. 对内部版本号点按7次，以在&#x200B;**Settings**&#x200B;中启用&#x200B;**开发人员选项**
1. 导航到&#x200B;**开发人员选项**
1. 启用&#x200B;**保持清醒**

### 4.如何为Windows播放器启用窗口模式？{#enable-player}

Windows播放器中没有窗口模式。 始终为全屏模式。

### 5.如何对AEM Screens播放器是否持续发送登录请求进行故障诊断？{#requests-login}

按照以下步骤对连续向`/content/screens/svc.json`和`/libs/granite/core/content/login.validate/j_security_check`发送请求的AEM Screens播放器进行故障诊断：

1. AEM Screens播放器启动时，会请求`/content/screens/svc.json`。 当播放器在响应中获取404状态代码时，它会针对&#x200B;*publish*&#x200B;实例使用`/libs/granite/core/content/login.validate/j_security_check`发起身份验证请求。 如果&#x200B;*publish*&#x200B;实例中存在自定义错误处理程序，请确保在`/content/screens/svc.json`或`/content/screens/svc.ping.json`上返回匿名用户的404状态代码。

1. 检查您的调度程序配置是否允许在`/filters`中发送这些请求。

   有关更多详细信息，请参阅[配置Screens过滤器](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters)。

1. 检查调度程序重写规则是否正在将任何屏幕路径重写为其他路径。

1. 检查您在&#x200B;*author*&#x200B;或&#x200B;*publish*&#x200B;实例和屏幕上是否有`/etc/map`规则，这些规则与`sling:match`的路径匹配，并在内部重定向到其他路径。 解析`/system/console/jcrresolver`中的确切URL有助于确定&#x200B;*publish*&#x200B;实例是否正在将这些URL重写为任何其他路径。

1. 检查Apache Sling资源解析程序工厂配置是否导致内部重写。

### 6.如何从播放器API获取显示器和设备的详细信息？

您可以通过以下方式获取显示屏和设备的详细信息：

* **内部JS API**
* **ContextHub存储**:在中定义了三个ContextHub存储 `/libs/screens/clientlibs/contexthub` 区，用于显示渠道、设备和显示信息。

   请按照以下步骤使用这些ContentHub存储值：

   * 编辑渠道属性，并在个性化选项卡中将ContextHub路径设置为值（如上所述）
   * 在渠道JS中，您可以使用：

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## 一般故障诊断提示{#general-troubleshooting-tips}

### 1.如何禁用Livefyre以避免A/P屏幕错误？{#how-to-disable-livefyre-to-avoid-a-p-screens-error}

为了避免出现日志错误，请禁用Livefyre :

1. ***禁用Livefyre包：***

   * 导航至 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * 搜索AEM Livefyre包：`com.adobe.cq.social.cq-social-livefyre`
   * 单击&#x200B;**Stop**

1. ***禁用Livefyre poller:***

   * 在CRXDE Lite中，导航到`/etc/importers/polling/livefyre-poller/jcr:content`
   * 添加新属性&#x200B;*enabled*&#x200B;类型&#x200B;*Boolean*
   * 将&#x200B;**enabled属性**&#x200B;设置为&#x200B;**false**

### 2.如何添加Oak索引信息？{#add-oak-index-info}

AEM Screens会为产品使用的查询创建索引定义。
如果`error.log`中存在任何&#x200B;*查询遍历警告*，请为查询创建自定义索引。 有关更多详细信息，请参阅[配置索引](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) 。

您还可以在[Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html)上引用其他资源。
