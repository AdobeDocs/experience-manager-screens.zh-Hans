---
title: AEM Screens常见问题解答
seo-title: AEM Screens常见问题解答
description: 可查看本页以获取与AEM Screens项目相关的常见问题解答。
seo-description: 可查看本页以获取与AEM Screens项目相关的常见问题解答。
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: b4f9acb68aca05ed3f6b040910742c245923dace
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 2%

---


# AEM Screens常见问题解答 {#aem-screens-faqs}

以下部分对与AEM Screens项目相关的几个常见问题解答提供了答案。

## 渠道管理 {#channel-management}

### 1.线上和线下渠道之间有何差异？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

“联机渠道”******&#x200B;将会在实时环境中显示更新的内容，而“脱机渠道”******&#x200B;则会显示缓存的内容。

### 2.如何在线制作渠道? {#how-do-i-make-a-channel-online}

选择渠道，然后从操作栏中导航到渠道属性。 在“ **渠道”选项卡下检查“开发人员模式** ”(强 **制渠道在线** )，使渠道联机。

### 3.“渠道角色”字段的用途是什么？ {#what-is-the-use-of-the-channel-role-field}

渠道角色是运行的实际渠道的抽象，这样作者可以直接专注于通用体验。 您可以将其视为一种标签，在渠道的上下文(显示或计划)中唯一标识该。

### 4.实际的渠道解决方式如何？ {#how-does-actual-channel-resolution-happen}

对 *于静态引*&#x200B;用，分辨率只遵循指定的路径。

对 *于动态引用*，一旦将渠道分配给显示屏(而非计划)，就会出现分辨率。 显示路径将成为渠道的上下文，并且解决方案如下（最高到最低优先级）:

1. 显示屏有一个与引用的渠道名称匹配的子节点
1. 显示屏有一个与引用的渠道名称匹配的同级节点
1. 显示屏的父位置具有与引用的渠道名称匹配的子节点
1. 显示屏的大父位置有一个与引用的渠道名称匹配的子节点

依此类推，直到您到达位置文件夹并立即停在该位置(因此，您不能引用渠道文件夹中的渠道，只引用位置子树中的渠道)。

## 设备注册 {#device-registration}

### 1.如果我发现终端节点（如设备入门和注册请求），我可以编写大量设备的脚本并注册这些设备。 除了将其锁定到分支Wi-Fi之外，是否还可以保护这些请求？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

当前仅可在作者实例上注册。 尽管注册服务未通过身份验证，但它只会在AEM中创建挂起的设备，实际上不会注册设备或分配任何显示屏。

要注册设备(即在AEM中为设备创建用户)，您仍需要向AEM进行身份验证，并且当前需要手动按照注册向导完成注册。 理论上，恶意用户可能创建多个挂起的设备，但如果没有AEM登录，则无法注册任何设备。

### 2.是否有一种方法通过某种身份验证将HTTPGET请求转换为HTTPPOST? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

注册请求是POST请求。

建议从会话获取设备ID，而不是作为参数传递。 这将清除服务器日志、浏览器缓存等。 它当前不是安全问题。 请注意，当服务器上没有状态更改时，将使用语义GET，当状态发生更改时，将使用POST。

### 3.是否有方法拒绝设备注册请求？ {#is-there-a-way-to-decline-a-device-registration-request}

您无法拒绝注册请求。 注册请求应在Adobe Experience ManagerWeb控制台中配置的超时后 [过期](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)。 默认情况下，此值设置为一天，并存储在内存缓存中。

## 设备监视和运行状况报告 {#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens播放器显示空白屏幕，如何进行故障诊断？ {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

请检查以下可能性以排除空白屏幕问题：

* AEM无法推送脱机内容
* 渠道没有任何内容
* 当前时间没有计划显示任何资产

### 2.如果AEM Screens播放器无法注册且其状态显示为失败，该怎么办？ {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

您需要启用Apache Sling推荐人过滤器允许为空。 这是在AEM Screens播放器和AEM Screens服务器之间优化控制协议操作所必需的。

1. 导航到 **Adobe Experience ManagerWeb控制台配置**
1. 选中 **allow.empty选项** 。
1. 单击&#x200B;**保存**。

### 3.如果注册AEM Screens播放器时，设备显示FAILURE，控制台日志显示ENAME_NOT_FOUND错误，如何进行疑难解答？ {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens服务器DNS，则可能会出现此问题。 您可以尝试使用IP地址进行连接。 要获取服务器的IP，请使用： *arp &lt;server_dns_name>*。

### 4. AMS是否建议在所有设备上实施Android监视程序？ 监视程序(Cordova)插件是否包含在APK中？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用纯Android API的跨平台Android监视程序已经是apk的一部分。 不需要任何其他软件，但根据您使用的设备，您可能需要放弃apk才能获得完整电源周期的系统权限(Powermanager api)。 如果它没有使用制造商密钥辞职，它将退出并重新启动应用程序，但不会重新启动电源。

有关如何实施Android Player的详细信息，请参阅实 [**施Android Player**](implementing-android-player.md)。

### 5.Adobe/AMS建议哪些第三方远程监视和警报工具（软件）用于监视每台设备？  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根据您对监视和警报的需求，如果设备在一段时间内未ping通知，新增功能AEM Screens通知服务会通知您。 第三方工具将取决于您的操作系统(OS)、其功能和客户的特定需求。

有关可以监视设备活动的详细信息，请参阅 [**AEM Screens通知服务**](screens-notifications-service.md)。

## AEM Screens 播放器 {#aem-screens-player}

### 1.如何将ChromeOS播放器作为Chrome浏览器插件安装？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS播放器可以在开发人员模式下作为Chrome浏览器插件安装，无需使用实际的Chrome播放器设备。 要进行安装，请按照以下步骤操作：

1. 单击 [此处](https://download.macromedia.com/screens/) ，下载最新的Chrome播放器。
1. 解压并保存到磁盘。
1. 打开Chrome浏览器，从菜 **单中** 选择“扩展”，或直接导航 ***到chrome://extensions***。
1. 从右上角 **打开** “开发人员”模式。
1. 单击左 **上角的** “Load Unpacked”（加载解压缩的Chrome Player）。
1. 检查 **AEM ScreensChrome Player** plugin(如果扩展列表中提供)。
1. 打开新选项卡，单击左上 **角的** “应用程序”图标，或直接导航到 ***chrome://apps***。
1. 单击 **AEM Screens** Plugin以启动Chrome Player。 默认情况下，播放器以全屏模式启动。 按 **Esc** 退出全屏模式。

### 2.如何对Screens播放器无法通过使用自定义错误处理程序的发布实例进行身份验证进行疑难解答？ {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

当AEM Screens播放器开始时，当播放 ***器收到404错误***，它会向/content/screens/svc.ping.json提出请求。 播放器启动身份验证请求以针对发布实例进行身份验证。 如果发布实例中有自定义错误处理程序，请确保在/content/screens/svc.ping.json上返回匿名用户的404 ***状态代码***。

### 3.如何在Android播放器中设置设备屏幕保持打开状态？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

请按照以下步骤在任何Android播放器上打开“保持清醒”:

1. 导航到Android播放器设置—>关 **于**
1. 点按内部版本号7次，以在“设置”中 **启用“开发人员** 选项 **”**
1. 导航到开发 **人员选项**
1. 启用 **保持清醒**

### 4.如何为Windows播放器启用窗口模式？{#enable-player}

Windows播放器中没有窗口模式。 始终为全屏模式。

### 5.如果AEM Screens播放器连续发送登录请求，如何进行故障诊断？{#requests-login}

请按照以下步骤对连续发送请求的AEM Screens播放器进行故障 `/content/screens/svc.json` 诊断， `/libs/granite/core/content/login.validate/j_security_check`并：

1. 当AEM Screens播放器开始时，它发出请求，当 `/content/screens/svc.json`播放器在响应中获得404状态代码时，播放器启动验证请求以针对发布实例 `/libs/granite/core/content/login.validate/j_security_check` 进行验证。 如果发布实例中有自定义错误处理程序，请确保在或上返回匿名用户的404状态 `/content/screens/svc.json` 代码 `/content/screens/svc.ping.json`。

1. 检查调度程序配置是否允许此部分中的这些 `/filters` 请求。 有关更 [多详细信息](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) ，请参阅配置屏幕过滤器。

1. 检查调度程序重写规则是否正在重写指向其他路径的任何屏幕路径。

1. 检查您的创作 `/etc/map` 或发布实 *例和屏* 幕路径是 *否匹配，并在内*`sling:match` 部重定向到其他路径。 在／中解析确切的url`system/console/jcrresolver` 有助于确定发布实 *例是否将* 这些url重写到任何其他路径。

1. 检查您是否有导致内部重写的任何Apache Sling Resource Resolver Factory配置。

## 一般疑难解答提示 {#general-troubleshooting-tips}

### 1.如何禁用Livefyre以避免A/P屏幕错误？ {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

为了避免日志错误，请禁用Livefyre:

1. ***禁用Livefyre捆绑：***

   * 导航至 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * 搜索AEM Livefyre捆绑包： `com.adobe.cq.social.cq-social-livefyre`
   * 单击停 **止**

1. ***禁用Livefyre poller:***

   * 在CRXDE Lite中，导航到 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 添加新的启用属 *性* 类型 *Boolean*
   * 将 **enabled属性设置为****false**

