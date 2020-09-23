---
description: Windows 8.1通用應用程式商店程式庫提供的Audience Manager方法清單。
seo-description: Windows 8.1通用應用程式商店程式庫提供的Audience Manager方法清單。
seo-title: Audience Manager 方法
solution: Experience Cloud,Analytics
title: Audience Manager 方法
topic: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 45%

---


# Audience Manager 方法 {#audience-manager-methods}

Windows 8.1通用應用程式商店程式庫提供的Audience Manager方法清單。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target和Audience Manager。 各方法會根據解決方案加上前置詞。Audience Manager方法會加上前置詞&quot;AudienceManager&quot;。

>[!NOTE]
>
>當您從winJS(JavaScript)使用winmd方法時，所有方法都會自動將其第一個字母小寫。

如果在您的JSON檔案中設定了觀眾管理員，則包含生命週期度量的訊號會隨生命週期點擊傳送。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   傳回最近取得的訪客描述檔。Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * 此方法的語法如下：

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid(winJS:getDpid)**

   傳回目前的 DPID。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var dpid = ADB.AudienceManager.getDpid();
      ```

* **GetDpuuid(winJS:getDpuuid)**

   傳回目前的 DPUUID。

   * 此方法的語法如下：

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid(winJS:setDpidAndDpuuid)**

   設定 DPID 和 DPUUID。若已設定 DPID 和 DPUUID，則會與各訊號一併傳送。

   * 此方法的語法如下：

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData(winJS:signalWithData)**

   傳送具有特徵的訊號給Audience Manager，並取得區塊回呼中傳回的相符區段。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

