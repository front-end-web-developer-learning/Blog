# PWA

## 什么是PWA？

Progressive Web App，简称PWA，直译是渐进式WEB应用，是Google在2015年提出，2016年6月才推广的项目。是提升App体验的一种新方法，能给用户原生应用的体验。PWA能做到原生应用的体验不是靠特指某一项技术，而是经过应用一些新技术进行改进，在安全，性能和体验三个方面都有很大提升，PWA本质上是Web App，借助一些新技术也具备了Native App的一些特性，兼具Web App和Native App的优点。PWA的主要特点包括下面三点：

- 可靠--即使在不稳定的网络环境下，也能瞬间加载并展现
- 体验--快速响应，并且有平滑的动画响应用户的操作
- 粘性--像设备上的原生应用，具有沉浸式的用户体验，用户可以添加到桌面

## PWA特性

- 可靠性

  当用户从主屏幕启动时，service work可以立即加载渐进式Web应用程序，完全不受网络环境的影响。service work就像一个客户端代理，它控制缓存以及如何响应资源请求逻辑，通过预缓存关键资源，可以消除对网络的依赖，确保为用户提供即时可靠的体验。

- 快速

  据统计，如果站点加载时间超过 3s，53% 的用户会放弃等待。页面展现之后，用户期望有平滑的体验，过渡动画和快速响应。

- 沉浸式体验

  渐进式Web应用程序可以安装并在用户的主屏幕上，无需从应用程序商店下载安装。他们提供了一个沉浸式的全屏幕体验，甚至可以重新与用户接触的Web推送通知。

Web应用程序中，可以通过manifest.json控制应用程序的显示方式和启动方式，指定主屏幕图标、启动应用程序时要加载的页面、屏幕方向，甚至可以指定是否显示浏览器Chrome。

- 渐进增强 - 能够让每一位用户使用，无论用户使用什么浏览器，因为它是始终以渐进增强为原则。
- 响应式用户界面 - 适应任何环境：桌面电脑，智能手机，笔记本电脑，或者其他设备。
- 不依赖网络连接 - 通过 service workers 可以在离线或者网速极差的环境下工作。
- 类原生应用 - 有像原生应用般的交互和导航给用户原生应用般的体验，因为它是建立在 app shell model 上的。
- 持续更新 - 受益于 service worker 的更新进程，应用能够始终保持更新。
- 安全 - 通过 HTTPS 来提供服务来防止网络窥探，保证内容不被篡改。
- 可发现 - 得益于 W3C manifests 元数据和 service worker 的登记，让搜索引擎能够找到 web 应用。
- 再次访问 - 通过消息推送等特性让用户再次访问变得容易。
- 可安装 - 允许用户保留对他们有用的应用在主屏幕上，不需要通过应用商店
- 可连接性 - 通过 URL 可以轻松分享应用，不用复杂的安装即可运行。

## 使用哪些技术做到PWA？

- 可靠-当用户打开我们的站点时（从桌面icon或者从浏览器），通过Service Worker能够让用户在网络条件很差的情况下也能瞬间加载并且展现。

  Service Worker是用JavaScript编写的JS文件，能够代理请求，并且能够操作浏览器缓存，通过将缓存的内容直接返回，让请求能够瞬间完成。开发者可以预存储关键文件，可以淘汰过期的文件等等，给用户提供可靠的体验。具体用法：[Service Worker 应用详解](http://lzw.me/a/pwa-service-worker.html)

- 体验-为了保证首屏的加载，我们需要从设计上考虑，在内容请求完成之前，可以优先保证App Shell的渲染，做到和Native App一样的体验，App Shell--是PWA界面展现所需要的最小资源。

  App shell架构是构建Progressive Web App的一种方式，这种应用能可靠且即时地加载到您的用户屏幕上，与本机应用相似。App“shell”是支持用户界面所需的最小的HTML，CSS和JavaScript，如果离线缓存，可确保在用户重复访问时提供即时，可靠的良好性能。这意味着并不是每次用户访问时都要从网络加载App Shell。只需要从网络中加载必要的内容。具体用法：[App Shell 模型](https://developers.google.cn/web/fundamentals/architecture/app-shell)

- 粘性-Web App Manifest 允许开发者控制PWA添加到桌面，允许定制桌面图标，URL等等；PWA可以通过给用户发送离线通知，让用户回流。

  [PWA：添加应用至桌面分享](https://segmentfault.com/a/1190000008929656)

## PWA核心功能

PWA并不是单指某一项技术，可以理解为一种思想和概念，目的就是对比原生app，将web网站通过一系列的web技术去优化它，提升其安全性，性能，流畅性，用户体验等各方面指标，最后达到用户就像在用app一样的感觉。

- Web App Manifest
- Service Worker：用户离线时，可以从缓存中启动web应用
- Cache API缓存
- Push&Notification推送与通知

## PWA关键技术

### Manifest（应用清单）

Web App Manifest是一个W3C规范，定义了一个基于JSON的清单，为开发人员提供一个放置与Web应用程序关联的元数据的集中地点。manifest 就是 PWA 概念的一环，它给你了控制你的应用如何出现在用户期待出现的地方（比如用户手机主屏幕），这直接影响到用户能启动什么，以及更重要的，用户如何启动它。

使用 web 应用程序清单，你的应用可以：

- 能够真实存在于用户主屏幕上
- 在 Android 上能够全屏启动，不显示地址栏
- 控制屏幕方向已获得最佳效果
- 定义启动画面，为你的站点定义主题
- 追踪你的应用是从主屏幕还是 URL 启动的

### Service Workers

Service Worker是浏览器在后台独立于网页运行的脚本，它打开了通向不需要网页或用户交互的功能的大门。这个 API 之所以令人兴奋，是因为它可以支持离线体验，让开发者能够全面控制这一体验。

Service Worker是由两部分构成，一部分是 cache，还有一部分则是 Worker。

它被设计为一个相对底层、高度可编程、子概念众多，也因此异常灵活且强大的 API，它就像一个位于客户端和网络之间的代理，可以拦截、处理、响应流经的网络请求，配合Cache API，你可以自由管理网络请求文件的缓存，这使得 Service Worker 可以从缓存中向 web 应用提供资源，即使是在离线的环境下。这样，在离线和网速低的情况下也能秒开，说白了，之前的Hybrid架构的出现不就是为了这个功能么。之前虽然有AppCache，但它具有相当多的缺陷。

### Push Notification（推送通知）

Push 和 Notification是两个不同的功能，涉及到两个API，但是它们之前有依赖关系。

Notification，属于浏览器发出的通知消息，之前需要浏览器一直开着才能实现这种通知，但是现在有了上面提到的Service Worker，就可以驻留在进程里面操作了。

Push & Notification关系：

- Push : 服务器端将更新的信息传递给 Service Worker
- Notification: Service Worker 将更新的信息推送给用户

## PWA优势

PWA对于开发者和用户有以下优点：

- 你只需要基于开放的 W3C 标准的 web 开发技术来开发一个app。不需要多客户端开发。不需要开发Android和IOS两套不同的版本。
- 用户可以在安装前就体验你的 app。
- 无需安装、不需要通过 AppStore 下载 app，只要你输入网址访问一次，然后将其添加到设备桌面就可以继续使用了。app 会自动升级不需要用户升级。
- 发布不需要提交到app商店审核。
- 更新迭代版本不需要审核，不需要重新发布审核。
- 现有的web网页都能够通过改进成为PWA，能很快转型，上线，实现业务，获取流量。
- 用户会受到‘安装’的提示，点击安装会增加一个图标到用户首屏。
- 被打开时，PWA 会展示一个有吸引力的闪屏。
- chrome 提供了可选选项，可以使 PWA 得到全屏体验。
- 必要的文件会被本地缓存，因此会比标准的web app 响应更快（也许也会比native app响应快）。
- 安装及其轻量 -- 或许会有几百 kb 的缓存数据。
- 网站的数据传输必须是 https 连接。
- 可以离线工作，并且在网络恢复时可以同步最新数据。
- Web最重要的意义在于开放和去中心化，这才是万维网的初衷。

## PWA劣势

- 门槛不低。部署的服务器要求HTTPS，ServiceWorker涉及API众多，需要单独学习。
- 浏览器支持不够全面。苹果Safari 短时间内不会支持（最新版本待验证）。
- 用户体验习惯。网页应用替代原生应用的方式，用户短时间内不适应。
- 浏览器对技术的支持还不够全面，不是每款浏览器都能100%的支持所有PWA。
- PWA现在还没有那么火。
- PWA对于开发者来说，最重要的意义就在于绕过APP商店的审核直接推给用户。如果普及，这将威胁到平台权威，APP商店肯定不干。

## PWA与其它App的对比

### 目前的移动端APP：

- Native APP
- Web App
- Hybrid App

### Native APP

Native APP，指原生App，是一个完整的App，可拓展性强，需要用户下载安装使用。

优点：

- 可使用移动设备所有功能
- 速度快、性能高、用户体验好
- 离线使用

缺点：

- 开发成本高、维护成本高
- 每个不通的平台都要重新开发
- 应用商店审核复杂，效率低

### Web APP

Web App 指采用Html5语言写出的App，生活在浏览器里的应用，不需要下载安装。

优点：

- 跨平台开发、无需下载、无需安装、开发速度快
- 发布灵活，因为根本不需要应用商店的审核
- 较低的开发成本
- 可即时上线
- 用户可以直接使用最新版本
- 支持设备广泛

缺点：

- 只能使用有限的移动设备API
- 浏览器兼容问题
- 无法上传到应用商店
- 用户暂时不适用

### Hybrid App

Hybrid APP指的是半原生半Web的混合类App，需要下载安装。

优点：

- 兼容多平台
- Web前端工作人员就可快速构建
- 可以上传到应用商店
- 可以基于浏览器的方式进行页面调试
- 可使用的移动设备的API多

缺点：

- 用户体验不如原生应用
- 为模拟原生样式，需要大量的html和css
- 性能稍慢
- 技术不是很成熟

## PWA兼容　

- 由于pwa是谷歌的“亲儿子”，所以它在新版本安卓的各大浏览器都有非常好的支持。
- 微信浏览器对pwa的支持情况，除了推送信息和支付接口之外基本已经实现支持。（支付接口的支持应该是出于安全的考虑，以及和weixin-js-sdk重叠的原因，X5浏览器支持它只是时间的问题）。如今我们更关心的是关于SW-cache这一部分，换句话说，我们可以放心在安卓微信上使用SW-cache的技术。
- service worker在IOS12得到了支持，这也就意味着pwa的时代很快就会到来。

## PWA在中国

国内IPhone不在少数，而IOS目前是不完全支持PWA的。
国内Android系统，大部分早已把Google框架移除了，所以兼容性会出问题。
推送依赖于GCM，而国内Google是无法访问的。

Google的技术在国内推进是很痛苦的，Android虽然近年来在国内不错，但PWA在国内的发展有很多困难。

## 缓存机制

[Service Worker](https://link.jianshu.com/?t=https%3A%2F%2Fw3c.github.io%2FServiceWorker%2F)的出现很大程度，改变了web app的格局，HTTP cache和SW cache有着天壤之别。这样的HTTP缓存机制没法弥补网页跳转带来的白屏间隙，SW cache由于优先缓存静态资源以及接口的机制，大大减少了网络状况差（甚至断网）带来的白屏现象。优先更新本地的同时，service worker会和后端进行一次通信，这次通信会告知静态资源是否被更改，在下次刷新的时候更改内容。

动态接口方面则会采用 [runtimeCaching](https://link.jianshu.com/?t=https%3A%2F%2Fgithub.com%2FGoogleChromeLabs%2Fsw-precache%23runtimecaching-arrayobject)进行交互，这部分也会进行动态内容的缓存，[sw-toolbox](https://link.jianshu.com/?t=https%3A%2F%2Fgithub.com%2FGoogleChromeLabs%2Fsw-toolbox)的代码将会被引入你的sw.js中，它会利用正则表达式匹配到你请求的接口，进行接口缓存，当该接口出现内容变化时，SW会和后端进行一次通讯保证下一次加载的数据是最新数据，这样的更新机制分为5个类型。

- networkFirst
- cacheFirst
- fastest
- cacheOnly
- networkOnly

networkFirst是显示完成后，SW优先和后端通讯，看接口是否更新，下一次刷新则是采用最新数据内容。cacheFirst则是优先考虑缓存，如果缓存没有命中，才会去请求接口拿新数据，这个选型适合那种不经常更改的内容或者有别的更新机制。fastest则是两个同时进行，哪个快执行哪个。cacheOnly和networkOnly比较不常用。

## 安全性

- [如何利用/防御 Service Worker](https://link.jianshu.com/?t=http%3A%2F%2Fmp.weixin.qq.com%2Fs%2F_izQ1OeDONI8D4LPiPpVOQ)

## 解决方案推荐

#### LAVAS:基于Vue.js的PWA解决方案

地址：[lavas](https://lavas.baidu.com/)

#### 饿了么的PWA升级实践（结合Vue.js）

地址：[饿了么](https://www.cnblogs.com/lhb25/p/upgrading-eleme-to-pwa.html)

#### 将已有的vue项目改造成PWA

地址：[改造vue项目](https://blog.csdn.net/ns2250225/article/details/79353946)

#### 改造你的项目

地址：[改造](https://www.jianshu.com/p/7546527a786d)

#### 基于 React 的 PWA 应用开发框架

地址：[react-pwa](https://www.awesomes.cn/repo/Atyantik/react-pwa)

