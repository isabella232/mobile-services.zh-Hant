---
description: 「回傳」功能的定義與原始碼範例。
seo-description: 「回傳」功能的定義與原始碼範例。
seo-title: 回傳範例
solution: Experience Cloud,Analytics
title: 回傳範例
topic-fix: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
exl-id: 3ec5abf1-a406-48b6-91b1-fbcb0a9094ee
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 100%

---

# 回傳範例 {#postback-example}

「回傳」功能的定義與原始碼範例。

>[!CAUTION]
>
>此範例僅供參考之用。`ADBMobileConfig.json` 檔案應在 Adobe Mobile 使用者介面中設定，且不應手動修改。若您已啟用遠端訊息設定，手動編輯設定檔案可能會有危險。

## ADBMobileConfig.json 定義 {#section_0F6EC001AB6D488E815F50C7F5DA022E}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## 程式碼範例 {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

因為其狀態為 `“MainMenu”`，所以此追蹤呼叫會觸發上述回傳訊息。URL 會以點擊中的值取代所有範本變數。假設使用者的上一個工作階段為 132 秒長，且該使用者使用 iOS SDK 4.6.0 版，則以下是產生的 URL 範例:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
