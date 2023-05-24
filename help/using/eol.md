---
title: Adobe Mobile Services生命週期結束常見問題集
description: 取得有關Adobe Mobile Services生命週期結束公告常見問題的解答。
exl-id: c5f44341-7b87-4530-b86e-17e2911a7959
source-git-commit: c349c0f83df9d42b61a419ae71d6d2b67c5f7819
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 4%

---

# Adobe Mobile Services生命週期結束常見問題集

Adobe行動服務的生命週期結束日期為 **2022年12月31日**.

## 發生什麼事了？

Mobile Services的生命週期將於2022年12月31日結束。 Mobile Services支援以行動裝置為中心的UI、贏取、深層連結、應用程式內傳訊、推播通知和地理位置，目前不再支援。

## 包含哪些專案，未包含哪些專案？

此終止服務僅包括Adobe Mobile Services，此為的獨立平台 [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). 依賴此介面的Mobile第4版SDK已於2021年8月31日淘汰。

此次終止服務不包含適用於行動應用程式的Adobe Analytics (屬於Adobe Experience Platform Mobile SDK)。 這些功能（包括應用程式內行為、生命週期分析、訊息互動追蹤和受眾設定檔）繼續獲得Adobe的支援。

## 為何要淘汰此功能？

隨著Adobe持續擴充其行動行銷功能，Mobile Services先前提供的功能將以Adobe Experience Cloud解決方案發行，或透過Adobe Exchange主要合作夥伴提供。 此轉換提供您更強大且更彈性的行動行銷功能。

## 在Mobile Services中建立的現有處理規則有何改變？

[處理規則](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) 在Mobile Services使用者介面中建立或產生的專案，將會在Mobile Services生命週期結束日期前自動移轉至Adobe Analytics。 已移轉的處理規則的行為類似於Adobe Analytics中的其他處理規則，您可以在其中自由檢視或編輯這些規則。 此移轉不需要使用者採取任何動作。

Mobile Services失效後，所有處理規則邏輯都將在Adobe Analytics中專門處理，通常包括使用 [內容資料變數](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=zh-Hant).

## 有哪些轉變選項可用？

Adobe根據您組織的使用案例，提供三種轉變路徑。

1. **應用程式內訊息和推播通知**：Adobe可將您的傳訊工作流程轉變為Adobe Journey Optimizer。 此產品可協助組織最佳化及個人化整個客戶歷程中的體驗，包括行動訊息。
1. **贏取和深層連結**：贏取和深層連結可透過AdobeExchange Premier Partners計畫提供。 Adobe的合作夥伴團隊可以適當介紹，以確保您找到最符合需求的解決方案。
1. **Places Service**：Places Service提供免費的地理位置功能。 請參閱 [Places Service檔案](https://experienceleague.adobe.com/docs/places/using/home.html).

## 如有疑問，請前往何處？

請參閱 [AdobeMobile Services生命週期結束Spark頁面](https://spark.adobe.com/page/C6D30y09zaRpD/) 以取得詳細資訊。 如有任何其他問題，請聯絡您的Adobe代表。
