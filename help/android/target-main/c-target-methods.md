---
description: 以下為 Android 資料庫所提供的 Adobe Target 方法清單。
keywords: android;資料庫;行動;sdk
seo-description: 以下為 Android 資料庫所提供的 Adobe Target 方法清單。
seo-title: 適用於 Android 的 Target 方法
solution: Experience Cloud,Analytics
title: 適用於 Android 的 Target 方法
topic-fix: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
exl-id: 0c7a6718-d078-4a2b-a2c9-d5cd50263939
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 100%

---

# 適用於 Android 的 Target 方法{#target-methods}

以下為 Android 資料庫所提供的 Adobe Target 方法清單。

SDK 目前可支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Adobe Experience Platform Identity Service。各方法會根據解決方案加上前置詞，例如 Experience Cloud ID 方法會加上前置詞 `target`。

>[!TIP]
>
>[生命週期量度](/help/android/metrics.md)會以參數形式傳送至各 mbox 負載。

## 類別參考：TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**屬性：**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**字串常數**

>[!TIP]
>
>下列常數可方便您針對自訂參數設定索引鍵。

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* 如果您是使用 4.14.0 版&#x200B;**之前**&#x200B;的 SDK，請參閱 [](https://developers.adobetarget.com/api/#input-parameters)https://developers.adobetarget.com/api/#input-parameters 以瞭解參數限制。
>
>* 如果您是使用 SDK 4.14.0 版&#x200B;**或更新版本**，請參閱 [](https://developers.adobetarget.com/api/#batch-input-parameters)https://developers.adobetarget.com/api/#batch-input-parameters 以瞭解參數限制。


* **loadRequest**

   傳送要求至您設定的 Target 伺服器並傳回區塊回撥中產生之選件的字串值。

   * 此方法的語法如下：

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   傳送要求至您設定的 Target 伺服器並傳回區塊回撥中產生之選件的字串值。

   * 此方法的語法如下：

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * 此方法的程式碼範例如下：

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   傳送要求至您設定的 Target 伺服器並傳回 TargetCallback 中產生之選件的字串值。

   * 此方法的語法如下：

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **傳回：** N/A

   * **參數：**

      此方法的參數如下：

      * **名稱**

         您要擷取的 Target mbox/位置名稱。

         * **類型：**&#x200B;字串
      * **defaultContent**

         如果 Target 伺服器無法連線或使用者不符合促銷活動資格，則將會在回撥中傳回值。

         * **類型：**&#x200B;字串
      * **profileParameters**

         此字典中的值會根據 Target 要求進入「profileParameters」物件。

         * **類型：**&#x200B;對應 `<String, Object>`
      * **orderParameters**

         此字典中的值會根據 Target 要求進入「order」物件。

         * **類型：**&#x200B;對應 `<String, Object>`
      * **mboxParameters**

         此字典中的值會根據 Target 要求進入。

         * **類型：**&#x200B;對應 `<String, Object>`
      * **requestLocationParameters**

         此字典中的值會根據 Target 要求進入「requestLocation」物件。

         * **類型：**&#x200B;對應 `<String, Object>`
      * **callBack**

         此方法將會與 Target 伺服器中的選件內容一併接受呼叫。如果 Target 伺服器無法連線或使用者不符合促銷活動資格，則將會傳回 defaultContent。

         * **類型：** TargetCallback `<String>`
   * 此方法的程式碼範例如下：

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      如需底層 Target API 的詳細資訊，請參閱 Target 開發人員說明中的[傳送](https://docs.adobe.com/dev/products/target/reference/delivery.html)。








* **createOrderConfirmRequest**

   使用指定的參數建立 TargetLocationRequest 物件。

   * 此方法的語法如下：

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * 此方法的程式碼範例如下：

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   使用指定的參數建立 TargetLocationRequest 物件。

   * 此方法的語法如下：

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * 此方法的程式碼範例如下：

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   清除應用程式中的目標 Cookie。

   * 此方法的語法如下：

      ```java
      public static void clearCookies();
      ```

   * 此方法的程式碼範例如下：

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   傳回 pcID。

   * 此方法的語法如下：

      ```java
      public static String getPcID();
      ```

   * 此方法的程式碼範例如下：

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   傳回工作階段 ID。

   * 此方法的語法如下：

      ```java
      public static String getSessionID();
      ```

   * 此方法的程式碼範例如下：

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   設定第三方 ID。

   * 此方法的語法如下：

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   傳回第三方 ID。

   * 此方法的語法如下：

      ```java
      public static String getThirdPartyID();
      ```

   * 此方法的程式碼範例如下：

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
