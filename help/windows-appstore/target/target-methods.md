---
description: Windows 8.1通用應用程式商店程式庫提供的Target方法清單。
seo-description: Windows 8.1通用應用程式商店程式庫提供的Target方法清單。
seo-title: Target 方法
solution: Experience Cloud,Analytics
title: Target 方法
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 42%

---

# Target 方法 {#target-methods}

Windows 8.1通用應用程式商店程式庫提供的Target方法清單。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target和Audience Manager。 各方法會根據解決方案加上前置詞。Analytics方法的前置詞為「Target」。

[生命週期量度](/help/windows-appstore/metrics.md)會以參數形式傳送至各 mbox 負載。

>[!TIP]
>
>當您從winJS(JavaScript)使用`winmd`方法時，所有方法都會自動將其第一個字母小寫。

## 類別參考：TargetLocationRequest

### 屬性

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 字串常數

這項資訊可協助您設定自訂參數的索引鍵。

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **LoadRequest(winJS:loadRequest)**

   傳送`request`至您設定的Target伺服器，並傳回區塊`callback`中產生之選件的字串值。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest(winJS:createRequest)**

   使用給定參數建立`TargetLocationRequest`對象。

   * 此方法的語法如下：

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest(winJS:createOrder &#x200B; ConfirmRequest)**

   使用給定參數建立`TargetLocationRequest`對象。

   * 此方法的語法如下：

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies(winJS:clearCookie)**

   清除目前裝置上應用程式的Target Cookie。

   * 此方法的語法如下：

      ```csharp
      static void ClearCookies(); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId(winJS:getPcId)**

   傳回目前裝置的PC ID Cookie。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * 此方法的程式碼範例如下：

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId(winJS:getSessionId)**

   傳回目前裝置的作業階段ID Cookie。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
