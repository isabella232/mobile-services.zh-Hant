---
description: 此資訊可協助您了解回傳以及其運作方式。
keywords: Android；資料庫；行動；sdk
seo-description: 此資訊可協助您了解回傳以及其運作方式。
seo-title: 回傳範例
solution: Marketing Cloud、Analytics
title: 回傳範例
topic: 開發人員和實施
uuid: 8010cd00-d42 b-4e16-8403-692fab2550 f1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

您可以使用此資訊來協助您瞭解回傳及其運作方式。

>[!CAUTION]
>
>此範例僅供參考。`ADBMobileConfig.json` 檔案應在 Adobe Mobile 使用者介面中設定，且不應手動修改。若您已啟用遠端訊息設定，手動編輯設定檔案可能會有危險。

## `ADBMobileConfig.json` definition {#section_8751E8176F3546C09420341A39758AFF}

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. URL 會以點擊中的值取代所有範本變數。假設使用者的前一個工作階段長度為132秒，而該使用者使用Android SDK4.6.0版，則產生的URL看起來如下所示：

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
