---
description: 以下資訊可協助您往返舊版贏取促銷活動連結 (根據裝置指紋)。
seo-description: 以下資訊可協助您往返舊版贏取促銷活動連結 (根據裝置指紋)。
seo-title: 測試舊版贏取
solution: Marketing Cloud、Analytics
title: 測試舊版贏取
uuid: e0591f4a-e26 b-4Fe4-97c1-a6831 a926 a
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Testing legacy acquisition {#testing-legacy-acquisition}

以下資訊可協助您往返舊版贏取促銷活動連結 (根據裝置指紋)。

如果行動應用程式尚未在 Google Play 上架，您可以選擇任一行動應用程式，作為建立促銷活動連結時的目的地。這只會影響贏取伺服器將您重新導向的應用程式 (在您點擊贏取連結後)，而不會影響測試贏取連結的能力。

1. Navigate to **[!UICONTROL Use Legacy Acquisition Links]** in Adobe Mobile Services and generate an acquisition campaign URL.

   如需詳細資訊，請參閱[使用舊版贏取連結](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)。

1. 在您要安裝應用程式的行動裝置上，按一下剛才產生的連結。

   Adobe 伺服器 (`c00.adobe.com`) 會儲存裝置指紋，然後重新導向至 App Store。您不必僅為了測試而下載應用程式。

1. 在您於步驟 2 中所使用的同一行動裝置上，首次啟動應用程式。

   確保以上過程順利進行最簡單的方式是，刪除應用程式並重新安裝。

請記住以下資訊:

* 贏取伺服器會根據連結點擊 (步驟 2) 和應用程式啟動時 (步驟 3) 所記錄的 IP 位址和使用者代理程式資訊，來提供屬性配對。
* 藉由使用 HTTP 監控工具，即可監控從應用程式傳送的點擊，以便提供贏取屬性的驗證。

>[!TIP]
>
>使用者代理程式中傳送的項目若有所不同，可能會造成屬性失效。
