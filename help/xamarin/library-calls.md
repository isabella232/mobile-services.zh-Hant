---
description: 幫助您從指令碼調用插件的資訊。
keywords: 沙馬林
solution: Experience Cloud Services
title: 對程式庫進行呼叫
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# 對程式庫進行呼叫{#making-calls-to-the-library}

此資訊可幫助您從指令碼調用插件。

當要從指令碼調用插件時，必須導入命名空間。

使用 `Com.Adobe.Mobile`:

* **iOS**:導入命名空間後，可以通過中的靜態方法直接調用SDK `ADBMobile` 類。

* **安卓**:您可以通過中的靜態方法直接調用SDK `Config/Analytics/Target/AudienceManager/Media`類。
