---
description: 協助您從指令碼呼叫外掛程式的資訊。
keywords: Xamarin
seo-description: 協助您從指令碼呼叫外掛程式的資訊。
seo-title: 對程式庫進行呼叫
solution: Experience Cloud
title: 對程式庫進行呼叫
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 13%

---


# 對程式庫進行呼叫{#making-calls-to-the-library}

這項資訊可協助您從指令碼呼叫外掛程式。

當您要從指令碼對外掛程式進行呼叫時，必須匯入命名空間。

使用 `Com.Adobe.Mobile`:

* **iOS**:匯入命名空間後，您可透過類別中的靜態方法直接對SDK進行呼 `ADBMobile` 叫。

* **Android**:您可以透過類別中的靜態方法直接對SDK進行 `Config/Analytics/Target/AudienceManager/Media`呼叫。

