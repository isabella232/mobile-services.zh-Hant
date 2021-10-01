---
description: 可協助您從指令碼呼叫外掛程式的資訊。
keywords: 沙馬林
solution: Experience Cloud
title: 對程式庫進行呼叫
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# 對程式庫進行呼叫{#making-calls-to-the-library}

此資訊可協助您從指令碼呼叫外掛程式。

當您想從指令碼對外掛程式進行呼叫時，必須匯入命名空間。

使用`Com.Adobe.Mobile`:

* **iOS**:匯入命名空間後，您可以透過類別中的靜態方法直接對SDK進行 `ADBMobile` 呼叫。

* **Android**:您可以透過類別中的靜態方法直接對SDK進行呼 `Config/Analytics/Target/AudienceManager/Media`叫。
