---
title: 在MultiZone布局中创建自定义模板
seo-title: 在MultiZone布局中创建自定义模板
description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
seo-description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: a4d48ba04bb8ab863f4f07b932892676b70e1e23

---


# 在MultiZone布局中创建自定义模板 {#creating-custom-templates-multizone}

以下示例展示了如何在multiZone布局中创建自定义模板。

例如，下面的部分演示了如何使用以下配置在多区域布局中创建自定义模板：

![图像](assets/custom-template1.png)


## 使用特定配置创建自定义模板 {#basic-flow-setting}

请按照以下步骤创建自定义模板。

1. 在 `/apps/<project>/templates/my-custom-layout`

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. 在中创建页面设计 `/apps/settings/wcm/designs/<project>`。

   >[!NOTE]
   >
   >确保上面 `cq:designPath` 的路径匹配。

1. 更新 **设计的offline-config** 节点，以同时指向新路径

1. 在文 **件夹中添加static.css**`/apps/settings/wcm/designs/<project>` 文件并将其内容设置为

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

## 将图像作为背景图层插入 {#inserting-image}

您可以将图像作为背景图层插入布局：

您可以调整CSS规则，以使用“data-uri”，并直接在CSS文件中嵌入图像（Base64编码）。

具体操作如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以按照以下步骤操作：

1. 确保以某种方式将图像包含在渠道的脱机配置中
1. 使用指向上述CSS中图像的直接链接，而不是“data-uri”变体


## 更新背景颜色 {#updating-color}

要更改背景颜色，请向xml文件添加以下代码：

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



