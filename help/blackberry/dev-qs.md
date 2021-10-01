---
title: 開發人員快速入門
description: BlackBerry開發人員快速入門手冊可協助您了解為AdobeMobile Services實作BlackBerry程式庫的程式。
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# 開發人員快速入門

此資訊可協助您了解實作BlackBerry程式庫的程式。

## 取得SDK

**SDK需要BlackBerry 10或更新版本。**

解壓縮下載的SDK後，確認`AdobeMobile`資料夾中存在下列檔案：

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## 新增SDK至您的專案

1. 按一下右鍵您的項目，然後選擇&#x200B;**[!UICONTROL 配置]** > **[!UICONTROL 添加庫]**。
1. 選擇&#x200B;**[!UICONTROL 外部庫]**，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 按一下&#x200B;**[!UICONTROL Device library]**&#x200B;欄位旁的&#x200B;**[!UICONTROL Browse]** 。
1. 導覽至`ADBMobile-4.0.0BETA-BlackBerry`資料夾。
1. 在`Device-Debug`資料夾中，選擇`libADBMobileShared.so`並按一下&#x200B;**[!UICONTROL 開啟]**。
1. 按一下&#x200B;**[!UICONTROL 模擬器程式庫]**&#x200B;欄位旁的&#x200B;**[!UICONTROL 瀏覽]**。
1. 導覽至`ADBMobile-4.0.0BETA-BlackBerry`資料夾。
1. 在`Device-Debug`資料夾中，選擇`libADBMobileShared.so`並按一下&#x200B;**[!UICONTROL 開啟]**。
1. 按一下&#x200B;**[!UICONTROL Include folders]**&#x200B;欄位旁的&#x200B;**[!UICONTROL Add]** 。
1. 導覽至`ADBMobile-4.0.0BETA-BlackBerry`資料夾。
1. 將`public`資料夾新增至包含。
1. 在`ADBMobile-4.0.0BETA-BlackBerry`資料夾中，有一個名為`ADBMobileConfig.json`的`.json`配置檔案。

   將該檔案複製至專案的根目錄。
1. 按一下右鍵您的項目，然後選擇&#x200B;**[!UICONTROL 刷新]**。

   `.json`檔案現在應會顯示在您的&#x200B;**[!UICONTROL 專案總管]**&#x200B;中。
1. 開啟專案的`bar-descriptor.xml`檔案。
1. 在視窗底部選取&#x200B;**[!UICONTROL Assets]**&#x200B;標籤。
1. 確認已選取&#x200B;**[!UICONTROL （所有設定）]**，然後按一下視窗&#x200B;**[!UICONTROL Assets]**&#x200B;區段中的&#x200B;**[!UICONTROL 新增檔案]**。
   >[!TIP]
   >
   >QNX Momentics IDE中有時會阻止這些按鈕的顯示。 如果看不到按鈕，請調整窗口大小，直到它們出現。

1. 按一下&#x200B;**[!UICONTROL 工作區]**。
1. 在項目中查找`ADBMobileConfig.json`檔案，然後按一下&#x200B;**[!UICONTROL OK]**。

您的應用程式可以使用`#include <ADBMobile.hpp>`從`adobeMobileLibrary.jar`庫導入類/介面。

## 新增應用程式權限 

在項目目錄的`bar-descriptor.xml`中，添加行`<permission>access_internet</permission>`，或在QNX Momentics IDE中，在&#x200B;**[!UICONTROL Application]**&#x200B;頁簽的權限部分上選擇&#x200B;**[!UICONTROL Internet]**&#x200B;框。

## 更新`ADBMobileConfig.json`配置檔案

`ADBMobileConfig.json`檔案包含全域SDK設定。 您需要更新一些值才能開始使用。

以下是`ADBMobileConfig.json`檔案的範例：

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

您至少必須更新`rsids`和`server`參數。 如需詳細資訊，請參閱[Adobe行動類別和方法參考](/help/blackberry/methods.md)。

您現在可以在BlackBerry 10應用程式中實施Analytics。
