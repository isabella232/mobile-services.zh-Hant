---
description: Windows 8.1通用App Store庫提供的Audience Manager方法清單。
solution: Experience Cloud Services,Analytics
title: Audience Manager 方法
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 46%

---

# Audience Manager 方法 {#audience-manager-methods}

Windows 8.1通用App Store庫提供的Audience Manager方法清單。

SDK當前支援多個Adobe Experience Cloud解決方案，包括分析、目標和Audience Manager。 各方法會根據解決方案加上前置詞。Audience Manager方法以「AudienceManager」為前置詞。

>[!NOTE]
>
>使用winJS(JavaScript)中的winmd方法時，所有方法的首個字母都會自動小寫。

如果在JSON檔案中配置了受眾管理器，則會在您的生命週期命中時發送包含生命週期度量的信號。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   傳回最近取得的訪客描述檔。返回 `null` 的下界。 訪問者配置檔案保存在 `SharedPreferences` 可輕鬆訪問多個應用程式。

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

* **SignalWithData(winJS:信號與資料)**

   發送具有特徵的信號Audience Manager，並獲取塊回調中返回的匹配段。

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
