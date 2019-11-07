---
description: 您只須替換 .xml 檔案，即可在 TVML/TVJS 應用程式中充分利用 Adobe Target。實際做法是使用自訂的 ADBTarget XML 元素，便可指定您的頁面中要由 Target 內容替換的區域。
seo-description: 您只須替換 .xml 檔案，即可在 TVML/TVJS 應用程式中充分利用 Adobe Target。實際做法是使用自訂的 ADBTarget XML 元素，便可指定您的頁面中要由 Target 內容替換的區域。
seo-title: 適用於 TVML/TVJS 的 Adobe Target
title: 適用於 TVML/TVJS 的 Adobe Target
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 適用於 TVML/TVJS 的 Adobe Target{#adobe-target-for-tvml-tvjs}

您只須替換 .xml 檔案，即可在 TVML/TVJS 應用程式中充分利用 Adobe Target。實際做法是使用自訂的 ADBTarget XML 元素，便可指定您的頁面中要由 Target 內容替換的區域。

>[!IMPORTANT]
>
>您必須將 TVML/TVJS 應用程式設定為使用 tvOS SDK，才能在 TVML 頁面中使用 `ADBTarget` 元素。如需詳細資訊，請參閱[使用 tvOS 實施 Apple TV](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)。

## 入門 {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. 找出您要在其中使用 Target 位置的 `.xml` 檔案。
1. 將 `ADBTarget` 元素新增至檔案，做為 `<document>` 元素的子項。
1. 如果 Target 無法找到 mbox 的位置，或作業逾時，則會使用 `<ADBTarget>` 標籤和 `</ADBTarget>` 標籤之間的值做為預設內容。

## 在 Target 中設定您的 mbox {#section_F2DA140C34B0421D976046F825B23123}

從 Target 傳回的內容會替換 `<ADBTarget>` 和 `</ADBTarget>` 之間的所有內容 (包括這兩個 `ADBTarget` 標籤)。

>[!TIP]
>
>您對於要替換的內容應有相應的規劃。

您的使用案例可能會簡單如替換某標籤中的字串值，或複雜到替換整個頁面。

## 設定您的 ADBTarget 元素 {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

在 `ADBTarget` 元素中，您必須在 `mbox` 屬性中提供 mbox 名稱。您可以選擇將自訂屬性以 `customParameterName="customParameterValue"` 格式新增至您的要求。

* **`mbox`**

   mbox 位置的名稱.

   * 屬性類型: 字串
   * 此為必要屬性。

* **`id`**

   訂購 ID。

   * 屬性類型: 字串
   * 此屬性&#x200B;**並非**&#x200B;必要。

* **`total`**

   訂購總計。

   * 屬性類型: 字串
   * 此屬性&#x200B;**並非**&#x200B;必要。

* **`purchasedProductIds`**

   此訂購中的購買產品 ID 清單 (以逗號分隔)。

   * 以下是此屬性的範例程式碼:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * 屬性類型: 字串
   * 此屬性&#x200B;**並非**&#x200B;必要。

* **`mboxParameters`**

   `mboxParameters` 的鍵值值組清單。此字串中的每筆輸入之間以分號分隔，而索引鍵/值則是以冒號分隔。

   * 以下是此屬性的範例程式碼:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * 屬性類型: 字串
   * 此屬性&#x200B;**並非**&#x200B;必要。

* **`customParameterName`**

   此屬性的值為 `customParameterValue`。

   * 屬性類型: 字串
   * 此屬性&#x200B;**並非**&#x200B;必要。


## 範例 {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### 範例 1

下列範例是使用 `ADBTarget` 頁面中的 `LandingPage.xml.js` 元素來替換提醒內容:

#### 設定 Target

假設您有一個命名為 `landingPage` 的 mbox 位置，則選件內容的設定如下:

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### 設定 landingPage.xml.js

* 以下為 landingPage.xml.js 的設定:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* 如果向 Target 發出的要求成功，且傳回您的選件內容，則您的頁面結果如下:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* 如果無法連線至 Target 伺服器，或要求逾時，則您的頁面結果如下:

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### 範例 2

下列範例說明如何將自訂資料新增至您的 `ADBTarget` 元素。此方法可讓您為 Target 中的此 mbox 位置建立條件式體驗和選件內容。

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
