---
description: 您可在 Apple 通知內附加影像檔案。加入視覺元件可顯著增加使用者與推送通知的互動。
seo-description: 您可在 Apple 通知內附加影像檔案。加入視覺元件可顯著增加使用者與推送通知的互動。
seo-title: 接收豐富推送通知
title: 接收豐富推送通知
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

您可在 Apple 通知內附加影像檔案。加入視覺元件可顯著增加使用者與推送通知的互動。

在 iOS 應用程式中接收豐富推送通知:

1. 完成以下所述步驟，針對應用程式實施推送訊息: [推送訊息](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. 確認您可以傳送文字推送訊息至應用程式。
1. 完成以下步驟，即可新增通知服務延伸功能:

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. Select **[!UICONTROL Notification Service Extension]**.
   1. 確認 `NotificationService.m` 檔案存在。

1. 開啟 `NotificationService.m` 檔案，並確認下列委派方法存在:

   * 接收通知要求的一個方法。
   * 處理服務延伸功能到期的一個方法。

      若要接收豐富推送通知，應使用第一個方法:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      在此方法中，您可使用金鑰從 `userInfo` 中取得媒體 `attachment-url` URL。 將檔案下載到本地目錄後，請將本地路徑添加到 `bestAttemptContent.attachments`。

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


如需 iOS 豐富推送通知的詳細資訊，請參閱 [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment)。
