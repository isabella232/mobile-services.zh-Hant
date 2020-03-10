---
description: 此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。
keywords: Unity
seo-description: 此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。
seo-title: iOS 和 Android 4.x SDK 適用的 Unity 外掛程式
solution: Marketing Cloud,Developer
title: iOS 和 Android 4.x SDK 適用的 Unity 外掛程式
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# iOS 和 Android 4.x SDK 適用的 Unity 外掛程式 {#unity-plug-in-for-the-ios-and-android-x-sdks}

此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。

Last Update: **March 10, 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## 快速入門 {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

從GitHub下載ADBMobile.unitypackage檔案。

Below are the contents of the `ADBMobile.unitypackage` file:

* 資產 (root)

   * ADBMobile

   * 外掛程式

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * 資產

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**可選資料夾**:Demo資 *料夾包含* Unity場景和范常式式碼。

## 匯入 ADBMobile 外掛程式至 Unity 專案 {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. 開啟 Unity 專案。
1. 按兩下 **[!UICONTROL ADBMobile.unitypackage]**。
1. 選取您要匯入的資料夾。
