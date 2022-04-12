---
title: AdobeMobile服務停產常見問題
description: 獲取有關Adobe移動服務產品壽命終止公告的常見問題的答案。
exl-id: c5f44341-7b87-4530-b86e-17e2911a7959
source-git-commit: a6dd74b8df771249e3c50de93f44639cfbfe7e13
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 2%

---

# AdobeMobile服務停產常見問題

Adobe移動服務的終止日期是 **2022年12月31日**。

## 怎麼了？

移動服務於2022年12月31日終了。 此日期後不再支援支援以移動為中心的UI、獲取、深度連結、應用內消息、推送通知和地理位置的移動服務。

## 包括哪些內容，不包括哪些內容？

此終止版僅包括Adobe移動服務，該平台位於 [移動營銷.adobe.com](https://mobilemarketing.adobe.com)。 依賴此介面的移動版本4 SDK於2021年8月31日落日。

這種壽命終結不包括Adobe Analytics的移動應用程式，這是Adobe Experience Platform移動軟體開發工具包的一部分。 這些功能（包括應用程式內行為、生命週期分析、消息交互跟蹤和受眾配置檔案）繼續從Adobe獲得支援。

## 為什麼要淘汰此功能？

隨著Adobe繼續擴展其移動營銷能力，以前在移動服務中提供的功能將在Adobe Experience Cloud解決方案中發佈，或通過AdobeExchange Premier合作夥伴提供。 此過渡為您提供了更強大、更靈活的移動營銷功能。

## 在移動服務中建立的現有處理規則會如何？

[處理規則](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) 在移動服務UI中建立或生成的UI將在移動服務終止日期之前自動遷移到Adobe Analytics。 遷移的處理規則與Adobe Analytics的其他處理規則的行為類似，在那裡您可以自由查看或編輯它們。 此遷移不需要用戶操作。

移動服務失效後，所有處理規則邏輯將在Adobe Analytics內完全處理，通常包括使用 [上下文資料變數](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=zh-Hant)。

## 有哪些過渡選項可用？

Adobe根據組織的使用案例提供三條過渡路徑。

1. **應用內消息傳遞和推送通知**:Adobe可以將消息傳遞工作流轉換到Adobe Journey Optimizer。 此產品可幫助組織優化和個性化整個客戶旅程中的體驗，包括移動消息傳遞。
1. **獲取和深度連結**:通過AdobeExchange Premier Partners計畫提供收購和深度連結。 這些合作夥伴包括Adjust、AppsFlyer和Branch，它們提供廣泛的收購能力。 Adobe的合作夥伴團隊可以進行適當的介紹，以確保您找到最適合您需要的解決方案。
1. **位置服務**:Places Service提供免費的地理位置功能。 查看 [Places服務文檔](https://experienceleague.adobe.com/docs/places/using/home.html)。

## 如果有問題，我可以去哪？

查看 [Adobe移動服務壽命結束Spark頁](https://spark.adobe.com/page/C6D30y09zaRpD/) 的子菜單。 如有其他問題，請與Adobe代表聯繫。
