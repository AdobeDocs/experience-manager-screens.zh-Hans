---
title: REST API
description: 了解AEM Screens如何提供一个遵循Siren规范的简单RESTful API。 还了解如何导航内容结构并将命令发送到环境中的设备。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: ac01935a-c3ff-485a-b60e-227fb94c75b0
source-git-commit: 43e89ddc3eb6baffca75d730a978e60e234aaee4
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# REST API{#rest-apis}

AEM Screens提供了一个遵循[Siren](https://github.com/kevinswiber/siren)规范的简单RESTful API。 它允许您导航内容结构并向环境中的设备发送命令。

该API可在&#x200B;[*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json)中访问。

## 导航内容结构 {#navigating-content-structure}

API调用返回的JSON列出了与当前资源相关的实体。 在列出的自链接后，这些实体中的每一个都可以再次作为REST资源访问。

例如，要访问演示旗舰位置中的显示内容，您可以调用以下命令：

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

或者使用curl：

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

结果将如下所示：

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

然后，要访问单屏幕显示，您可以调用：

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## 对资源执行操作 {#executing-actions-on-the-resource}

API调用返回的JSON可包含资源上可用的操作列表。

例如，该显示列出了&#x200B;*broadcast-command*&#x200B;操作，该操作允许向分配给该显示的所有设备发送命令。

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

或者使用curl：

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***结果：***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

要触发此操作，请调用以下调用：

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

或者使用curl：

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```
