---
description: Adobe SDK 可運用 Apple 的 Search Ads 應用程式屬性 API，讓開發人員和行銷人員追蹤和了解應用程式下載次數，而這些下載次數源自於 Apple App Store 中的 Search Ads 促銷活動。
seo-description: Adobe SDK 可運用 Apple 的 Search Ads 應用程式屬性 API，讓開發人員和行銷人員追蹤和了解應用程式下載次數，而這些下載次數源自於 Apple App Store 中的 Search Ads 促銷活動。
seo-title: Apple Search Ads
solution: Marketing Cloud,Analytics
title: Apple Search Ads
topic: 開發人員和實施
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: ht
source-git-commit: ebcc04ab3e80aafb9d9ec2e1fbc809c743554cb7

---


# Apple Search Ads {#apple-search-ads}

Adobe SDK 可運用 Apple 的 Search Ads 應用程式屬性 API，讓開發人員和行銷人員追蹤和了解應用程式下載次數，而這些下載次數源自於 Apple App Store 中的 Search Ads 促銷活動。如需 Search Ads 促銷活動的詳細資訊，請參閱 [Apple Search Ads](https://searchads.apple.com)。

## 福利 {#section_CEA30C652AC8470784B8054E299B80FA}

以下為使用 Apple 廣告的優點:

* 新增數行程式碼至應用程式中，即可輕鬆測量 Search Ads 應用程式下載促銷活動的效益。
* 開發人員可存取下載日期/時間和帶動轉換的標得關鍵字。

## 實施 Apple Ad {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>若要實施 Apple Ad，您必須擁有 iOS SDK 4.13.2 版或更新版本。

啟用應用程式以存取 Search Ads 屬性:

1. 實施 Adobe SDK 4.13.2 版或更高版本。

   如需詳細資訊，請參閱[核心實施與生命週期](/help/ios/getting-started/dev-qs.md)。

1. 將 iAd 架構新增至應用程式的 Xcode 專案檔中。

## Search Ads 屬性報告 {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Apple Search Ads 屬性資料會顯示在贏取名稱、來源及詞語值中。

   如果 attribution = `true`，則所有 `iad-*` 欄位將會包含在生命週期點擊中。

   此外，下列值將會從 `"iad"`字典對應至一般贏取內容資料欄位:

   * `"iad-campaign-id"` --&gt; `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --&gt; `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --&gt; `"a.referrer.campaign.content"`
   * `"iad-keyword"` --&gt; `"a.referrer.campaign.term"`
   此對應程序能確保可讓這些值用於標準報表中。
