---
description: 虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。This allows users to maintain their data in one report suite but manage the data as if it were in separate report suites.
seo-description: 虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。這可讓使用者將資料維護在單一報表套裝中，但管理資料就像資料位於個別報表套裝一樣。
seo-title: 虛擬報表套裝
title: 虛擬報表套裝
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

虛擬報表套裝 (VRS) 是透過將一個或多個區段定義套用至報表套裝所建立的報表套裝。這可讓使用者將資料維護在單一報表套裝中，但管理資料就像是在個別報表套裝中一樣。

Apps that use VRSs do the same thing as apps that use a regular report suite, except for managing the following features:

* 處理規則
* evars/props/listvars/事件
* 啟用時間戳記的選項
* 維度旗標 (生命週期、位置等等)
* 分類

這些值在上層報表套裝中受到管理，並會與屬於同一個上層報表套裝的 VRS 共用。

在Adobe Mobile Services UI中可以存取下列區域，不受父報表套裝的限制：

* 配置檔案
* 管理地標
* 管理連結目的地
* 管理回傳
* 訊息連結
* 贏取

VRS可協助您完成下列工作：

* 限制資料存取權

   一家跨國公司的應用程式會將資料傳送至所有地理位置的報表套裝，不過，該公司希望限制某個地區的商業使用者檢視另一個地區的資料。 The company’s admin can create a VRS to segment users by region and give permission to the VRS only to the business user who manages the region.

   這種限制方式能避免商務使用者檢視與其在所地區無關的資料。例如，EMEA地區的企業使用者不需要查看亞太地區的資料。

* 允許控制應用程式內／推播訊息、位置POI、贏取和回傳，並將所有資料傳送至一個報表套裝。

   跨國公司想要將所有資料都傳送至所有地理位置的同一個報表套裝，不過，該公司希望每個地區的行銷團隊都能處理自己的應用程式內／推播訊息。 公司的管理員可以建立地區VRS，而每個團隊都可以根據該VRS管理自己的應用程式。

   地區團隊會使用 VRS 的配置檔案來建立他們的應用程式。資料會傳送至父報表套裝，但應用程式內／推播訊息、位置POI、贏取和回傳會在從VRS建立的應用程式中控制。

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Only Adobe Analytics admins can create and modify virtual report suites in Adobe Analytics. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

每個 VRS 都有唯一的 ID。若要在Adobe Mobile Services UI中檢視父報表套裝ID，請在「管理應用程式設定」頁面的「應用程式資訊」區 **[!UICONTROL 段中]** ，按一下「更 **[!UICONTROL 多詳細資訊」]**。

在 Adobe Mobile Services UI 中，您可以使用 VRS 針對組織中的特定群組建立應用程式和區段資料。舉例來說，位於西班牙的商務使用者無法看到與日本商務使用者相關的資料。

>[!TIP]
>
>您無法修改從父報表套裝繼承的值。

VRS 是附於上層報表套裝的伺服器端區段定義，因此您無法對 VRS 執行資料收集，因為 SDK 只會傳送點擊至上層報表套裝，VRS 則反過來記錄點擊。

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

在Adobe Mobile services中，您可以根據父報表套裝或虛擬報表套裝建立應用程式。 依據虛擬報表套裝建立應用程式時，我們建議您按應程式的定義來調整 VRS 區段。

>[!TIP]
>
>推播認證會附加在Mobile Services UI的應用程式層級。

若要確定您是否正確傳送推送訊息，請務必正確定義對象區段。如需詳細資訊，請參閱 [對象: 定義和設定推送訊息的對象區段](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

The time zone property on the Manage App Settings page is different from the time zone property that you use to create the VRS in Adobe Analytics. 「管理應用程式設定」頁面的時區屬性繼承自上層報表套裝，用於傳送資料到 Adobe Analytics。The property that you specify when you create the VRS in Adobe Analytics is used to display the reports in the Mobile Services UI and might be different from the parent report suite.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

若要在建立應用程式時使用 VRS，請在&#x200B;**「應用程式資訊」頁面的「報表套裝」**&#x200B;下拉式清單中選取 VRS。該清單含有上層和虛擬報表套裝。

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

下列是 VRS 的屬性:

>[!TIP]
>
>唯讀屬性繼承自父報表套裝。

| 屬性 | 繼承自上層報表套裝 | 可編輯? | 附註 |
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
| `analytics.lifecycleTimeout` | 無 | 是 | 如果使用者不希望資料不一致，則應為上層報表套裝。 |
| `analytics.privacyDefault` | 無 | 是 |  |
| `analytics.batchLimit` | 無 | 是 |  |
| `analytics.timezone` | 是 | 是，在您首次建立應用程式時。 | 此時區屬性用於傳送資料至 Adobe Analytics，而且與 VRS 建立時設定的時區屬性不同。 |
| `analytics.timezoneOffset` | 是 | 無 |  |
| `analytics.referrerTimeout` | 無 | 是 |  |
| `analytics.backdateSessionInfo` | 是 | 是 |  |

## 其他資訊 {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

以下是虛擬報表套裝的其他資訊：

* 如需 VRS 的詳細資訊，請參閱[虛擬報表套裝](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html)。
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).