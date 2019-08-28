---
description: 您只須替換 .xml 檔案，即可在 TVML/TVJS 應用程式中充分利用 Adobe Target。實際做法是使用自訂的 ADBTarget XML 元素，便可指定您的頁面中要由 Target 內容替換的區域。
seo-description: 您只須替換 .xml 檔案，即可在 TVML/TVJS 應用程式中充分利用 Adobe Target。實際做法是使用自訂的 ADBTarget XML 元素，便可指定您的頁面中要由 Target 內容替換的區域。
seo-title: 適用於 TVML/TVJS 的 Adobe Target
title: 適用於 TVML/TVJS 的 Adobe Target
uuid: afd5a583-5266-43f2-8cb0-0ce89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 適用於 TVML/TVJS 的 Adobe Target{#adobe-target-for-tvml-tvjs}

您只須替換 .xml 檔案，即可在 TVML/TVJS 應用程式中充分利用 Adobe Target。實際做法是使用自訂的 ADBTarget XML 元素，便可指定您的頁面中要由 Target 內容替換的區域。

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. 如需詳細資訊，請參閱 [「使用TvOS進行Apple TV實施](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)」。

## 入門 {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>您應據此規劃要取代的項目。

您的使用案例可能會簡單如替換某標籤中的字串值，或複雜到替換整個頁面。

## 設定您的ADBTarget元素 {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

在 `ADBTarget` 元素中，您必須在 `mbox` 屬性中提供 mbox 名稱。You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   mbox 位置的名稱.

   * 屬性類型：字串
   * 需要此屬性。

* **`id`**

   訂單ID。

   * 屬性類型：字串
   * 不 **** 需要此屬性。

* **`total`**

   訂單總計。

   * 屬性類型：字串
   * 不 **** 需要此屬性。

* **`purchasedProductIds`**

   此訂購中的購買產品 ID 清單 (以逗號分隔)。

   * 以下是此屬性的程式碼範例：


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * 屬性類型：字串
   * 不 **** 需要此屬性。

* **`mboxParameters`**

   `mboxParameters` 的鍵值值組清單。此字串中的每個項目都會以分號分隔，而索引鍵值則由冒號分隔。

   * 以下是此屬性的程式碼範例：

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * 屬性類型：字串
   * 不 **** 需要此屬性。

* **`customParameterName`**

   此屬性的值 `customParameterValue`為。

   * 屬性類型：字串
   * 不 **** 需要此屬性。


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
