---
description: 以下為 iOS 資料庫所提供的 Audience Manager 方法清單。
seo-description: 以下為 iOS 資料庫所提供的 Audience Manager 方法清單。
seo-title: Audience Manager 方法
solution: Marketing Cloud,Analytics
title: Audience Manager 方法
topic: 開發人員和實施
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods {#audience-manager-methods}

以下為 iOS 資料庫所提供的 Audience Manager 方法清單。

SDK目前支援多種Adobe Experience cloud解決方案，包括Analytics、Target、Audience manager和Adobe Experience Platform Identity Service。 各方法會根據解決方案加上前置詞，因此 Manager 方法會加上前置詞`audience`「audience」。

如果您已在 JSON 檔案中設定 Audience Manager，則包含生命週期量度的訊號會與 `application:didFinishLaunchingWithOptions:` : 一併傳送。

* **audienceVisitorProfile**

   傳回最近取得的訪客設定檔，但若未提交任何訊號則會傳回 `null`。訪客設定檔會儲存在 `NSUserDefaults` 中，方便您在多次啟動應用程式時存取。

   * 以下是此方法的語法:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * 以下是此功能表的程式碼範例：

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   傳回目前的 DPID。

   * 以下是此方法的語法:

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   傳回目前的 DPUUID。

   * 以下是此方法的語法:

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   設定 DPID 和 DPUUID。設定時，兩者皆會附加到每個訊號。

   * **資料提供者 ID (DPID)** 是 Audience Manager 指派的資料合作夥伴 ID。
   * **資料提供者唯一使用者 ID (DPUUID)** 是使用者的資料提供者唯一 ID。

      >[!IMPORTANT]
      >
      >在4.13.x版之前，DPUUID未自動編碼。 從 4.13.x 版開始，SDK 會先解除編碼傳遞的值，然後重新編碼該值。此程序可確保 SDK 不會破壞回溯相容性。

   * 以下是此方法的語法:

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   重設 Audience Manager UUID 並清除目前的訪客設定檔。

   * 以下是此方法的語法:

      ```objective-c
      +(void) audienceReset;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   傳送具有特徵的訊號給對象管理，並取得區塊回撥中傳回的相符區段。

   * 以下是此方法的語法:

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## 範例

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
