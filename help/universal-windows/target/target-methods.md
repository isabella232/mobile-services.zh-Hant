---
description: 通用 Windows 平台程式庫所提供的 Target 方法清單。
seo-description: 通用 Windows 平台程式庫所提供的 Target 方法清單。
seo-title: Target 方法
solution: Marketing Cloud、Analytics
title: Target 方法
topic: 開發人員和實施
uuid: 2ad5953b-7850-446a-8053-b3715 b86329 b
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target methods {#target-methods}

通用 Windows 平台程式庫所提供的 Target 方法清單。

SDK 目前已支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target 以及 Audience Manager。

[生命週期度量](/help/universal-windows/metrics.md) 會傳送為每個mbox載入的參數。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## 類別參考: TargetLocationRequest

## 屬性

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 字串常數

此資訊可協助您設定自訂參數的索引鍵。

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

* **LoadRequest(WinJS：LoadRequest)**

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * 以下是此方法的語法:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **CreateRequest(WinJS：CreateRequest)**

   使用指定的參數建立 `TargetLocationRequest` 物件。

   * 以下是此方法的語法:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **CreateOrderConfirmRequest(WinJS：CreateOrderConfirmRequest)**

   使用指定的參數建立 `TargetLocationRequest` 物件。

   * 以下是此方法的語法:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **ClearCookies(WinJS：ClearCookies)**

   在目前裝置上清除應用程式中的 Target cookies。

   * 以下是此方法的語法:

      ```csharp
      static void ClearCookies();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **getPCId(WinJS：getPCId)**

   傳回目前裝置的 PC ID cookie。

   * 以下是此方法的語法:

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **getSessionId(WinJS：getSessionId)**

   傳回目前裝置的工作階段 ID cookie。

   * 以下是此方法的語法:

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * 以下是此方法的範例程式碼:

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```

