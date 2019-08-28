---
description: 此資訊可協助您了解當機追蹤方式，以及處理錯誤當機的最佳實務。
seo-description: 此資訊可協助您了解當機追蹤方式，以及處理錯誤當機的最佳實務。
seo-title: 追蹤應用程式當機
solution: Marketing Cloud、Analytics
title: 追蹤應用程式當機
topic: 開發人員和實施
uuid: 3ab98c14-cdf-4060-ad88-ec07 c1 c6 f07
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 追蹤應用程式當機 {#track-app-crashes}

此資訊可協助您了解當機追蹤方式，以及處理錯誤當機的最佳實務。

>[!TIP]
>
>應用程式當機是生命週期度量的一部分。在追蹤當機之前，請將程式庫新增至您的專案並實施生命週期。如需詳細資訊，請參閱 *核心實作與生命週期* 中 [的新增SDK和設定檔案至IntelliJ IDEA或Eclipse專案](/help/android/getting-started/dev-qs.md)。

實施生命週期量度時，會呼叫各活動之 `Config.collectLifecycleData` 方法中的 `OnResume`。In the `onPause` method, a call is made to `Config.pauseCollectingLifeCycleData`.

在 `pauseCollectingLifeCycleData` 中，會設定標記指示順利結束。當應用程式重新啟動或繼續執行時，`collectLifecycleData` 會檢查此標記。如果應用程式並未依標記狀態判定為順利結束，則會傳送 `a.CrashEvent` 內容資料與下個呼叫，並回報當機事件。

若要確認當機報告準確，您必須呼叫各活動之 `pauseCollectingLifeCycleData` 方法中的 `onPause`。若要瞭解此為至關重要的原因，以下是 Android 活動生命週期的圖說。

![](assets/android-lifecycle.png)

如需有關 Android 活動生命週期的詳細資訊，請參閱[活動](https://developer.android.com/guide/components/activities.html)。

*此 Android 生命週期圖說是由[Android Open Source Project 建立和共用](https://source.android.com/)，並根據[Creative Commons 2.5 屬性授權](https://creativecommons.org/licenses/by/2.5/)中的條款來使用。*

## 導致回報錯誤當機的原因為何?

1. 如果您正使用 IDE (例如 Android Studio) 進行偵錯，當應用程式於前景執行時，從 IDE 重新啟動應用程式會造成當機。

   >[!TIP]
   >
   >您可以在從IDE再次啓動應用程式之前，先接地應用程式以避免此次損毀。

1. If the last foreground Activity of your app is backgrounded and does not call `Config.pauseCollectingLifecycleData();` in `onPause`, and your app is manually closed or killed by the OS, the next launch results in a crash.

## 該如何處理片段?

各片段中皆有與活動類似的應用程式生命週期事件。然而，如果片段未連接至活動，則無法使用。

>[!IMPORTANT]
>
>您需要依賴生命週期事件，因為包含活動的活動可執行您的程式碼。這將由片段的上層檢視處理。

## (選擇性)實作活動生命週期回呼

自 API Level 14 開始，Android 允許活動的全域生命週期回撥。For more information, see [Application](https://developer.android.com/reference/android/app/Application).

You can use these callbacks to ensure that all of your Activities correctly call `collectLifecycleData()` and `pauseCollectingLifecycleData()`. 您僅需要將此程式碼新增至應用程式可能會在其中啟動的主要活動與任何其他活動:

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

To send additional context data with your lifecycle call by using `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`, you must override the `onResume` method for that Activity and ensure that you call `super.onResume()` after manually calling `collectLifecycleData`.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```

