# PWA(Progress Web App)

这是在使用vue-cli构建一个测试工程时在选项中有提到的PWA技术，由名字可以看出是渐进式的网络应用程序。

## 官网： https://developers.google.com/web/progressive-web-apps/    （需要翻墙）

## 特点： Reliable （ 可靠的 ）、Fast（ 快速的 ）、Engaging（ 可参与的 ） 

​		即PWA可以添加在用户的手机主屏幕上，不用从应用商店下载(Engaging),且不用考虑网络状态就能立即加载出PWA，当然没网只能从缓存中加载(Reliable),且加载速度很快(Fast)

这项技术在网络覆盖极差的印度非常流行

## 三个关键技术：

1. Service Worker(SW)(关键)

   ![](D:\markdown\notes\SW图解.jpg)

2. Manifest(应用清单)

     Web App Manifest 是一个 W3C 规范，它定义了一个基于 JSON 的 List 。Manifest 在 PWA 中的作用有：
                      
                     能够将你浏览的网页添加到你的手机屏幕上
                     在 Android 上能够全屏启动，不显示地址栏 （ 由于 Iphone 手机的浏览器是 				  Safari ，所以不支持哦）
                     控制屏幕 横屏 / 竖屏 展示
                     定义启动画面
                     可以设置你的应用启动是从主屏幕启动还是从 URL 启动
                     可以设置你添加屏幕上的应用程序图标、名字、图标大小
   ————————————————
   版权声明：本文为CSDN博主「osenki」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
   原文链接：https://blog.csdn.net/qq_19238139/article/details/77531191

3. Push Notification(消息通知)

   Push 和 Notification 是两个不同的功能，涉及到两个 API 。

                 Notification 是浏览器发出的通知消息。
               
                 Push 和 Notification 的关系，Push：服务器端将更新的信息传递给 SW ，Notification： SW 将更新的信息推送给用户。
   ————————————————
   版权声明：本文为CSDN博主「osenki」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
   原文链接：https://blog.csdn.net/qq_19238139/article/details/77531191

## 缺点

1、浏览器的支持度问题，尤其是 Safari 浏览器，这样就会导致我们在 IOS 系统手机上没办法体验 PWA 。（ 谁让 ‘ 果果 ’ 不是开源的呢 ）
  2、根据国情来看哈，目前 Native App 的使用用户都已经习惯了，虽然会下载一下，但是现在 WiFi 到处都是了，毕竟 WiFi 的普及太快了。让用户使用 PWA 来替代 Native App 短时间会不适应的。 

  3、消息推送问题，PWA的消息推送走的是 GCM（ FCM ）通道。而国内 Google 是无法访问的。（只能翻墙了，但是工信部已经禁止使用 VPN 了。） 

————————————————
版权声明：本文为CSDN博主「osenki」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_19238139/article/details/77531191