---
description: 通用Windows平台庫提供的Audience Manager方法清單。
solution: Experience Cloud Services,Analytics
title: Audience Manager 方法
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 44%

---

# Audience Manager 方法{#audience-manager-methods}

通用Windows平台庫提供的Audience Manager方法清單。

SDK當前支援多個Adobe Experience Cloud解決方案，包括分析、目標和Audience Manager。 根據解預先確定方法。Audience Manager方法的前置詞為 `AudienceManager`。

>[!TIP]
>
>消費時 `winmd` 來自winJS(JavaScript)的方法，所有方法的首字母都自動小寫。

如果在JSON檔案中配置了受眾管理器，則包含生命週期度量的信號會隨您的生命週期命中而發送。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   傳回最近取得的訪客描述檔。返回 `null` 的下界。 訪問者配置檔案保存在 `SharedPreferences` 可輕鬆訪問多個應用程式。

   * 此方法的語法如下：

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
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

   向受眾管理發送具有特徵的信號，並在塊回調中獲取返回的匹配段。

   * 此方法的語法如下：

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * 此方法的程式碼範例如下：

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      });
      ```
