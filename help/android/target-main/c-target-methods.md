---
description: 以下為 Android 資料庫所提供的 Adobe Target 方法清單。
keywords: android;library;mobile;sdk
seo-description: 以下為 Android 資料庫所提供的 Adobe Target 方法清單。
seo-title: Target methods for Android
solution: Marketing Cloud,Analytics
title: Target methods for Android
topic: 開發人員和實施
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target methods for Android{#target-methods}

以下為 Android 資料庫所提供的 Adobe Target 方法清單。

The SDK currently supports multiple Adobe Experience Cloud Solutions, including Analytics, Target, Audience Manager, and the Adobe Experience Platform Identity Service]. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `target`.

>[!TIP]
>
>[生命週期量度](/help/android/metrics.md)會以參數形式傳送至各 mbox 負載。

## Class reference : TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**屬性:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**String constants**

>[!TIP]
>
>The following constants are for ease of use when you set keys for custom parameters.

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
>* If you are using SDKs **before** version 4.14.0, see [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or later**, see [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


* **loadRequest**

   傳送要求至您設定的 Target 伺服器並傳回區塊回撥中產生之選件的字串值。

   * 以下是此方法的語法:

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   傳送要求至您設定的 Target 伺服器並傳回區塊回撥中產生之選件的字串值。

   * 以下是此方法的語法:

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * 以下是此方法的範例程式碼:

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

   * 以下是此方法的語法:

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **傳回:** N/A

   * **參數:**

      Here are the parameters for this method:

      * **名稱**

         您要擷取的 Target mbox/位置名稱。

         * **** 類型：字串
      * **defaultContent**

         如果 Target 伺服器無法連線或使用者不符合促銷活動資格，則將會在回撥中傳回值。

         * **Type:** String
      * **profileParameters**

         此字典中的值會根據 Target 要求進入「profileParameters」物件。

         * **** Type: Map `<String, Object>`
      * **orderParameters**

         此字典中的值會根據 Target 要求進入「order」物件。

         * **** Type: Map `<String, Object>`
      * **mboxParameters**

         Values in this dictionary will go in the request to Target.

         * **** Type: Map `<String, Object>`
      * **requestLocationParameters**

         此字典中的值會根據 Target 要求進入「requestLocation」物件。

         * **** Type: Map `<String, Object>`
      * **callBack**

         此方法將會與 Target 伺服器中的選件內容一併接受呼叫。如果 Target 伺服器無法連線或使用者不符合促銷活動資格，則將會傳回 defaultContent。

         * **** Type: TargetCallback `<String>`
   * 以下是此方法的范常式式碼：

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








* **createOrder&#x200B;ConfirmRequest**

   使用指定的參數建立 TargetLocationRequest 物件。

   * 以下是此方法的語法:

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   使用指定的參數建立 TargetLocationRequest 物件。

   * 以下是此方法的語法:

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   清除應用程式中的目標 Cookie。

   * 以下是此方法的語法:

      ```java
      public static void clearCookies();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   傳回 pcID。

   * 以下是此方法的語法:

      ```java
      public static String getPcID();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   傳回工作階段 ID。

   * 以下是此方法的語法:

      ```java
      public static String getSessionID();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   設定第三方 ID。

   * 以下是此方法的語法:

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   傳回第三方 ID。

   * 以下是此方法的語法:

      ```java
      public static String getThirdPartyID();
      ```

   * 以下是此方法的範例程式碼:

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
