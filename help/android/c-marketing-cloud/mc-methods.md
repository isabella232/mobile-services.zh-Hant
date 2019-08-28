---
description: 以下為 Android 資料庫所提供的 Experience Cloud ID 方法。
keywords: Android；資料庫；行動；sdk
seo-description: 以下為 Android 資料庫所提供的 Experience Cloud ID 方法。
seo-title: Adobe Experience Platform Identity Service方法
solution: Marketing Cloud、Analytics
title: Adobe Experience Platform Identity Service方法
topic: 開發人員和實施
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: a54a969bb6abedfeb0fc20276d260664b68c1d66

---


# Adobe Experience Platform Identity Service方法{#experience-cloud-id-service-methods}

以下為 Android 資料庫所提供的 Experience Cloud ID 方法。

SDK目前支援多個Adobe Experience Cloud解決方案]，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **公用靜態字串 appendToURL (最後字串URL)**

   將 Adobe 訪客資料附加至 URL 字串以與 Adobe JavaScript 資料庫搭配使用。您必須有 Mobile SDK 4.12+ 才能使用此方法。如需詳細資訊，請參閱[附加訪客 ID 協助程式功能](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)。

   >[！重要事項]
   >
   >此方法可能會造成封鎖網路呼叫。請勿在具時效性的執行緒上呼叫此方法。

   * 以下是此方法的語法:

      ```java
      URL java.lang.String  
      ```

      附加訪客資訊的必要 URL 字串。

   * 以下是此方法的範例程式碼:

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   從訪客 ID 服務中擷取 Experience Cloud ID。

   * 以下是此方法的語法:

      ```java
      public static String getMarketingCloudId(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   透過 Experience Cloud ID，您可以設定與每個訪客相關聯的額外客戶 ID。訪客 API 可接受同一名訪客具有多個客戶 ID，並透過客戶類型識別碼來區分不同客戶 ID 的範圍。此方法對應至 JavaScript 資料庫中的 `setCustomerIDs`。

   * 以下是此方法的語法:

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   將提供的識別碼類型和值同步至訪客 ID 服務。

   在 `authenticationState` 中以下列其中一個值傳遞:

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 以下是此方法的語法:

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   將提供的識別碼同步至 ID 服務。

   在 `authenticationState` 中以下列其中一個值傳遞:
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 以下是此方法的語法:

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   擷取唯讀 `ADBVisitorID` 物件清單。

   * 以下是此方法的語法:

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getURLVariablesAsync**

   此方法在4.16.0版中引入，傳回包含訪客ID服務URL變數的適當字串。如需如何使用此方法的詳細資訊，請參閱 [Adobe Experience Platform Identity Service方法](/help/android/reference/hybrid-app.md)。

   * 以下是此方法的語法:

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
