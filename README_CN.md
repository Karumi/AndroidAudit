**Your Android app as a crime scene! 假设你的Android app是一个犯罪现场！**

Technical audits of iOS and Android applications have become an integral part of our daily job here at Karumi. Even though it can look easy, there are quite a few implementation details to review when performing such audit. In this document we are going to review what we believe are the most important things to check, separated by technical area. 

在Karumi，iOS和Android应用的技术审核已经成为日常工作必不可少的一部分。这项工作看起来容易，然而在实际进行审核的时候，我们会发现有不少实现细节要注意。我们来回顾一下这个文档里面我们认为最重要的审核条目。这些审核条目按照技术方向被分成几种不同类别。

**Version Control System: 版本控制系统：**

[术语参考](https://github.com/progit/progit2-zh/blob/master/TRANSLATION_NOTES.asc)

Whether the engineers are using version control, which system and using what process tells us a lot of things about the software development process. 

工程师是否使用版本控制，使用哪种系统，通过哪种过程来向我们呈现软件开发过程。


* Do you have a properly configured *ignore file so IDE metadata files and other extraneous elements are not under version control?

* 你有没有一个正确设置的*ignore忽略文件，使得IDE的元文件和多余的东西不出现在版本控制系统中？

* Are third party libraries versioned in the repository rather than configured as an external dependency?

* 第三方库文件是不是通过版本控制系统放到同一个仓库中，而不是被设置成一个外部依赖？

* Do you use sufficiently concise and descriptive commit messages?

* 你有没有撰写足够准确而且描述清晰的提交信息？

* Is the size of the commits reasonable?

* 提交的大小是否合理？

* Are all the files in a commit related to the same issue or feature?

* 同一个提交的所有文件是否都是和同一个问题或者特性相关连？

* Are you using branches following any branching scheme like "feature branch" or “git-flow”? 

* 你在使用分支时有没有使用”特性分支“或者”git-flow”这样的分支策略？

* Are these branch names descriptive enough?

* 分支命名是否足够描述清晰？

* Are you using the pull request/code review system before merging the code into master?

* 是否在合并到主分支之前使用拉取请求(pull request)或者代码审核(code review)系统？

    * Do you have any guidelines regarding what to look for when reviewing a PR?
    
    * 审核拉取请求(pull request)的时候，有没有相关可以参考的参考规则？

    * How many comments on average for every PR?
    
    * 每个PR平均有多少评论？

    * How many people review each PR?
    
    * 每个PR有多少人审核？

    * How many +1 do you need before merging?
    
    * 合并PR需要达到多少个同意？

    * Who is responsible for closing the branch?
    
    * 谁来负责关闭被合并的分支？

* Are you using release branches to prepare every release?

* 有没有用发布分支(release branch)来准备每次版本发布？

* How long are your staging process open?

* 测试过程持续多久？

* How many fixes do you introduce into your release candidate before to release it?

* 正式发布之前需要引进多少个问题修复到发布候选版本中？

* Are you able to checkout the exact code used to build any of the published versions of your app?

* 能否签出和用于构建线上应用的完全一样的代码？

* How many hotfixes have you released in the past year?

* 去年你一共发布了多少个紧急修复(hotfixes)？

* Are you squashing the commits in a branch before merging it into the master/develop/ branch?

* 合并分支到主分支或者开发分支之前你是否会压缩提交？

* Is the master/develop branch ready to be released at any time?

* 主分支或者开发分支是否随时可以发布？

**Build Tools:构建工具：** 

Being able to reproduce the build process on every developer machine and any other external system as continuous integration is key.

能够在任何开发者机器，任何像持续集成系统这样的外部系统上复制构建过程非常重要。

* How many libraries are being used in the project?

* 项目使用了多少库？

* Is the project split into different modules?

* 项目是否被分成了多个模块？

* Do they consume their dependencies from Maven or Gradle or are they using local jars?

* 项目模块是否通过Maven或者Gradle来提供依赖还是使用本地Jar文件？

* Is the project dangerously approaching to the dex method count limit? Is it already beyond that point?

* 项目是否接近了dex方法数量的红线？还是已经超过了红线？

* Are you using libraries you project does not need?

* 有没有使用不需要的库？

* Is the project using multidex?

* 有没有使用multidex？

* Are the external dependencies up to date?

* 外部依赖是否保持了最新状态？

* Are you respecting every third party library license?

* 你是否遵守了每个第三方库的授权证明？

* Is the project using any deprecated or abandoned/unmaintained third party library?

* 项目是否使用了任何过时或者被遗弃/停止维护的第三方库？

* Is the minimum SDK the one required by the product description?

* 最低SDK是否是项目描述中所要求的？

* Is the target SDK up to date?

* 目标SDK是否是当前最新？

* Is proguard, or any other obfuscation tool, enabled and properly configured?

* 是否启用并且正确配置了proguard或者任何其他混淆工具？

* Are the keystore credentials and Google Play Store credentials stored in a secure place?

* keystore证书和Google Play Store证书是否被存放在安全的地方？

* Is the application keystore and the credential stored in a secure place?

* 应用证书和签名是否被存放在安全的地方？

* Does the application use build types properly?

* 应用有没有正确使用构建类型？

* Does the application use flavors properly?

* 应用是否正确使用特色类型？

* Is the release build type properly configured?

* 发布构建类型是否正确配置？

* Is the backup option enabled?

* 是否开启了备份选项？

* Is lint enabled and successfully passing?

* lint是否启用而且成功通过？

* Is there any static analysis tool configured and passing?

* 是否配置了静态分析工具而且成功通过？

* Is there any checkstyle configured and passing?

* 是否配置了风格检查而且成功通过

* Is the application id and version name/code configured properly?

* 是否正确配置应用id和版本号，版本编码？

* Are you using any structure or strategy for versioning the id?

* 对于id，你是否使用某种版本结构或者策略？

* Is there any continous integration tool configured?

* 有没有配置持续集成工具？

* Is the release process automated?

* 发布过程是否自动化？

**Android Resources Usage:Android资源使用：**

There is a wide range of devices in the Android world, each one with their own screen size, capabilities, etc. You need to be extra careful and leverage some of the Android tools to provide the best possible experience to your user regardless of their device.

在Android世界中有很多不同的设备，每种都有不同的屏幕大小，功能等等特征。你需要额外小心还要使用Android工具来根据用户的设备给他们提供最佳的体验。

* Are there any missing resources for densities, flavors or build types?

* 对于各种屏幕密度，特色或者构建类别是否有缺失的资源？

* Does the application support all the densities required by the product description?

* 应用是否支持产品描述要求的所有屏幕密度？

* Does the application use drawable/mipmap, fonts or vectorial resources?

* 应用是否使用位图，字体或者矢量资源？

* Are there any missing translations?

* 是否有缺失的翻译？

* Is the translation process automated?

* 翻译过程是否自动化？

* What is the default language for translations?

* 默认的翻译是什么语言？

* Does the application use custom fonts?

* 应用是否使用自定义字体？

* Does the application use configuration values inside the String resources file?

应用是否使用存放在String资源文件中的配置变量？

* Is the naming convention used to assign names to the resources homogeneous?

变量命名的规则和资源命名的规则是否一致？

* Are configuration parameters related to the device hardware configured properly?

硬件相关的配置参数是否正确设置？

* Are you supporting tablets?

是否支持平板设备？

**Android Layout Usage: Android布局用法：**

As we have said before, there is a wide range of Android devices in the world, each one with it own screen size and density. Using Android Layouts correctly is key

就像我们之前说到的，市面上有很多不同屏幕，不同像素密度的各种Android设备。正确使用Android布局非常重要。

* Does the number of layers in the application layouts produce performance issues?

* 应用布局的层数是否造成了性能问题？

* Do you use themes and styles?

* 是否使用了主题和风格？

* Do your reuse layouts using the "include" tag?

* 是否通过使用“include”标签来复用布局？

* Do you use the correct view group type in the layouts implementation?

* 在布局实现中有没有使用正确的视图组（view group）?

* Are the layouts configured for different screen sizes?

* 布局有没有为不同屏幕大小适配？

* Is the naming convention used to assign names to the layouts and widgets homogeneous?

* 布局和控件命名规则是否一致？

* Are the lists implemented using ListView or RecyclerView widgets?

* 实现列表的时候使用的是ListView还是RecyclerView控件？

* Is the Android Support Library properly used?

* 是否正确使用了Android Support库？

**Permissions Usage:权限用法：**

Asking for the right permissions builds trust among your users and can help your app to walk the extra mile and seamlessly integrate with other services to deliver a delightful; experience to your users.

请求正确的权限可以帮助你在用户中建立起信任，也可以让你的应用走的更远，同时可以无缝的和其他服务集成给你的用户带来良好的体验。

* Are all the requested permissions really needed?

* 所有请求的权限是否真的有必要？

* Is there any permission used maliciously?

* 有没有滥用任何权限？

* Is there any permission missing?

* 有没有缺失必要的权限？

* Is the target SDK used greater than 23 and the "dangerous permissions" requested using the compatibility permissions system?

* 目标SDK版本是否高于23？危险权限是否通过兼容权限系统（compatibility permissions system）请求？

* Are the permission requested when they are going to be used?

* 权限被使用时有没有发出请求？

* Is there any feedback shown to the user explaining why the permission is needed?

* 有没有通过反馈说明需要请求的权限？

**Security Issues:安全问题？**

As developers we need to be conscious about our app security, we don’t want our user’s data to be leaked or their sessions stolen

作为开发者，我们需要意识到应用的安全性，我们不希望用户数据被泄露或者用户会话被劫持。

* Is the HTTP client configured to use HTTPS?

* HTTP客户端是否配置使用HTTPS？

* Is the HTTP client configured to use certificate pinning and messages authentication with HMAC?

* HTTP客户端是否配置使用证书绑定，消息是否使用HMAC验证？

* Is the application persisting user sensitive information? Where?

* 应用是否持久化用户敏感信息？存放在哪里了？

* Is the application persisting information out of the internal storage system?

* 应用是否在内置存储外存储信息？

* Is the application logging traces when running a release build?

* 运行一个发布版时，应用是否记录日志跟踪信息？

* Is the application code obfuscated?

* 应用代码有没有混淆？

* Is the application exposing any Android content provider, receiver or service to other applications?

* 应用是否对外暴露任何content provider, receiver或者service给其他应用？

* Is the application "debuggable" value disabled in the release build?

* 发行版中，应用的“debuggable”标志是否被禁用了？

**Push Notifications:推送通知：**

Push is a great mechanism to keep our users informed about relevant content at any time, but it is a more complex problem that it looks at first glance

推送通知是一种可以在任何时候保持用户关注相关内容的良好机制，但是这个问题并不像第一眼看起来那么简单。

* Is the application using a third party library to implement the push notifications system?

* 应用是否使用第三方库来实现推送通知系统？

* Is the GCM system used to send information to the application inside the push notifications or just to show messages to the user?

* GCM系统是否用来给应用通过推送通知来发送信息还是只是用来给用户显示消息？（这个问题没有理解清楚）

* What is the application behaviour when a push notification is received?

* 应用收到推送通知后的行为是什么？

* What is the application behaviour if the info associated to the push notification is not the one expected?

* 如果和推送通知关联的信息并不是我们想要的，这时应用的行为又是什么？

* Are the notifications shown to the user using the compatibility API?

* 通知是否使用了兼容API来显示给用户？

**Performance:性能：**

Performance is critical. Nobody wants to use a crappy, sluggish app in their 400-600$ device. Performance is $.

性能非常关键。没人希望在自己400-600美金购买的设备上运行一个又烂又慢的应用。性能就是金钱。

* Does the application have any memory leak?

* 应用是否有内存泄露？

* Is any memory analyzer like "LeakCanary" configured in the development build?

* 开发版构建中是否配置了类似“LeakCanary”这样类似的内存分析工具？

* Is the Android Strict Mode enabled and configured in the development build?

* 开发版构建中是否配置并启用了Strick Mode？

* What is the application threading usage? Are you using async tasks, intent services or any other third party libraries?

* 应用的线程使用情况怎么样？有没有使用async task，intent services或者其他第三方库？

* Is the number of background threads causing performance issues?

* 后台线程的数量是否造成了性能问题？

* Do you use any scheduler policy or just create threads on demand?

* 有没有使用任何线程调度策略，还是有需要就创建线程？

* Do you keep in mind the Android Doze Mode?

* 有没有随时关注Android的Doze Mode？

* Is the application listening to events related to the network state or any repetitive event from the operating system?

* 应用是否监听了网络状态事件，或者其他操作系统的重复事件？

* Is the main thread used to perform tasks only related to the user interface code?

* 主线程是否只用来执行用户界面相关的任务？

* Is the application using any caching policy?

* 应用有没有使用任何缓存策略？

* Is the HTTP client configured to use a timeout?

* HTTP客户端有没有配置超时？

* Is the HTTP client configured to use GZIP?

* Is the application UI running at 60 frames per second?

* UI能否达到每秒60的帧率？

* Is there any custom view implemented allocating a lot of memory or executing expensive tasks in the UI thread?

* 有没有分配大量内存，或者在UI线程执行耗时炒作的自定义控件？

* Are you testing your app on lower-end devices?

* 有没有在低端设备上测试你的应用？

* Is the recycler views scrolling sluggish? 

* 自循环列表控件（recycler view）的滚动有没有卡顿？

* Is the images handling implemented using any third party library or do you have your custom solution?

* 图片处理实现使用了第三方库还是用自定义的解决方案？

* Are the images consumed resized to the screen size or downloading the one associated to the device screen?

* 使用图片的时候是在设备上缩放到屏幕大小还是下载和屏幕大小相关联的图片？

* Is the memory usage reasonable?

* 内存使用是否合理？

* Are they using using the java "static" modifier properly?

* 有没有正确使用“static”修饰符？

* Is any task related to images management handling more than one image at the same time?

* 有没有图片管理相关的功能一次同时处理一张以上的图片的情况？

* Is the stats tracking system working on a background thread configured with the correct priority?

* 状态跟踪系统是不是运行在一个正确配置了优先级的后台线程上？

* Is the code optimized in the release build?

* 代码是否在发行版构建中做了优化？

**Java Packages Structure:Java包结构：**

A good packaging structure will make our code more scalable

* 好的包结构可以让代码更好扩展

* Are packages used to split the code by features or by concepts? E.g. Login vs User

* 包是根据功能还是概念来分割的？比如，登录（Login）相对与用户（User）。

* Are the java visibility modifiers used to hide implementation details inside packages?

* 在包内部有没有使用java的可见性修饰符来隐藏实现细节？

* Are packages out of the root package?

* 有没有包游离在根包之外？

* Is the tests folder following the same packages structure implemented in the source folder?

* 测试目录和源代码目录是否遵循了同样的包结构？

* Are the features organized using the same packages structure?

* 功能需求是否用同样的包结构来组织？

* Is there any class out of the correct package?

* 有没有任何放在不正确包里面的类？

* Are the naming conventions followed so the packages are homogeneously named?

* 有没有遵循一定的命名规范，这样包命名就可以比较一致？

* Is the root package name related to the company name?

* 根包的名字是否和公司名字相关？

**Codestyle:代码风格：**

A consistent code base in terms of styling helps our engineers to read code in an easier way. An engineer is suppose to read MUCH more code than she/he writes so this is an important concept

风格一致的代码基础库可以让工程师更容易阅读代码。工程师通常读的代码远多于写的代码，所以这个概念很重要。

* Is the codestyle homogeneous?

* 风格是否保持一致？

* Do you use hungarian notation?

* 是否使用匈牙利命名法？

* Is there any checkstyle tool configured and passing?

* 有没有配置并通过代码风格检查工具？

* Does the code follow the Java codestyle?

* 代码是否遵循java的代码风格？

* Do you use tabs or spaces?

* 使用tab还是空格？

* Are the classes correctly named?

* 类名是否正确？

* Do you use "I" as interfaces prefix or “Impl” as implementation suffixes?

* 使用“I”作为接口前缀还是使用“Impl”作为后缀？

* Do you use the correct names for variables?

* 变量名是否正确？

* Do you use the correct names for fields?

* 字段命名是否正确？

* Do you use the correct names for methods?

* 方法命名是否正确？

* Are the attributes and method visibility modifiers used properly?

* 属性和方法的可见性修饰符是否正确使用了？

* Is the code in English?

* 代码是否用英语来写？

* Do you use javadoc?

* 是否使用javadoc？

* Do you write code comments?

* 是否写注释？

* Do you use constants or enums to avoid duplicated literals?

* 是否使用常量或者枚举量来避免出现重复的字面量？

**Offline Implementation:离线实现：**

Providing a good offline experience is a differentiating factor for our applications.

好的离线体验是我们应用的一个差异化因素。

* Is the application usable when there is no internet connection?

* 断网时应用是否可以正常使用？

* What is the application behaviour when the network connection is slow?

* 网速慢时应用的行为是什么？

* What is the application behaviour when a request has been cut due to a network failure?

* 网络请求被网络中断时应用的行为是什么？

* Are the application data modifications synchronized with the application backend once the connection has been recovered?

* 应用的数据更改是否在应用后端连接恢复时马上进行同步？

* Is there any timeout configured related to the network connections?

* 网络连接有没有设置超时？

* Is there any HTTP caching policy configured?

* 有没有配置HTTP缓存策略？

* Is the user session renegotiated automatically?

* 用户会话是否自动重新协商？

**Architecture:架构：**

The application architecture from the code point of view is one of the parts of an audit that gives us more insight about the application. During the application architecture review we will be focused in concepts related to the S.O.L.I.D and Clean Code principles.

代码角度的应用架构是整个审查规则中让我们对应用有更多洞察的一部分。在应用架构复审的时候我们将关注SOLID相关的概念以及Clean Code原则。

**Presentation Layer Implementation:展示层实现：**

* Is any pattern related to GUI implementation used in the application? Model View Presenter or Model View ViewModel could be two of the most commonly used patterns to develop applications. Is it implemented properly?

* 针对GUI实现，应用有没有相应的模式？MVP和MVVM可能时开发应用时最常见的两种模式。有没有正确实现呢？

* Is the presentation layer implementation coupled to the view implementation?

* 展示层实现是否和显示层实现耦合了？

* Is the view implementation coupled to the model implementation?

* 显示层实现和模型层实现是否耦合了？

* Does the presentation layer implement business requirements?

* 展示层是否实现了业务需求？

* Does the view implementation use the Android SDK tools properly?

* 显示层实现是否正确使用了Android SDK里面提供的工具？

* Does you use third party libraries to simplify the view implementation?

* 是否使用了第三方库来简化显示层实现？

* Are the different features implemented in different activities or fragments?

* 不同特性用activity还是fragment实现？

* Is the common UI behaviour centralized?

* 公共的UI行为是否统一处理了？

* Do you use custom views to reuse UI code?

* 有没有使用自定义控件来重用UI代码？

**Domain Implementation:领域实现：**

* Is there any domain layer or is all the business logic implemented inside the presentation layer?

* 领域层甚至说全部业务逻辑是否有在展示层实现？

* Are the domain rules and different application requirements expressed inside the main business logic entities?

* 领域规则和不同应用的需求是否在主要的业务逻辑主体里面进行描述？

* Is the domain layer implemented using the object oriented principles?

* 领域层实现是否用了面向对象的原则？

* Is the domain layer coupled to the Android SDK or any third party library?

* 领域层实现是否和Android SDK或者任何第三方库耦合？

* Is the domain layer coupled to the presentation layer?

* 领域层是否和展示层耦合？

* Is the domain model anemic?

* 领域模型是否很少？

* Do you use rich domain models?

* 是否使用大量的领域模型？

* Is the code based on low coupled and high cohesive components?

* 代码是否构建在高内聚低耦合的模块中？

* Is the error handling implemented using exceptions or any other error mechanism?

* 错误处理时用Exception还是其他错误处理机制实现？

* Is the data mapped between different layers?

* 不同层次的数据是否进行了映射？

* Are the external components design (like the database schema or the json parsing) influencing the domain model design?

* 外部设计（比如数据库模型或者JSON解析）是否影响领域模型设计？

* Are the developers abusing inheritance?

* 开发者有没有滥用继承？

* Is the code duplicated?

* 代码是否重复？

* Is there any dependency injection library or service locator configured?

* 有没有使用依赖注入库或者服务发现器？

* Is the class/method complexity too high?

* 类或者方法复杂度是否过高？

**API Client Implementation:API客户端实现**

* Is the API client implementation coupled to the Android SDK.

* API客户端实现是否和Android SDK耦合？

* Is the API client leaking implementation details related to the HTTP client or the library used to implement the networking layer?

* API客户端是否泄露了HTTP客户端或者网络层实现的相关细节？

* Is the API client sending the correct headers?

* API客户端是否发送了正确的头？

* What is the API client behaviour based on different HTTP responses?

* 对应不同的HTTP相应，API客户端的行为是什么？

* Is the API client implementing authentication mechanisms?

* API客户端是否实现了验证机制？

* Is the renew session process properly implemented?

* 刷新会话的过程是否正确实现了？

* Does the JSON serializer support obfuscation?

* JSON序列化工具是否支持混淆？ 

* Is the API client implementation segregated in different API clients?

* API客户端是否和不同API分割开（这里没有完全理解）?

**Storage Implementation:存储实现：**

* Where is the information stored?

* 信息存放在哪里？

* Are you reading/writing data from/in the storage using transactions?

* 从存储读出或者写入数据时有没有使用事务？

* Is the storage saving user sensitive information securely?

* 存储是否安全存放了用户的敏感信息？

* Is the storage layer using any third party libraries?

* 数据层是否使用第三方库？

* Is the storage layer leaking implementation details?

* 数据层是否泄露了实现细节？ 

* Is the storage tables/schemas properly modeled?

* 存储的表或者模型是否正确建模了？

* Are the queries sent to the storage optimized?

* 发送到存储的请求是否做了优化？

* Are the Android SDK persistence APIs used to store the data in the correct place? Data to the database, preferences or small data to the Shared Preferences and files into disk?

* 是否在正确的场合使用了Android SDK的持久化API？数据放数据库，选项或者小数据放Shared Preferences，文件存放在磁盘上？

**Testability:可测试性：**

* Does the application have tests?

* 应用是否有测试？ 

* Is the application testable?

* 应用是否可测试？

* Is the application coverage based on different (unit/integration/end-to-end) tests?

* 应用是否覆盖不同测试（单元测试，集成测试，端到端测试）？

* Are the tests correctly named?

* 测试命名是否正确？

* Are the tests properly scoped?

* 测试是否正确划分了范围？

* Is there overspecification in the tests?

* 测试中有没有过度描述？ 

* Is the execution time reasonable?

* 测试执行事件是否合理？

* Is the code coverage too low?

* 测试覆盖率是否过低？

* Are there any ignored tests?

* 有没有被忽略的测试？

* Are there any flaky tests?

* 有没有不可靠的测试？

* Do you use the up to date testing frameworks?

* 有没有使用最新的测试框架？

* Are there any tests without asserts?

* 有没有没有断言的测试？

* Are tests written by the same developers implementing the production code?

* 测试是否由实现线上代码的相应开发者编写？

* Do you have a manual QA team?

* 有没有手工QA团队？

* Do you have a QA team automatizing part of the tests?

* 有没有QA团队自动化部分测试？

* Do you have any continuous integration system?

* 有没有持续集成系统？

* Do you use builders, factories or mothers to reduce the effort needed to create some entities that are just needed for tests?

* 有没有使用构造类，工厂类或者母亲类来减少创建测试所需实体的麻烦？

* Are the tests assertions properly written?

* 测试断言是否正确编写？

* Do you perform more than one logic assertion per test?

* 每个测试是否执行了超过一个逻辑断言？

* Do you have different test suites related to the same project?

* 同一个项目是否有不同的测试套件？

* Do you use different testing approaches to test different parts of the application?

* 测试应用不同部分时，你是否使用了不同的测试方法？

* Do you use any monkeyrunner?

* 有没有使用monkey runner？

* Do you follow any TDD or BDD methodologies?

* 你是否遵循TDD或者BDD方法论？

* Do you use java to write the test cases?

* 是否使用java编写测试用例？

Based on this list related to different topics we can assert the application quality. There are other points that we also review but this list contains the most important ones. Are you giving the correct answers to all this questions?

根据这个列表的不同主题，我们能够确保应用的质量。我们还考察一些其他的点，但是这个列表包含了最重要的部分。你能给出这些问题的正确回答吗？

***By Pedro Vicente Gómez Sánchez.由Pedro Vicente Gómez Sánchez.编写***
