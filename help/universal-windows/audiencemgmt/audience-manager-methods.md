---
description: 通用Windows平台庫提供的Audience Manager方法清單。
solution: Experience Cloud,Analytics
title: Audience Manager 方法
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 44%

---

# Audience Manager 方法{#audience-manager-methods}

通用Windows平台庫提供的Audience Manager方法清單。

SDK目前支援多個Adobe Experience Cloud解決方案，包括Analytics、Target和Audience Manager。 各方法會根據解決方案加上前置詞。Audience Manager方法的前置詞為`AudienceManager`。

>[!TIP]
>
>當您從winJS(JavaScript)使用`winmd`方法時，所有方法都會自動將其第一個字母小寫。

如果已在您的JSON檔案中設定audience manager，則包含生命週期量度的訊號會與生命週期點擊一併傳入。

* **GetVisitorProfile(winJS:getVisitorProfile)**

   傳回最近取得的訪客描述檔。如果尚未提交任何訊號，則傳回`null`。 訪客設定檔會儲存在`SharedPreferences`中，方便您在多次啟動應用程式時存取。

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

* **SignalWithData(winJS:signalWithData)**

   傳送具有特徵的訊號給對象管理，並取得區塊回撥中傳回的相符區段。

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
