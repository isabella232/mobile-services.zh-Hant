---
description: 以下為 iOS 資料庫所提供的 Audience Manager 方法清單。
seo-description: 以下為 iOS 資料庫所提供的 Audience Manager 方法清單。
seo-title: Audience Manager 方法
solution: Experience Cloud,Analytics
title: Audience Manager 方法
topic: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 80%

---


# Audience Manager 方法 {#audience-manager-methods}

以下為 iOS 資料庫所提供的 Audience Manager 方法清單。

SDK 目前可支援多個 Adobe Experience Cloud 解決方案，包括 Analytics、Target、Audience Manager 以及 Adobe Experience Platform Identity Service。各方法會根據解決方案加上前置詞，因此 Manager 方法會加上前置詞`audience`「audience」。

如果您已在 JSON 檔案中設定 Audience Manager，則包含生命週期量度的訊號會與 `application:didFinishLaunchingWithOptions:` : 一併傳送。

* **audienceVisitorProfile**

   傳回最近取得的訪客設定檔，但若未提交任何訊號則會傳回 `null`。訪客設定檔會儲存在 `NSUserDefaults` 中，方便您在多次啟動應用程式時存取。

   * 以下是此方法的語法:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * 以下是此功能表的範例程式碼:

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   傳回目前的 DPID。

   * 此方法的語法如下：

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * 此方法的程式碼範例如下：

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   傳回目前的 DPUUID。

   * 此方法的語法如下：

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * 以下是此方法的範例程式碼:

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   設定 DPID 和 DPUUID。設定後，兩者都會附加至每個訊號。

   * 資 **料提供者ID(DPID)** ，是Audience Manager指派的資料合作夥伴ID。
   * 資 **料提供者唯一使用者ID(DPUUID)** ，是該使用者的資料提供者唯一ID。

      >[!IMPORTANT]
      >
      >在 4.13.x 版之前，DPUUID 不會自動編碼。從4.13.x版開始，SDK會先解除編碼傳入的值，然後重新編碼此值。 此程式可確保SDK不會中斷回溯相容性。

   * 以下是此方法的語法:

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * 此方法的程式碼範例如下：

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

   * 此方法的範例程式碼如下：

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
