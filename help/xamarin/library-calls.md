---
description: 協助您從指令碼對外掛程式進行呼叫的資訊。
keywords: Xamarin
seo-description: 此資訊有助您從指令碼對外掛程式發出呼叫。
seo-title: 對程式庫進行呼叫
solution: Marketing Cloud，開發人員
title: 對程式庫進行呼叫
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

此資訊可協助您從指令碼對外掛程式進行呼叫。

當您想從指令碼對外掛程式進行呼叫時，必須匯入命名空間。

`Com.Adobe.Mobile`透過：

* **iOS**：匯入命名空間後，您可以透過 `ADBMobile` 類別中的靜態方法直接對SDK進行呼叫。

* **Android**：您可以透過 `Config/Analytics/Target/AudienceManager/Media`類別中的靜態方法直接對SDK進行呼叫。

