---
description: 您可以將影像檔案附加至Apple通知。 新增視覺元件可大幅提升使用者與推播通知的互動。
title: 接收豐富推送通知
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
exl-id: 1167ae4b-04ad-4c0d-a9db-67d30693f697
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 39%

---

# 接收豐富推送通知 {#receive-rich-push-notifications}

您可以將影像檔案附加至Apple通知。 新增視覺元件可大幅提升使用者與推播通知的互動。

若要在iOS應用程式中接收豐富推送通知：

1. 完成以下所述步驟，針對應用程式實施推送訊息:  [推送訊息](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. 確認您可以傳送文字推送訊息至您的應用程式。
1. 完成下列步驟，新增通知服務擴充功能：

   1. 在Xcode專案中，選取&#x200B;**[!UICONTROL 檔案]** > **[!UICONTROL 新增]** > **[!UICONTROL 目標]**。
   1. 選取&#x200B;**[!UICONTROL 通知服務擴充功能]**。
   1. 確認 `NotificationService.m` 檔案存在。

1. 開啟 `NotificationService.m` 檔案，並確認下列委派方法存在:

   * 接收通知請求的一種方法。
   * 一種處理服務擴充功能到期的方法。

      若要接收豐富推送通知，請使用第一種方法：

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      在此方法中，您可以使用 `attachment-url` 索引鍵從 `userInfo` 取得媒體 URL。將檔案下載至本機目錄後，請將本機路徑新增至 `bestAttemptContent.attachments`。

      以下是此方法中的程式碼範例:

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


如需iOS豐富推送通知的詳細資訊，請參閱[UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment)。
