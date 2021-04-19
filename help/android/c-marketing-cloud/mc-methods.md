---
description: 以下為 Android 資料庫所提供的 Experience Cloud ID 方法。
keywords: android;資料庫;行動;sdk
seo-description: 以下為 Android 資料庫所提供的 Experience Cloud ID 方法。
seo-title: Adobe Experience Platform Identity Service 方法
solution: Experience Cloud,Analytics
title: Adobe Experience Platform Identity Service 方法
topic-fix: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
exl-id: 8eb98c3f-c6ef-4593-ad3a-f566f4d4b6a2
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 100%

---

# Adobe Experience Platform Identity Service 方法{#experience-cloud-id-service-methods}

以下為 Android 資料庫所提供的 Experience Cloud ID 方法。

SDK 目前可支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Adobe Experience Platform Identity Service。

各方法會根據解決方案加上前置詞，例如 Experience Cloud ID 方法會加上前置詞 `visitor`。如需詳細資訊，請參閱 [Experience Cloud ID 設定](/help/android/c-marketing-cloud/mcvid.md)。

* **公用靜態字串 appendToURL (最後字串URL)**

   將 Adobe 訪客資料附加至 URL 字串以與 Adobe JavaScript 資料庫搭配使用。您必須安裝 Mobile SDK 4.12 以上版本，才能使用此方法。如需詳細資訊，請參閱[附加訪客 ID 協助程式功能](https://docs.adobe.com/content/help/zh-Hant/id-service/using/id-service-api/methods/appendvisitorid.html)。

   >[!IMPORTANT]
   >
   >此方法會造成封鎖網路呼叫。請勿在具時效性的執行緒上呼叫此方法。

   * 此方法的語法如下：

      ```java
      public static String appendToURL(final String URL) 
      ```

      附加訪客資訊的必要 URL 字串。

   * 此方法的程式碼範例如下：

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   從訪客 ID 服務中擷取 Experience Cloud ID。

   * 此方法的語法如下：

      ```java
      public static String getMarketingCloudId(); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >此方法會造成封鎖網路呼叫，且&#x200B;**不**&#x200B;應從使用者介面執行緒呼叫此方法。

* **syncIdentifiers**

   透過 Experience Cloud ID，您可以設定與每個訪客相關聯的額外客戶 ID。訪客 API 可接受同一名訪客具有多個客戶 ID，並透過客戶類型識別碼來區分不同客戶 ID 的範圍。此方法對應至 JavaScript 資料庫中的 `setCustomerIDs`。

   * 此方法的語法如下：

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   將提供的識別碼類型和值同步至訪客 ID 服務。

   在 `authenticationState` 中以下列任一值傳遞：

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 此方法的語法如下：

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   將提供的識別碼同步至 ID 服務。

   在 `authenticationState` 中以下列任一值傳遞：
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 此方法的語法如下：

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 此方法的程式碼範例如下：

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   擷取唯讀 `ADBVisitorID` 物件清單。

   * 此方法的語法如下：

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * 此方法的程式碼範例如下：

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   4.16.0 版導入了此方法，可傳回包含訪客 ID 服務 URL 變數的適當形式字串。如需如何使用此方法的詳細資訊，請參閱 [Adobe Experience Platform Identity Service 方法](/help/android/reference/hybrid-app.md)。

   * 此方法的語法如下：

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * 此方法的程式碼範例如下：

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

## 公用方法 {#section_8AC744B431A3438C9B45629CA3EA0F51}

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
