---
description: Windows 8.1 通用應用程式商店程式庫所提供的 Audience Manager 方法清單。
seo-description: Windows 8.1 通用應用程式商店程式庫所提供的 Audience Manager 方法清單。
seo-title: Audience manager方法
solution: Marketing Cloud,Analytics
title: Audience manager方法
topic: 開發人員和實施
uuid: e39c9c3e-fd53-4b46-8ff-88101a064a9c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods {#audience-manager-methods}

Windows 8.1 通用應用程式商店程式庫所提供的 Audience Manager 方法清單。

SDK 目前已支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target 以及 Audience Manager。各方法會根據解決方案加上前置詞。Audience Manager 方法會加上前置詞 "AudienceManager"。

>[!NOTE]
>
>當您從winJS(JavaScript)使用winmd方法時，所有方法都會自動將其第一個字母小寫。

如果您已在 JSON 檔案中設定 audience manager，則包含生命週期量度的訊號會與生命週期點擊一併傳送。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   傳回最近取得的訪客設定檔。如果尚未提交任何訊號，則傳回 `null`。訪客設定檔會儲存在 `SharedPreferences` 中，方便您在多次啟動應用程式時存取。

   * 以下是此方法的語法:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid(winJS:getDpid)**

   傳回目前的 DPID。

   * 以下是此方法的語法:

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile; 
      var dpid = ADB.AudienceManager.getDpid();
      ```

* **GetDpuuid(winJS:getDpuuid)**

   傳回目前的 DPUUID。

   * 以下是此方法的語法:

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid(winJS:setDpidAndDpuuid)**

   設定 DPID 和 DPUUID。若已設定 DPID 和 DPUUID，則會與各訊號一併傳送。

   * 以下是此方法的語法:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData(winJS:signalWithData)**

   傳送具有特徵的訊號給 Audience Manager，並取得區塊回撥中傳回的相符區段。

   * 以下是此方法的語法:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * 以下是此方法的範例程式碼:

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

