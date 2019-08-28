---
description: 依使用者是否已安裝應用程式 (應用程式深層連結) 或未安裝 (前往網站或應用程式商店) 將使用者路由至目的地。
keywords: 行動
seo-description: 依使用者是否已安裝應用程式 (應用程式深層連結) 或未安裝 (前往網站或應用程式商店) 將使用者路由至目的地。
seo-title: 插頁廣告
solution: Marketing Cloud、Analytics
title: 插頁廣告
topic: 量度
uuid: 7dce8ab2-2a5d-4384-ac1 e-e31 dfaa33654
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 插頁廣告{#interstitials}

依使用者是否已安裝應用程式 (應用程式深層連結) 或未安裝 (前往網站或應用程式商店) 將使用者路由至目的地。建議可以提供路由選項讓使用者選擇，行銷人員可設定能顯示可用登陸目的地的插入式頁面，讓使用者自行選擇。

若要設定插入式連結，同時建立行銷連結：

1. Click **[!UICONTROL Edit Deep Link Interstitial]**.

   ![深層連結插播](assets/interstitial2.png)

1. 在下列欄位輸入資訊:

   * **[!UICONTROL 自訂 HTML]**

      選取自訂的插入式 HTML 頁面。

      行銷人員可使用自訂插播式廣告，使用自訂HTML/CSS/JS自訂插入式登陸頁面，讓您品牌化頁面。

      HTML 頁面的要求如下:

      * 必須是 HTML 檔案。
      * Must contain the `%%DEST%%` and `%%FALLBACK%%` placeholders.
      * The uploaded HTML will be served in an `<iframe>`.

         您必須確保連結目標會指向父視窗。You can include `<base target="_parent" />` in `<head>` or specify a target property for each `<a/>` individually.

         >[!TIP]
         >
         >如果上傳自訂HTML，除非您移除上傳的檔案，否則不會使用此表格中的其他四個選項。
   * **[!UICONTROL 影像 URL]**

      指定 URL 為影像資產。

   * **[!UICONTROL 內文]**

      指定插入式連結的內文。

   * **[!UICONTROL 確認文字]**

      指定文字按鈕的文字。

   * **[!UICONTROL 後援文字]**

      指定要顯示的後援文字。

      如果深層連結失敗，此欄位會更新文字按鈕。在允許使用者後援至其他選項之前，會將使用者導向至嘗試深層連結。例如，可後援至應用程式商店以下載及安裝應用程式，或帶領使用者前往公司的網站。後援文字可讓使用者得知在深層連結失敗時有其他選項可供使用。


1. (**Optional**) Click the icons above the image to see how the interstitial looks rotated and on different devices.

   您可以在 Mobile Services 外部變更或編輯影像，確保影像在不同的狀況中可正確顯示。
1. 按一下&#x200B;**[!UICONTROL 儲存]**。
