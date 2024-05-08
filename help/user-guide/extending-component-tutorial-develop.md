---
title: 扩展AEM Screens组件
description: 在本教程中了解扩展AEM Screens现成组件的步骤和最佳实践。 扩展图像组件，以添加可创作的文本叠加。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: e316614f-2d40-4b62-a1e5-f30817def742
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 1%

---

# 扩展AEM Screens组件

以下教程将指导您完成扩展AEM Screens现成组件的步骤和最佳实践。 扩展图像组件，以添加可创作的文本叠加。

## 概述 {#overview}

本教程面向不熟悉AEM Screens的开发人员。 在本教程中，扩展了Screens图像组件以创建海报组件。 标题、描述和徽标叠加在图像上，以便在序列渠道中创建引人入胜的体验。

>[!NOTE]
>
>在开始本教程之前，建议先完成本教程： [为AEM Screens开发自定义组件](developing-custom-component-tutorial-develop.md).

![自定义海报组件](assets/2018-05-07_at_4_09pm.png)

通过扩展图像组件来创建自定义海报组件。

## 先决条件 {#prerequisites}

要完成本教程，您需要满足以下条件：

1. AEM 6.5 +最新Screens功能包
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本地开发环境

使用CRXDE-Lite执行教程步骤和屏幕截图。 [Eclipse](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/devtools/aem-eclipse) 或 [IntelliJ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/devtools/ht-intellij) IDE也可用于完成本教程。 有关使用IDE的详细信息 [使用AEM进行开发可在此处找到](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup).

## 项目设置 {#project-setup}

屏幕项目的源代码通常作为多模块Maven项目进行管理。 为了加快教程，使用预生成了一个项目 [AEM项目原型13](https://github.com/adobe/aem-project-archetype). 更多详细信息 [可在此处找到使用Maven AEM项目原型创建项目的内容](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup).

1. 使用下载并安装以下包 **CRX包管理** `http://localhost:4502/crx/packmgr/index.jsp)r:`

[获取文件](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [获取文件](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（可选）** 如果使用Eclipse或其他IDE，请下载以下源包。 使用Maven命令将项目部署到本地AEM实例：

   **`mvn -PautoInstallPackage clean install`**

   SRC开始屏幕 `We.Retail` 运行项目

[获取文件](assets/start-poster-screens-weretail-run.zip)

1. 在 **CRX包管理器** `http://localhost:4502/crx/packmgr/index.jsp` 以下两个软件包已安装：

   1. **`screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip`**
   1. **`screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip`**

   ![Screens We.Retail通过CRX包管理器运行Ui.Apps和Ui.Content包](assets/crx-packages.png)

   AEM Screens `We.Retail Run Ui.Apps` 和 `Ui.Content` 通过CRX包管理器安装的包

## 创建海报组件 {#poster-cmp}

海报组件可扩展现成的AEM Screens图像组件。 Sling的机制， `sling:resourceSuperType`，用于继承图像组件的核心功能，而无需复制和粘贴。 有关的基础知识的更多信息 [Sling请求处理可在此处找到。](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/introduction/the-basics)

海报组件在预览/生产模式下全屏渲染。 在编辑模式下，请务必以不同方式呈现组件，以便于创作序列渠道。

1. 在 **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` （或选择的IDE）到 `/apps/weretail-run/components/content`创建 `cq:Component` 已命名 `poster`.

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

   通过设置 `sling:resourceSuperType`属性等于 `screens/core/components/content/image`，海报组件有效地继承了图像组件的所有功能。 在下找到的对等节点和文件 `screens/core/components/content/image` 可添加到下方 `poster` 覆盖和扩展功能的组件。

1. 复制 `cq:editConfig` 节点在下 `/libs/screens/core/components/content/image`. 粘贴 `cq:editConfig` 在 `/apps/weretail-run/components/content/poster` 组件。

   在 `cq:editConfig/cq:dropTargets/image/parameters` 节点，更新 `sling:resourceType` 属性等于 `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   XML表示形式 `cq:editConfig` 列示如下：

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

1. 复制WCM Foundation `image` 对话框用于 `poster` 组件。

   最简单的方法是从现有对话框开始，然后进行修改。

   1. 从以下位置复制对话框： `/libs/wcm/foundation/components/image/cq:dialog`
   1. 将对话框粘贴到下 `/apps/weretail-run/components/content/poster`

   ![已将对话框从/libs/wcm/foundation/components/image/cq：dialog复制到/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   对话框复制自 `/libs/wcm/foundation/components/image/cq:dialog` 到 `/apps/weretail-run/components/content/poster`

   AEM Screens `image` 组件是WCM Foundation的超类型 `image` 组件。 因此， `poster` 组件从两者继承功能。 海报组件的对话框由屏幕对话框和基础对话框的组合组成。 的功能 **Sling资源合并器** 用于隐藏从超类型组件继承的不相关的对话框字段和选项卡。

1. 更新 `cq:dialog` 下 `/apps/weretail-run/components/content/poster` 以XML表示以下更改：

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
                                   sling:resourceType="granite/ui/components/coral/foundation/form/click"
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
                                   sling:resourceType="granite/ui/components/coral/foundation/form/click"
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

   属性 `sling:hideChildren`= `"[linkURL,size]`”用于 `items` 节点，以确保 **linkURL** 和 **大小** 对话框中的字段是隐藏的。 仅从海报对话框中删除这些节点是不够的。 属性 `sling:hideResource="{Boolean}true"` “辅助功能”选项卡上用于隐藏整个选项卡。

   对话框中添加了两个单击字段，作者可以控制标题和描述的文本位置和颜色。

   ![海报 — 最终对话框结构](assets/2018-05-03_at_4_49pm.png)

   海报 — 最终对话框结构

   此时， `poster` 组件可添加到 **空闲通道** 中的页面`We.Retail` 运行项目： `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![海报对话框字段](assets/poster-dialog-full.png)

   海报对话框字段

1. 在下创建文件 `/apps/weretail-run/components/content/poster` 已命名 `production.html.`

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

   可直接在上方看到海报组件的生产标记。 HTL脚本覆盖 `screens/core/components/content/image/production.html`. 此 `image.js` 是创建类似POJO的图像对象的服务器端脚本。 然后，可以调用Image对象来渲染 `src` 作为内联样式背景图像。

   `The h1` 添加和h2标记后，会根据组件属性显示标题和描述： `${properties.jcr:title}` 和 `${properties.jcr:description}`.

   围绕 `h1` 和 `h2` 标记是一个div包装器，其中包含三个CSS类，且变体为&quot; `cmp-poster__text`“。 的值 `textPosition` 和 `textColor` 属性用于根据作者的对话框选择更改渲染的CSS类。 在下一部分中，将写入客户端库中的CSS，以便在显示中启用这些更改。

   徽标还作为覆盖包含在组件中。 在此示例中，指向` We.Retail` 徽标在DAM中进行硬编码。 根据用例，可能更适合创建对话框字段，以将徽标路径设置为动态填充值。

   另请注意，组件使用BEM（块元素修饰符）表示法。 BEM是一种CSS编码约定，它使创建可重用组件变得更容易。 BEM是使用的表示法 [AEM核心组件](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. 在下创建文件 `/apps/weretail-run/components/content/poster` 已命名 `edit.html.`

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

   此 **编辑** 可直接在上方看到海报组件的标记。 HTL脚本覆盖 `/libs/screens/core/components/content/image/edit.html`. 标记类似于 `production.html` 标记，并在图像顶部显示标题和描述。

   此 `aem-Screens-editWrapper`添加，以便组件不会在编辑器中全屏呈现。 此 `data-emptytext` 属性可确保在没有填充图像或内容时显示占位符。

## 创建客户端库 {#clientlibs}

客户端库提供了一种机制，用于组织和管理AEM实施所需的CSS和JavaScript文件。 有关使用的更多信息 [可以在此处找到客户端库。](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs)

AEM Screens组件在编辑模式与预览/生产模式中的呈现方式有所不同。 将创建两组客户端库，一组用于编辑模式，另一组用于预览/生产模式。

1. 为海报组件的客户端库创建文件夹。

   下 `/apps/weretail-run/components/content/poster`，创建一个名为的文件夹 `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在 `clientlibs` 文件夹，创建名为的节点 `shared` 类型 `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 将以下属性添加到共享客户端库：

   * `allowProxy` | 布尔型 | `true`
   * `categories` | 字符串[] | `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的属性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的属性

   此 `categories` 属性是用于标识客户端库的字符串。 此 `cq.screens.components` 类别在编辑和预览/生产模式下均使用。 因此，在中定义的任何CSS/JS `shared` clientlib在所有模式下加载。

   最佳做法是，切勿在生产环境中直接向/apps公开任何路径。 此 `allowProxy` 属性确保通过的前缀引用客户端库CSS和JS `/etc.clientlibs`. 欲知关于 [可以在此处找到allowProxy属性。](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs)

1. 创建名为的文件 `css.txt` 在共享文件夹下。

   使用以下内容填充文件：

   ```
   #base=css
   
   styles.less
   ```

1. 创建名为的文件夹 `css` 在 `shared` 文件夹。 添加名为的文件 `style.less` 在 `css` 文件夹。 客户端库的结构现在应如下所示：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教程不会直接编写CSS，而是使用LESS。 [更少](https://lesscss.org/) 是一个常用的CSS预编译器，它支持CSS变量、mixin和函数。 AEM客户端库本身支持LESS编译。 Sass或其他预编译器可以使用，但必须在AEM之外编译。

1. 填充 `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` ，如下所示：

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
   >GoogleWeb Fonts用于字体系列。 Web Fonts需要互联网连接，并且并非所有AEM Screens实施都有可靠的连接。 规划离线模式是AEM Screens部署的一个重要考虑事项。

1. 复制 `shared` 客户端库文件夹。 将其粘贴为同级并重命名为 `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 更新 `categories` 要成为的生产客户端库的属性 `cq.screens.components.production.`

   此 `cq.screens.components.production` 类别可确保仅在“预览”/“生产”模式下加载样式。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的属性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的属性

1. 填充 `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` ，如下所示：

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

   上述样式在屏幕上以绝对位置显示标题和描述。 显示的标题比描述大。 利用组件的BEM表示法，可以轻松地在cmp-poster类中仔细限定样式。

第三个客户端库类别： `cq.screens.components.edit` 可用于将仅编辑特定样式添加到组件。

| Clientlib类别 | 用途 |
|---|---|
| `cq.screens.components` | 在编辑模式和生产模式之间共享的样式和脚本 |
| `cq.screens.components.edit` | 仅在编辑模式下使用的样式和脚本 |
| `cq.screens.components.production` | 仅在生产模式下使用的样式和脚本 |

## 将海报组件添加到序列渠道 {#add-sequence-channel}

海报组件用于序列渠道。 本教程的入门软件包包含一个“空闲通道”。 已预配置空闲通道，以允许组内的组件 **`We.Retail Run - Content`**. 海报组件的组设置为 `We.Retail Run - Content` 并且可以添加到渠道中。

1. 从以下位置打开空闲通道： `We.Retail` 运行项目： **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 拖放的新实例 **海报** 组件从侧栏转到页面。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 编辑海报组件的对话框，以便添加图像、标题和描述。 使用文本位置和文本颜色选项确保标题/描述在图像上可读。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 要添加几个海报组件，请重复上述步骤。 在组件之间添加过渡。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 融于一起 {#putting-it-all-together}

以下视频介绍了已完成的组件以及如何将其添加到序列渠道。 然后，该渠道会添加到位置显示中，并最终分配给Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成的代码 {#finished-code}

以下是教程中完成的代码。 此 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** 和 **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** 是编译的AEM包。 此 **SRC-screens-weretail-run-0.0.1.zip** 是可以使用Maven部署的未编译的源代码。

[获取文件](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[获取文件](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC最终AEM Screens `We.Retail` 运行项目

[获取文件](assets/src-screens-weretail-run-001.zip)
