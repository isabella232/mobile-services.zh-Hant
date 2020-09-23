---
description: 通用Windows平台程式庫提供的Target方法清單。
seo-description: 通用Windows平台程式庫提供的Target方法清單。
seo-title: Target 方法
solution: Experience Cloud,Analytics
title: Target 方法
topic: Developer and implementation
uuid: 2ad5953b-7850-446a-8053-b3715b86329b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 36%

---


# Target 方法 {#target-methods}

通用Windows平台程式庫提供的Target方法清單。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target和Audience Manager。

[生命週期度量](/help/universal-windows/metrics.md) ，會以參數的形式傳送至每個mbox載入。

>[!TIP]
>
>當您從winJS( `winmd` JavaScript)使用方法時，所有方法都會自動將其第一個字母小寫。

## 類別參考：TargetLocationRequest

## 屬性

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

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **CreateRequest(winJS:createRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * 此方法的語法如下：

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest(winJS:createOrder &#x200B; ConfirmRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * 此方法的語法如下：

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
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
      staticPlatform::String ^GetPcId();
      ```

   * 此方法的程式碼範例如下：

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **GetSessionId(winJS:getSessionId)**

   傳回目前裝置的作業階段ID Cookie。

   * 此方法的語法如下：

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * 此方法的程式碼範例如下：

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```
