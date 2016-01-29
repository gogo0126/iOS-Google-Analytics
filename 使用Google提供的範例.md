##使用Google提供的範例
其實就是照著google的文件[Try Analytics for iOS](https://developers.google.com/analytics/devguides/collection/ios/v3/start?ver=swift)做，筆記一下：

1.假設已經裝CocoaPods，到命令列下指令：

`$ pod try Google`
選擇AnalyticsExample.xcodeproj，會自動下載並打開。

2.要去取得GoogleServices-Info.plist檔案，[到此連結](https://developers.google.com/mobile/add?platform=ios&cntapi=analytics&cntapp=Default%20Demo%20App&cntpkg=com.google.samples.quickstart.AnalyticsExample&cnturl=https:%2F%2Fdevelopers.google.com%2Fanalytics%2Fdevguides%2Fcollection%2Fios%2Fv3%2Fstart%3Fver%3Dswift%26configured%3Dtrue&cntlbl=Continue%20with%20Try%20Analytics)，登入gmail帳號之後，填上Bundle ID，一步一步往下產生檔案並且下載。

3.將GoogleService-Info.plist加到專案中。

4.如果是用Swift的人，請選擇AnalyticsExampleSwift目標；建置過程中有發生錯誤，可以把bitcode關掉，到設定裡面去找。
執行之後，應該可以看到5個Tab頁面，點選時，會有log出現，log會在一段時間傳送給google；可以到[Analytics ](https://www.google.com/analytics/web/)，點開即時報告，應該可以看到有變化。
