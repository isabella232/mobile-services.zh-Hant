---
description: 「回傳」功能的定義與原始碼範例。
seo-description: 「回傳」功能的定義與原始碼範例。
seo-title: 回傳範例
solution: Marketing Cloud、Analytics
title: 回傳範例
topic: 開發人員和實施
uuid: 809c5646-7a80-40b-984b-0af89d85259
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback example {#postback-example}

「回傳」功能的定義與原始碼範例。

>[!CAUTION]
>
>此範例僅供參考。`ADBMobileConfig.json` 檔案應在 Adobe Mobile 使用者介面中設定，且不應手動修改。若您已啟用遠端訊息設定，手動編輯設定檔案可能會有危險。

## ADBMobileConfig.json definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Code sample {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. URL會取代所有範本變數與點擊中的值。假設使用者的前一個工作階段長度為132秒，而該使用者位於iOS SDK4.6.0版中，則此為產生的URL範例：

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
