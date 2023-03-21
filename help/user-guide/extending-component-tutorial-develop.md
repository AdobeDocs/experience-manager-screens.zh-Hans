---
title: 扩展AEM Screens组件
seo-title: Extending an AEM Screens Component
description: 以下教程将演示扩展开箱即用AEM Screens组件的步骤和最佳实践。 图像组件经过扩展，可添加可创作的文本叠加。
seo-description: The following tutorial walks through the steps and best practices for extending out of the box AEM Screens components. The Image component is extended to add an authorable text overlay.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: e316614f-2d40-4b62-a1e5-f30817def742
source-git-commit: 29116a15d5486b2c446cae0d092c4d4b802fe9e7
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 2%

---

# 扩展AEM Screens组件 {#extending-an-aem-screens-component}

以下教程将演示扩展开箱即用AEM Screens组件的步骤和最佳实践。 图像组件经过扩展，可添加可创作的文本叠加。

## 概述 {#overview}

本教程面向不熟悉AEM Screens的开发人员。 在本教程中，扩展了Screens图像组件以创建海报组件。 标题、描述和徽标叠加在图像顶部，以在序列渠道中创建引人入胜的体验。

>[!NOTE]
>
>在开始本教程之前，建议您先完成本教程： [为AEM Screens开发自定义组件](developing-custom-component-tutorial-develop.md).

![自定义海报组件](assets/2018-05-07_at_4_09pm.png)

自定义海报组件是通过扩展图像组件来创建的。

## 前提条件 {#prerequisites}

要完成本教程，您需要满足以下条件：

1. AEM 6.5 +最新Screens功能包
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本地开发环境

使用CRXDE-Lite可执行教程步骤和屏幕截图。 [Eclipse](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/aem-eclipse.html) 或 [IntelliJ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/ht-intellij.html) IDE还可用于完成本教程。 有关使用IDE以 [可在此处找到使用AEM进行开发](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

## 项目设置 {#project-setup}

Screens项目的源代码通常作为多模块Maven项目进行管理。 为加快教程进度，已使用 [AEM项目原型13](https://github.com/adobe/aem-project-archetype). 有关 [可在此处找到使用Maven AEM项目原型创建项目](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

1. 使用 **CRX包管理** `http://localhost:4502/crx/packmgr/index.jsp)r:`

[获取文件](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [获取文件](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（可选）** 如果使用Eclipse或其他IDE，请下载以下源包。 使用Maven命令将项目部署到本地AEM实例：

   **`mvn -PautoInstallPackage clean install`**

   SRC启动屏幕We.Retail运行项目

[获取文件](assets/start-poster-screens-weretail-run.zip)

1. 在 **CRX包管理器** `http://localhost:4502/crx/packmgr/index.jsp` 安装了以下两个包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens We.Retail运行Ui.Apps和Ui.Content包，这些包通过CRX包管理器安装](assets/crx-packages.png)

   Screens We.Retail运行Ui.Apps和Ui.Content包，这些包通过CRX包管理器安装

## 创建海报组件 {#poster-cmp}

海报组件可扩展现成的屏幕图像组件。 一种吊具， `sling:resourceSuperType`，用于继承图像组件的核心功能，而无需复制并粘贴。 有关 [Sling请求处理可在此处找到。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/the-basics.html)

海报组件在预览/生产模式下以全屏呈现。 在编辑模式下，请务必以不同方式呈现组件，以便于创作序列渠道。

1. 在 **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` 在 `/apps/weretail-run/components/content`创建 `cq:Component` 已命名 `poster`.

   将以下属性添加到 `poster` 组件：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![/apps/weretail-run/components/content/poster的属性](assets/poster.png)

   /apps/weretail-run/components/content/poster的属性

   通过设置 `sling:resourceSuperType`属性等于 `screens/core/components/content/image` 海报组件可有效地继承图像组件的所有功能。 下面找到的对等节点和文件 `screens/core/components/content/image` 可以在 `poster` 组件，以覆盖和扩展功能。

1. 复制 `cq:editConfig` 节点下方 `/libs/screens/core/components/content/image.`粘贴 `cq:editConfig` 在 `/apps/weretail-run/components/content/poster` 组件。

   在 `cq:editConfig/cq:dropTargets/image/parameters` 节点更新 `sling:resourceType` 属性等于 `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   cq:editConfig的XML表示形式如下所示：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. 复制WCM Foundation `image` 对话框 `poster` 组件。

   最简单的方法是从现有对话框开始，然后进行修改。

   1. 从以下位置复制对话框： `/libs/wcm/foundation/components/image/cq:dialog`
   1. 在下方粘贴对话框 `/apps/weretail-run/components/content/poster`

   ![将对话框从/libs/wcm/foundation/components/image/cq:dialog复制到/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   将对话框从/libs/wcm/foundation/components/image/cq:dialog复制到/apps/weretail-run/components/content/poster

   屏幕 `image` 组件是WCM Foundation的超级类型。 `image` 组件。 因此， `poster` 组件从两者中继承功能。 海报组件的对话框由屏幕和基础对话框的组合组成。 的功能 **Sling资源合并器** 用于隐藏从超类型组件继承的不相关对话框字段和选项卡。

1. 更新下方的cq:dialog `/apps/weretail-run/components/content/poster` 以下更改以XML表示：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   资产 `sling:hideChildren`= `"[linkURL,size]`“ ” `items` 节点来确保 **linkURL** 和 **大小** 字段。 仅从海报对话框中删除这些节点是不够的。 资产 `sling:hideResource="{Boolean}true"` 在“辅助功能”选项卡中，用于隐藏整个选项卡。

   对话框中添加了两个选择字段，以便作者控制标题和描述的文本位置和颜色。

   ![海报 — 最终对话框结构](assets/2018-05-03_at_4_49pm.png)

   海报 — 最终对话框结构

   此时， `poster` 组件可添加到 **空闲渠道** 页面： `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![海报对话框字段](assets/poster-dialog-full.png)

   海报对话框字段

1. 在下方创建文件 `/apps/weretail-run/components/content/poster` 已命名 `production.html.`

   使用以下内容填充文件：

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   上面是海报组件的生产标记。 HTL脚本覆盖 `screens/core/components/content/image/production.html`. 的 `image.js` 是用于创建类似于POJO的图像对象的服务器端脚本。 然后可以调用Image对象来渲染 `src` 作为内联样式背景图像。

   `The h1` 和h2标记会根据组件属性显示标题和描述： `${properties.jcr:title}` 和 `${properties.jcr:description}`.

   围绕 `h1` 和 `h2` 标记是包含三个CSS类的div包装器，其变体为“ `cmp-poster__text`&quot; 的值 `textPosition` 和 `textColor` 属性用于更改根据作者的对话框选择呈现的CSS类。 在下一部分中，将编写客户端库中的CSS以在显示中启用这些更改。

   组件中还包含徽标作为叠加。 在此示例中，We.Retail徽标的路径在DAM中进行了硬编码。 根据用例的不同，创建对话框字段以使徽标路径成为动态填充值可能更有意义。

   另请注意，组件使用BEM（块元素修饰符）符号。 BEM是一种CSS编码约定，可更轻松地创建可重用组件。 BEM是使用的符号 [AEM核心组件](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. 在下方创建文件 `/apps/weretail-run/components/content/poster` 已命名 `edit.html.`

   使用以下内容填充文件：

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   以上是 **编辑** 标记。 HTL脚本覆盖 `/libs/screens/core/components/content/image/edit.html`. 标记类似于 `production.html` 标记，并在图像顶部显示标题和描述。

   的 `aem-Screens-editWrapper`以便组件不会在编辑器中呈现全屏。 的 `data-emptytext` 属性可确保在未填充图像或内容时显示占位符。

## 创建客户端库 {#clientlibs}

客户端库提供了一种机制，用于组织和管理实施AEM所必需的CSS和JavaScript文件。 有关使用的更多信息 [客户端库可在此处找到。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

AEM Screens组件在编辑模式与预览/生产模式下的呈现方式不同。 将创建两组客户端库，一组用于“编辑”模式，另一组用于“预览”/“生产”模式。

1. 为海报组件的客户端库创建文件夹。

   下 `/apps/weretail-run/components/content/poster,`创建名为的文件夹 `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在 `clientlibs` 文件夹创建名为的节点 `shared` 类型 `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 将以下属性添加到共享客户端库：

   * `allowProxy` | 布尔型 | `true`
   * `categories` | 字符串[] | `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的属性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的属性

   的 `categories` 属性是一个用于标识客户端库的字符串。 的 `cq.screens.components` 类别在“编辑”和“预览”/“生产”模式中均使用。 因此， `shared` clientlib以所有模式加载。

   最佳做法是，切勿在生产环境中直接向/apps显示任何路径。 的 `allowProxy` 属性可确保客户端库CSS和JS通过前缀( `/etc.clientlibs`. 有关 [allowProxy属性可在此处找到。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

1. 创建名为 `css.txt` 共享文件夹下方。

   使用以下内容填充文件：

   ```
   #base=css
   
   styles.less
   ```

1. 创建名为的文件夹 `css` 在 `shared` 文件夹。 添加名为 `style.less` 在 `css` 文件夹。 客户端库的结构现在应如下所示：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教程不使用LESS，而是直接编写CSS。 [LESS](https://lesscss.org/) 是一种常用的CSS预编译器，它支持CSS变量、混合和函数。 AEM客户端库本身支持LESS编译。 可以使用Sas或其他预编译器，但必须在AEM之外进行编译。

1. 填充 `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` ，具有以下特点：

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >GoogleWeb Fonts用于字体系列。 Web Fonts需要internet连接，而且并非所有实施的屏幕都能可靠连接。 规划离线模式是Screens部署的重要注意事项。

1. 复制 `shared` 客户端库文件夹。 将其粘贴为同级，然后将其重命名为 `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 更新 `categories` 要 `cq.screens.components.production.`

   的 `cq.screens.components.production` 类别可确保样式仅在“预览”/“生产”模式下加载。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的属性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的属性

1. 填充 `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` ，具有以下特点：

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   上述样式将标题和描述显示在屏幕上的绝对位置。 标题显示的大于描述。 使用组件的BEM符号，可以轻松地仔细检查cmp-poster类中的样式。

第三个clientlibrary类别： `cq.screens.components.edit` 只能用于向组件添加“编辑”特定样式。

| Clientlib类别 | 用途 |
|---|---|
| `cq.screens.components` | 在编辑模式和生产模式之间共享的样式和脚本 |
| `cq.screens.components.edit` | 仅在编辑模式下使用的样式和脚本 |
| `cq.screens.components.production` | 仅在生产模式中使用的样式和脚本 |

## 将海报组件添加到序列渠道 {#add-sequence-channel}

海报组件用于序列渠道。 本教程的起始包中包含一个空闲渠道。 空闲渠道已预配置为允许组的组件 **We.Retail运行 — 内容**. 海报组件的组设置为 `We.Retail Run - Content` 和可添加到渠道中。

1. 从We.Retail Run项目中打开Idle Channel: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 拖放新实例 **海报** 组件。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 编辑海报组件的对话框以添加图像、标题、描述。 使用文本位置和文本颜色选项可确保标题/描述在图像上可读。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重复上述步骤以添加一些海报组件。 在组件之间添加过渡。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 融于一起 {#putting-it-all-together}

以下视频显示完成的组件以及如何将其添加到序列渠道。 然后，该渠道会添加到“位置”显示屏，并最终分配给Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成的代码 {#finished-code}

以下是教程中完成的代码。 的 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** 和 **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** 是编译的AEM包。 **SRC-screens-weretail-run-0.0.1.zip **是未编译的源代码，可使用Maven部署。

[获取文件](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[获取文件](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC最终屏幕We.Retail运行项目

[获取文件](assets/src-screens-weretail-run-001.zip)
