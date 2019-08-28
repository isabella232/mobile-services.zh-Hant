---
description: '此資訊可協助您實施 Android 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。'
keywords: Android；資料庫；行動；sdk
seo-description: '此資訊可協助您實施 Android 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。'
seo-title: 核心實施與生命週期
solution: Marketing Cloud、Analytics
title: 核心實施與生命週期
topic: 開發人員和實施
uuid: af4d11ac-8245-46a0-9b3a-4a-4a29cfbbb2
translation-type: tm+mt
source-git-commit: c4da3599c858bfbccb7af954df75f94eb7d8e99a

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

此資訊可協助您實施 Android 資料庫並收集生命週期量度 (例如: 啟動、升級、工作階段、參與的使用者等等)。

## 下載 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>若要下載SDK，您必須使用Android2.2或更新版本。

1. 請完成以下區段中的步驟，以設定開發報表套裝和下載預先填入版本的設定檔案:

   * [建立報表套裝](/help/android/getting-started/requirements.md)
   * [下載 SDK](/help/android/getting-started/requirements.md)

1. 下載並解壓縮 `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` 檔案並確認下列軟體元件存在：

   * `adobeMobileLibrary.jar`這個資料庫將會與Android裝置和模擬器搭配使用。

   * `ADBMobileConfig.json`，此元件為根據您應用程式自訂的 SDK 設定檔案。
   >[!IMPORTANT]
   >
   >If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, and you want to set up a development report suite and download a pre-populated version of the configuration file, see [Before You Start](/help/android/getting-started/requirements.md).

## Add the SDK and config file to your IntelliJ IDEA or Eclipse project {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA專案**

新增 SDK 和設定檔案至您的專案:

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.

1. 在專案導覽面板中，以滑鼠右鍵按一下您的專案。
1. Select **[!UICONTROL Open Module Settings]**.
1. Under **[!UICONTROL Project Settings]**, select **[!UICONTROL Libraries]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. 選取 **[!UICONTROL Java]** 並導覽至 `adobeMobileLibrary.jar` 檔案。
1. 選取您計劃使用行動資料庫所在的模組。
1. 按一下&#x200B;**[!UICONTROL 「套用」]**&#x200B;與&#x200B;**[!UICONTROL 「確定」]，以關閉「模組設定」視窗。**

**Eclipse專案**

新增 SDK 和設定檔案至您的專案:

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.
1. In **[!UICONTROL Eclipse IDE]**, right-click the project name.
1. Click  **[!UICONTROL Build Path]** &gt; **[!UICONTROL Add External Archives]**.
1. 選擇 `adobeMobileLibrary.jar`.
1. Click **[!UICONTROL Open]**.
1. Right-click the project again and select **[!UICONTROL Build Path]** &gt; **[!UICONTROL Configure Build Path]**.
1. 在&#x200B;**[!UICONTROL 「排序和匯出」]**&#x200B;標籤上，確認已選取 **`adobeMobileLibrary.jar`。**

## Add app permissions {#section_2EAF73ABF6424647B219A63B33B02CD5}

AppMeasurement 資料庫需要下列權限，才能傳送資料及記錄離線追蹤呼叫:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

若要新增這些權限，請在位於應用程式專案目錄的 `AndroidManifest.xml` 檔案中新增下列行:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Set the application context {#set-application-context}

您應在主要活動的 `onCreate` 方法中加入下列程式碼：

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
````

## Implement lifecycle metrics {#section_BA686C09021F474AADDE8690BBB910F7}

啟用生命週期後，每當您的應用程式啟動時，就會傳送一次點擊以測量啟動數、升級數、工作階段數、參與使用者數，以及許多其他量度。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

**請在應用程式的各活動中完成下列步驟:**

1. 匯入資料庫:

   ```java
   import com.adobe.mobile.*;
   ```

1. 在 `onResume` 函式中，啟動生命週期資料集合:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. 在 `onPause` 函式中，暫停生命週期資料集合:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>您必須將這些呼叫新增至每個活動，以確保正確的當機報告。如需詳細資訊，請參閱 [追蹤應用程式當機](/help/android/analytics-main/crashes.md)。

## 包含其他資料與生命週期呼叫

若要納入其他資料與生命週期量度呼叫，請將其他參數傳遞至包含內容資料的 `collectLifecycleData`:

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

與 `collectLifecycleData` 一併傳送的其他內容資料值，必須對應至 Adobe Mobile Services 中的自訂變數:

![](assets/map-variable-lifecycle.png)

系統會自動收集其他生命週期量度。如需詳細資訊，請參閱[生命週期量度](/help/android/metrics.md)。

## 後續步驟 {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

完成下列作業:

* [追蹤應用程式狀態](/help/android/analytics-main/states.md)
* [追蹤應用程式動作](/help/android/analytics-main/actions.md)

