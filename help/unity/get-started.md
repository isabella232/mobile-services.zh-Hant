---
description: 此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。
keywords: Unity
seo-description: 此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。
seo-title: iOS 和 Android 4.x SDK 適用的 Unity 外掛程式
solution: Marketing Cloud，開發人員
title: iOS 和 Android 4.x SDK 適用的 Unity 外掛程式
uuid: 83289a73-982d-4472-a8 c8-00b562 dc80 f
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# iOS 和 Android 4.x SDK 適用的 Unity 外掛程式 {#unity-plug-in-for-the-ios-and-android-x-sdks}

此外掛程式可讓您從 Unity 應用程式傳送 Adobe Analytics 呼叫。

上次更新: **2016 年 10 月 20 日**

## 入門 {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

從 GitHub 或 Developer Connection 下載 [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 檔案。

以下是 `ADBMobile.unitypackage` 檔案的內容：

* 資產 (root)

   * ADBMobile

      * 示範

         * ADBMobileDemo.cs
         * BooDemo.boo
         * BooScene.unity
         * CSharpScene.unity
         * JavaScriptDemo.js
         * JavaScriptScene.unity
         * SecondScene.unity
         * SecondSceneScript.cs
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



可選資料夾: Demo 資料夾包含每個受支援指令碼語言的 Unity 場景和範例程式碼。

## 匯入 ADBMobile 外掛程式至 Unity 專案 {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. 開啟 Unity 專案。
1. Double-click **[!UICONTROL ADBMobile.unitypackage]**.
1. 選取您要匯入的資料夾。

