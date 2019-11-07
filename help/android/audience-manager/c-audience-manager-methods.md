---
description: 以下為 Android 資料庫所提供的 Audience Manager 方法清單。
keywords: android;資料庫;行動;sdk
seo-description: 以下為 Android 資料庫所提供的 Audience Manager 方法清單。
seo-title: Audience Manager 方法
solution: Marketing Cloud,Analytics
title: Audience Manager 方法
topic: 開發人員和實施
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager 方法{#audience-manager-methods}

以下為 Android 資料庫所提供的 Audience Manager 方法清單。

SDK 目前可支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Adobe Experience Platform Identity Service。各方法會根據解決方案加上前置詞，例如 Experience Cloud ID 方法會加上前置詞 `audience manager`。

如果您已在 JSON 檔案中設定 Audience Manager，則包含生命週期量度的訊號會與生命週期點擊一併傳送。

* **getVisitorProfile**

   傳回最近取得的訪客設定檔，但若未提交任何訊號則會傳回 `null`。訪客設定檔會儲存在 `SharedPreferences` 中，方便您在多次啟動應用程式時存取。

   * 以下是此方法的語法:

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   傳回目前的 DPID。

   * 以下是此方法的語法:

      ```java
      public static void getDpid(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   傳回目前的 DPUUID。

   * 以下是此方法的語法:

      ```java
      public static void getDpuuid(); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   設定 DPID 和 DPUUID，而且這些值會隨著每個訊號傳送。

   如果傳遞至此方法的 DPUUID 值包含非 URL 安全的字元，客戶必須在將參數傳遞至 SDK 前將其編碼。

   * 以下是此方法的語法:

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * 以下是此方法的範例程式碼:

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   傳送具有特徵的訊號給對象管理，並取得區塊回撥中傳回的相符區段。

   * 以下是此方法的語法:

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * 以下是此方法的範例程式碼:

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
