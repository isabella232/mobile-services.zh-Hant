---
description: 此資訊可協助您了解回傳以及其運作方式。
keywords: android;資料庫;行動;sdk
solution: Experience Cloud,Analytics
title: 回傳範例
topic-fix: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
exl-id: 2ff41066-e2ee-425f-8aff-e5e3f3e5f0f5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---

# 回傳範例 {#postbacks-example}

此資訊可協助您了解回傳以及其運作方式。

>[!CAUTION]
>
>此範例僅供參考之用。`ADBMobileConfig.json` 檔案應在 Adobe Mobile 使用者介面中設定，且不應手動修改。若您已啟用遠端訊息設定，手動編輯設定檔案可能會有危險。

## `ADBMobileConfig.json` 定義 {#section_8751E8176F3546C09420341A39758AFF}

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

## 程式碼範例 {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

因為其狀態為 `"MainMenu"`，所以此追蹤呼叫會觸發上述回傳訊息。URL 會以點擊中的值取代所有範本變數。假設使用者的上一個工作階段為 132 秒長，且該使用者使用 Android SDK 4.6.0 版，則最後的 URL 看起來會像這樣:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
