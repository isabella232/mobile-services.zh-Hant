---
description: 虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。這可讓使用者在一個報表套裝中維護資料，但管理資料如同獨立報表套裝一樣。
seo-description: 虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。這可讓使用者在一個報表套裝中維護資料，但管理資料如同獨立報表套裝一樣。
seo-title: 虛擬報表套裝
title: 虛擬報表套裝
uuid: 3f467cadp-43e7-4cd0-889b-89f8c61fbbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。這可讓使用者在一個報表套裝中維護其資料，但管理資料如同獨立報表套裝一樣。

使用VRSS的應用程式執行的動作與使用一般報表套裝的應用程式相同，但管理下列功能除外：

* 處理規則
* evars/props/listvars/事件
* 啓用時間戳記選項
* 維度旗標 (生命週期、位置等等)
* 分類

這些值在上層報表套裝中受到管理，並會與屬於同一個上層報表套裝的 VRS 共用。

可在Adobe Mobile Services UI中存取下列區域，不受父報表套裝的限制：

* 配置檔案
* 管理地標
* 管理連結目的地
* 管理回傳
* 訊息連結
* 贏取

VRS可協助您完成下列工作：

* 限制資料存取權

   一家跨國公司的應用程式會將資料傳送至所有地理位置的報表套裝，但是，公司想要限制某個地區的商業使用者檢視另一地區的資料。該公司的管理員可建立VRS以依地區區分使用者，並僅授予VRS給負責管理地區的商業使用者。

   這種限制方式能避免商務使用者檢視與其在所地區無關的資料。例如，EMEA的商業使用者不需要查看APAC地區的資料。

* 允許控制應用程式內/推送訊息、位置POI、贏取和回傳，並將所有資料傳送至一個報表套裝。

   跨國公司想要將所有資料都傳送至所有地理位置的同一個報表套裝，不過，公司希望每個地區的行銷團隊都能處理自己的應用程式內/推送訊息。公司的管理員可以建立地區性VRSS，而且每個團隊都可以根據該VRS來管理自己的應用程式。

   地區團隊會使用 VRS 的配置檔案來建立他們的應用程式。資料會傳送至父報表套裝，而應用程式內/推送訊息、位置POI、贏取和回傳則會控制在VRS建立的應用程式中。

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>只有Adobe Analytics管理員可以在Adobe Analytics中建立及修改虛擬報表套裝。To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

每個 VRS 都有唯一的 ID。若要在Adobe Mobile Services **[!UICONTROL UI中檢視父報表套裝ID，請在「管理應用程式設定」頁面中，按一下]****[!UICONTROL 「更多詳細資料]**」。

在 Adobe Mobile Services UI 中，您可以使用 VRS 針對組織中的特定群組建立應用程式和區段資料。舉例來說，位於西班牙的商務使用者無法看到與日本商務使用者相關的資料。

>[!TIP]
>
>您無法修改父報表套裝繼承的值。

VRS 是附於上層報表套裝的伺服器端區段定義，因此您無法對 VRS 執行資料收集，因為 SDK 只會傳送點擊至上層報表套裝，VRS 則反過來記錄點擊。

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

在Adobe Mobile Services中，您可以根據父報表套裝或虛擬報表套裝建立應用程式。依據虛擬報表套裝建立應用程式時，我們建議您按應程式的定義來調整 VRS 區段。

>[!TIP]
>
>推播認證會附加在Mobile Services UI的應用程式層級。

若要確定您是否正確傳送推送訊息，請務必正確定義對象區段。如需詳細資訊，請參閱 [對象: 定義和設定推送訊息的對象區段](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

「管理應用程式設定」頁面上的時區屬性與您用來在Adobe Analytics中建立VRS的時區屬性不同。「管理應用程式設定」頁面的時區屬性繼承自上層報表套裝，用於傳送資料到 Adobe Analytics。在Adobe Analytics中建立VRS時所指定的屬性可用來顯示Mobile Services UI中的報表，而且可能與父報表套裝不同。

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

若要在建立應用程式時使用 VRS，請在&#x200B;**「應用程式資訊」頁面的「報表套裝」**&#x200B;下拉式清單中選取 VRS。該清單含有上層和虛擬報表套裝。

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

下列是 VRS 的屬性:

>[!TIP]
>
>唯讀屬性是從父報表套裝繼承。

| 屬性 | 繼承自上層報表套裝 | 可編輯? | 附註 |
|--- |--- |--- |--- |
| `target.clientCode` | 否 | 有 |  |
| `target.timeout` | 否 | 有 |  |
| `audienceManager.server` | 否 | 是 |  |
| `audienceManager.analyticsForwardingEnabled` | 是 | 是 |  |
| `audienceManager.timeout` | 否 | 有 |  |
| `acquisition.server` | 否 | 否 |  |
| `acquisition.appid` | 否 | 否 |  |
| `analytics.rsids` | 有 | 否 |  |
| `analytics.server` | 否 | 否 |  |
| `analytics.ssl` | 否 | 是 |  |
| `analytics.offlineEnabled` | 是 |  |  |
| `analytics.charset` | 是 | 否 |  |
| `analytics.lifecycleTimeout` | 否 | 是 | 如果使用者不希望資料不一致，則應為上層報表套裝。 |
| `analytics.privacyDefault` | 否 | 有 |  |
| `analytics.batchLimit` | 否 | 是 |  |
| `analytics.timezone` | 是 | 是，在您首次建立應用程式時。 | 此時區屬性用於傳送資料至 Adobe Analytics，而且與 VRS 建立時設定的時區屬性不同。 |
| `analytics.timezoneOffset` | 有 | 否 |  |
| `analytics.referrerTimeout` | 否 | 是 |  |
| `analytics.backdateSessionInfo` | 是 | 是 |  |

## 其他資訊 {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

以下是關於虛擬報表套裝的一些其他資訊：

* 如需 VRS 的詳細資訊，請參閱[虛擬報表套裝](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html)。
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).