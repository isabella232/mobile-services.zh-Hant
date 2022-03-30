---
description: 從指令碼調用庫插件。
keywords: Unity
solution: Experience Cloud Services
title: 對程式庫進行呼叫
uuid: 74c30379-6cdf-4318-9db8-e14fb63aa18a
exl-id: de95edd5-3a5b-4b84-aeea-adff3362f544
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 18%

---

# 對程式庫進行呼叫{#making-calls-to-the-library}

當要從指令碼調用插件時，請導入命名空間：

* **C#:** 使用 `com.adobe.mobile;`

導入命名空間後，可以通過ADBMobile類的靜態方法直接調用插件。
