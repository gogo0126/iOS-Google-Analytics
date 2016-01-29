## 不使用Cocoapods直接匯入Google Analytics SDK ##
參考[此網站的作法](http://www.brainyandbrawny.com/article/Google_Analytics_For_iOS_Without_Cocoapods)，用中文做筆記。

1. 首先，到[此處](https://developers.google.com/analytics/devguides/collection/ios/v3/sdk-download)所需要的SDK檔案。
2. 解壓縮之後，把`GoogleAnalytics/Library/`裡面的檔案拖曳到自己的專案裡；`libGoogleAnalyticsServices.a`這個檔案也拖曳到專案裡，都放同一個資料夾裡面比較好管理。
3. 在Bridging-Header.h檔案import底下這些header:

	```
	#import "GAI.h"
	#import "GAIDictionaryBuilder.h"
	#import "GAIFields.h"
	#import "GAILogger.h"
	```

4. 在專案設定裡面，加上底下這些link:

 * ` CoreData.framework`
 * `SystemConfiguration.framework`
 * `libz.dylib`
 * `libsqlite3.dylib`
 * `libGoogleAnalyticsServices.a`

5. 參考[Add Analytics to Your iOS App](https://developers.google.com/analytics/devguides/collection/ios/v3/?ver=swift)裡面的教學中，在AppDelegate的`didFinishLaunchingWithOptions`方法中，原本的

	```
var configureError:NSError?
GGLContext.sharedInstance().configureWithError(&configureError)
assert(configureError == nil, "Error configuring Google services: \(configureError)")
	```
要取代為
	```
GAI.sharedInstance().trackerWithTrackingId("YOUR TRACKING ID")
	```

6. 接下來就只要找個viewController，在willAppear貼上這段程式碼試試，可以run就是成功了。
	```
	var tracker = GAI.sharedInstance().defaultTracker
	tracker.set(kGAIScreenName, value: name)
	
	var builder = GAIDictionaryBuilder.createScreenView()
	tracker.send(builder.build() as [NSObject : AnyObject])
	```
