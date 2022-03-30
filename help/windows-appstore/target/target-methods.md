---
description: Windows 8.1通用App Store庫提供的目標方法清單。
solution: Experience Cloud Services,Analytics
title: Target 方法
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 43%

---

# Target 方法 {#target-methods}

Windows 8.1通用App Store庫提供的目標方法清單。

SDK當前支援多個Adobe Experience Cloud解決方案，包括分析、目標和Audience Manager。 各方法會根據解決方案加上前置詞。分析方法的前置詞為「目標」。

[生命週期量度](/help/windows-appstore/metrics.md)會以參數形式傳送至各 mbox 負載。

>[!TIP]
>
>消費時 `winmd` 來自winJS(JavaScript)的方法，所有方法的首字母都自動小寫。

## 類別參考：TargetLocationRequest

### 屬性

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 字串常數

此資訊有助於您設定自定義參數的鍵。

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

   發送 `request` 返回在塊中生成的要約的字串值 `callback`。

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

   建立 `TargetLocationRequest` 對象。

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

   建立 `TargetLocationRequest` 對象。

   * 此方法的語法如下：

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookie(winJS:clearCookie)**

   清除當前設備上應用程式的目標Cookie。

   * 此方法的語法如下：

      ```csharp
      static void ClearCookies(); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId(winJS:getPcId)**

   返回當前設備的PC ID Cookie。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * 此方法的程式碼範例如下：

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId(winJS:getSessionId)**

   返回當前設備的會話ID Cookie。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
