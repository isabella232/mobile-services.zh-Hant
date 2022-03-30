---
description: 此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。
keywords: Unity
solution: Experience Cloud Services
title: iOS 和 Android 4.x SDK 適用的 Unity 外掛程式
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
exl-id: fdb012d0-64f5-4c63-96d7-508fef01041f
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 100%

---

# iOS 和 Android 4.x SDK 適用的 Unity 外掛程式 {#unity-plug-in-for-the-ios-and-android-x-sdks}

此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。

上次更新：**2020 年 3 月 10 日**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## 快速入門 {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

從 GitHub下載 ADBMobile.unitypackage 檔案。

該 `ADBMobile.unitypackage` 檔案的內容如下：

* Assets (root)

   * ADBMobile

   * 外掛程式

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * assets

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**選用資料夾**：*Demo* 資料夾內有 Unity 場景和範例程式碼。

## 將 ADBMobile 外掛程式匯入 Unity 專案 {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. 開啟 Unity 專案。
1. 按兩下 **[!UICONTROL ADBMobile.unitypackage]**。
1. 選取您要匯入的資料夾。
