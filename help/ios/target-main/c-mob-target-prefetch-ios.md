---
description: Adobe Target 預先擷取功能使用 iOS Mobile SDK，透過快取伺服器回應，盡量以最少次數擷取提供項目內容。
seo-description: Adobe Target 預先擷取功能使用 iOS Mobile SDK，透過快取伺服器回應，盡量以最少次數擷取提供項目內容。
seo-title: iOS 中的預先擷取選件內容
title: iOS 中的預先擷取選件內容
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
translation-type: ht
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# iOS 中的預先擷取選件內容 {#prefetch-offer-content-in-ios}

Adobe Target 預先擷取功能使用 iOS Mobile SDK，透過快取伺服器回應，盡量以最少次數擷取提供項目內容。

>[!IMPORTANT]
>
>iOS 版 Mobile SDK 中的預先擷取功能不支援 Adobe Target 中的自動指定目標、自動分配以及自動個人化活動類型。

此程序會減少載入時間，避免多個網路呼叫，並允許通知 Adobe Target 行動應用程式使用者造訪哪一個 mbox。預先擷取呼叫期間，會擷取並快取所有內容，而且將從快取中擷取此內容，以供包含指定 mbox 名稱之快取內容的所有未來呼叫使用。

預先擷取內容不會在跨啟動之間持續有效。只要應用程式仍然存在，或直到呼叫 `clearPrefetchCache()` 方法為止，則會快取預先擷取內容。

>[!IMPORTANT]
>
>自 SDK 4.14.0 版開始，即可使用 Target 預先擷取 API。如需有關參數限制的詳細資訊，請參閱[批次輸入參數](https://developers.adobetarget.com/api/#batch-input-parameters)。

在 SDK 4.14 或更新版本中，若要指定 ，啟動 v2 批次 mbox TnT 呼叫時，系統會從 檔案中挑選 `environmentId``ADBMobileConfig.json`environmentId。若未指定此檔案中的 `environmentId`，系統就不會以 TNT 批次 mbox 呼叫傳送任何環境參數，而是為預設環境傳送選件。

例如:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## 預先擷取方法 {#section_05967F1F3A554B0FBC2C08A954554BDE}

以下是您可以在 iOS 中用於預先擷取的方法:

* **targetPrefetchContent**

   將含有一連串位置的預先擷取要求傳送至設定的 Target 伺服器，並在提供的回撥中傳回要求狀態。

   * 以下是此方法的語法:

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * 以下是此方法的參數:

      * **`targetPrefetchArray`**

         `TargetPrefetchObjects` 陣列，包含每個要預先擷取之 Target 位置的名稱與 mboxParameters。

      * **`profileParameters`**

         包含要與此要求中每個位置預先擷取搭配使用之設定檔參數的鍵值和值。

      * **`callback`**

         完成預先擷取時叫用。如果預先擷取成功，會傳回 `true`，如果預先擷取失敗，則傳回 `false`。

* **targetLoadRequests**

   針對在要求陣列中指定的多個 mbox 位置執行批次要求。陣列中的每個物件包含回撥函式，當內容可用於其指定的 mbox 位置時，將會叫用該函式。

   >[!IMPORTANT]
   >
   >如果已快取要求位置的內容，則會在提供的回撥中立即傳回內容。否則，SDK 將會傳送網路要求給 Target 伺服器以擷取內容。

   * 以下是此方法的語法:

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * 以下是此方法的參數:

      * **`requests`**

         `TargetRequestObjects` 陣列，包含要擷取之每個位置的名稱、預設內容、參數，以及回撥函式。

      * **`profileParameters`**

         包含要與此要求中每個位置預先擷取搭配使用之設定檔參數的鍵值和值。

* **targetPrefetchClearCache**

   清除 Target 預先擷取快取的資料。

   * 以下是此方法的語法:

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * 沒有適用於此方法的參數。

* **targetRequestObjectWithName**

   使用提供的資料建立並傳回 `TargetRequestObject` 例項。

   * 以下是此方法的語法:

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * 沒有適用於此方法的參數。

* **createTargetPrefetchObject**

   使用提供的資料建立並傳回 `TargetPrefetchObject` 例項。

   * 以下是此方法的語法:

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## 公用類別 {#section_A273E53F069E4327BBC8CE4910B37888}

以下是 iOS 中支援預先擷取的公用類別:

### 類別參考: TargetPreFetchObject

封裝用於 mbox 預先擷取的 mbox 名稱和參數。

* **`name`**

   您要擷取的位置/mbox 名稱。

   * **類型**: NSString*

* **`mboxParameters`**

   選擇性字典包含 mbox 參數的鍵值值組。

   * **類型**: NSDictionary*

* **`orderParameters`**

   字典包含 order 參數的鍵值值組。

   * **類型**: NSDictionary*

* **`productParameters`**

   字典包含 product 參數的鍵值值組。

   * **類型**: NSDictionary*

### 類別參考: TargetRequestObject

此類別封裝 mbox 名稱、預設內容、mbox 參數，以及用於 Target 位置要求的傳回回撥。

* **`name`**

   要求位置的名稱。

   * **類型**: NSString*

* **`mboxParameters`**

   NSString 值代表您要擷取之位置/mbox 的名稱。

   * **類型**: NSString*

* **`defaultContent`**

   如果 Target 伺服器無法連線，將傳回的預設內容。

   * **類型**: NSString*

* **`callback`**

   當批次請求 Target 位置時，將在內容可用於該位置時叫用回撥。

   * **類型**: 函式

## 程式碼範例 {#section_BF7F49763D254371B4656E17953D520C}

以下是如何藉由使用 iOS SDK 預先擷取內容的範例:

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

以下是藉由使用 iOS SDK 批次處理 `loadRequest` 的範例:

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## 其他資訊 {#section_A454BAD1CD49423E86C71BAEE06125FD}

以下是關於這些範例的部分其他資訊:

* `ProductParameters` 僅允許下列鍵值:

   * `id`
   * `categoryId`

* `OrderParameters` 僅允許下列鍵值:

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` 接受字串的陣列。