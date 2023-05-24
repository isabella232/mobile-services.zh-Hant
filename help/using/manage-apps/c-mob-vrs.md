---
description: 虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。這讓使用者可以在一個報表套裝裡保管其資料，但做法就像在個別報表套裝中管理資料。
title: 虛擬報表套裝
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
exl-id: c9ce7f7c-2023-4a9d-9e4d-bacc21f9ad40
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 73%

---

# 虛擬報表套裝 {#virtual-report-suites}

{#eol}

虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。這讓使用者可以在一個報表套裝裡保管其資料，但做法就像在個別報表套裝中管理資料。

使用 VRS 的應用程式與使用一般報表套裝的應用程式功能相同，只有管理下列功能的方式有所差異:

* 處理規則
* eVars/props/listvars/events
* 啟用時間戳記的選項
* Dimension標幟（生命週期、位置等）
* 分類

這些值會在父報表套裝中進行管理，並與屬於相同父報表套裝的VRS共用。

下列是可以在 Adobe Mobile Services 使用者介面存取的區域，不受上層報表套裝所影響:

* 設定檔
* 管理地標
* 管理連結目的地
* 管理回傳
* 訊息連結
* 贏取

VRS 可協助您完成下列作業:

* 限制資料存取

   跨國公司有一個應用程式，可將所有地理位置的資料傳送至報表套裝。 但是，這家公司想要限制某一地區的商務使用者，讓他們無法檢視另一地區的資料。該公司的管理員可以建立 VRS，依地區將使用者區隔開來，並只向管理該地區的商務使用者授與 VRS 的權限。

   這種限制方式能避免商務使用者檢視與其在所地區無關的資料。舉例來說，位於 EMEA 的商務使用者不需要看到 APAC 地區的資料。

* 允許控制傳送至一個報表套裝的資料之應用程式內/推送訊息、位置 POI、贏取和回傳。

   跨國公司想要將所有資料都傳送至所有地理位置的同一個報表套裝，但是，這家公司想要每個地區的行銷團隊各自處理其相關的應用程式內/推送訊息。該公司的管理員可以建立地區 VRS，讓每個團隊可以依據該 VRS 管理其個別的應用程式。

   地區團隊會使用 VRS 的配置檔案來建立他們的應用程式。資料會傳送至上層報表套裝，但應用程式內/推送訊息、位置 POI、贏取和回傳會由 VRS 建立的應用程式控制。

## 在 Adobe Analytics 中建立虛擬報表套裝 {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>只有 Adobe Analytics 管理員可以在 Adobe Analytics 中建立和修改虛擬報表套裝。若要建立虛擬報表套裝，請參閱 [建立虛擬報表套裝](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html?lang=zh-Hant) (位於Adobe Analytics檔案中)。

每個 VRS 都有唯一的 ID。若要在 Adobe Mobile Services 使用者介面中檢視上層報表套裝 ID，請在「管理應用程式設定」頁面的&#x200B;**[!UICONTROL 應用程式資訊]**&#x200B;區段中，按一下&#x200B;**[!UICONTROL 更多詳情]**。

在AdobeMobile Services使用者介面中，您可以使用VRS建立應用程式，並將資料區段至組織中的特定群組。 舉例來說，如此一來，西班牙的商業使用者便看不到與日本商業使用者相關的資料。

>[!TIP]
>
>您無法修改從上層報表套裝繼承的值。

VRS是附加至父報表套裝的伺服器端區段定義。 因此，您無法對VRS執行資料收集，因為SDK只會將點選傳送至父報表套裝，而父報表套裝會記錄點選。

## Adobe Mobile Services 的虛擬報表套裝與資料收集 {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

在 Adobe Mobile Services 中，您可以依據上層報表套裝或虛擬報表套裝建立應用程式。依據虛擬報表套裝建立應用程式時，我們建議您按應程式的定義來調整 VRS 區段。

>[!TIP]
>
>在 Mobile Services 使用者介面中，推送認證會附加於應用程式層級。

為確保推送訊息正確傳送，必須正確定義對象區段。 如需詳細資訊，請參閱 [對象：定義並設定推送訊息的對象區段](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## 瞭解時區 {#section_498E1EED22D741C3BDED44F01FACA72A}

「管理應用程式設定」頁面上的時區屬性，與您在 Adobe Analytics 中建立 VRS 時所用的時區屬性並不相同。「管理應用程式設定」頁面的時區屬性繼承自上層報表套裝，用於傳送資料到 Adobe Analytics。您在 Adobe Analytics 建立 VRS 時指定的屬性，用於顯示 Mobile Services 使用者介面中的報表，且可能與上層報表套裝不同。

## 在 Mobile Services 使用者介面中選取虛擬報表套裝 {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

若要在建立應用程式時使用 VRS，請在&#x200B;**[!UICONTROL 「應用程式資訊」頁面的]**「報表套裝」下拉式清單中選取 VRS。該清單含有上層和虛擬報表套裝。

>[!IMPORTANT]
>
>若要從清單中選取 VRS，請找到帶有藍點的選項和 `vrs_` *`<company_name>`*`_`*`<unique name>`*   命名慣例。

## 虛擬報表套裝屬性 {#section_20ECE6243F664C4FB4347ADB4FF0458A}

下列是 VRS 的屬性:

>[!TIP]
>
>唯讀屬性繼承自上層報表套裝。

| 屬性 | 繼承自父報告套裝 | 可編輯？ | 附註 |
|--- |--- |--- |--- |
| `target.clientCode` | 無 | 是 |  |
| `target.timeout` | 無 | 是 |  |
| `audienceManager.server` | 無 | 是 |  |
| `audienceManager.analyticsForwardingEnabled` | 是 | 是 |  |
| `audienceManager.timeout` | 無 | 是 |  |
| `acquisition.server` | 無 | 無 |  |
| `acquisition.appid` | 無 | 無 |  |
| `analytics.rsids` | 是 | 無 |  |
| `analytics.server` | 無 | 無 |  |
| `analytics.ssl` | 無 | 是 |  |
| `analytics.offlineEnabled` | 是 |  |  |
| `analytics.charset` | 是 | 無 |  |
| `analytics.lifecycleTimeout` | 無 | 是 | 如果使用者不希望他們的資料不一致，則應為父報表套裝。 |
| `analytics.privacyDefault` | 無 | 是 |  |
| `analytics.batchLimit` | 無 | 是 |  |
| `analytics.timezone` | 是 | 是，當您首次建立應用程式時。 | 此時區屬性用於傳送資料至Adobe Analytics，與建立VRS時設定的時區屬性不同。 |
| `analytics.timezoneOffset` | 是 | 無 |  |
| `analytics.referrerTimeout` | 無 | 是 |  |
| `analytics.backdateSessionInfo` | 是 | 是 |  |

## 其他資訊 {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

以下是虛擬報表套裝的其他資訊:

* 如需VRS的詳細資訊，請參閱 [虛擬報表套裝概觀](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html?lang=zh-Hant).
* 如需規劃 VRS 實作的詳細資訊，請參閱[虛擬報表套裝工作流程](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html)。
