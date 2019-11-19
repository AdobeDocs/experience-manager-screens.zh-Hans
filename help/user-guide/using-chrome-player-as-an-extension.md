---
title: 使用Chrome Player作为扩展
seo-title: 使用Chrome Player作为扩展
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 使用Chrome Player作为扩展 {#using-chrome-player}

ChromeOS播放器可以在开发人员模式下作为Chrome浏览器插件安装，无需实际的Chrome播放器设备。

>[!CAUTION]
>
> 建议将Chrome Player用作故障排除的扩展，以快速演示、调试以及解决客户问题。 这种机制不应用于需要自助终端模式和集中管理的生产部署。

可查看本页以了解有关将Chrome播放器作为浏览器扩展安装的信息。

1. 单击此处下载最新的Chrome Player。

1. 解压缩并将其保存到磁盘上。

1. 打开Chrome浏览器，单击3点菜单，从右上角的“扩展”中 **选择** “更多工具” **，或直接导航到**`chrome://extensions`。

1. 从右上角 **打开** “开发人员”模式。

1. 单击左 **上角的“Load Unpacked** ”（加载解压缩的Chrome Player）。

1. 检查AEM Screens Chrome Player插件（如果在扩展列表中可用）。

1. 打开新选项卡，单击左上角的“应用程序”图标，或直接导航到 `chrome://apps`。

1. 单击“ **AEM Screens插件** ”以启动Chrome Player。
   >[!NOTE]
   >
   > 默认情况下，播放器以全屏模式启动。 按 **Esc** 退出全屏模式。


## 高级调试提示 {#advanced-debugging-tips}

1. 播放器在本地下载内容后，您可以通过转到浏览本地下载的内容 `http://localhost:24502`。

   >[!NOTE]
   >
   > 如果上述URL无效，则表示未为播放器分配显示屏或内容未成功下载。 检查播放器配置JSON的网络选项卡，查看播放器是否获得了正确的详细信息以及下载中的任何网络问题。

1. 您可以右键单击并检查铬黄播放器的三个图层
   **调试内容**:右键单击并检查内容以调试正在运行的内容（上下文菜单中应该有一个名为“检查”的项目）

   **调试固件**:调出管理员UI，然后右键单击并检查以调试固件（播放器）代码（应该有一个选项用于检查和检查后台页面以及模拟浏览器重新启动）

   **调试背景页**:调出管理员UI，然后右键单击并检查后台页面（对于后台服务，如http服务器）

## 升级Player扩展 {#upgrading-player}

如果发布了播放器的新版本，请按照以下步骤升级播放器扩展。 您还可以按照以下说明测试升级方案：

1. 关闭任何正在运行的铬黄和播放器实例
1. 使用播放器文件重命名旧文件夹
1. 将新的zip解压缩到与旧文件夹相同的位置
1. 启动Chrome并导航到 `chrome://extensions`
1. 选中播放器图标，然后单击刷新或重新加载按钮