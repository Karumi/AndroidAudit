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

**Android Layout Usage:**

As we have said before, there is a wide range of Android devices in the world, each one with it own screen size and density. Using Android Layouts correctly is key

* Does the number of layers in the application layouts produce performance issues?

* Do you use themes and styles?

* Do your reuse layouts using the "include" tag?

* Do you use the correct view group type in the layouts implementation?

* Are the layouts configured for different screen sizes?

* Is the naming convention used to assign names to the layouts and widgets homogeneous?

* Are the lists implemented using ListView or RecyclerView widgets?

* Is the Android Support Library properlyused?

**Permissions Usage:**

Asking for the right permissions builds trust among your users and can help your app to walk the extra mile and seamlessly integrate with other services to deliver a delightful; experience to your users.

* Are all the requested permissions really needed?

* Is there any permission used maliciously?

* Is there any permission missing?

* Is the target SDK used greater than 23 and the "dangerous permissions" requested using the compatibility permissions system?

* Are the permission requested when they are going to be used?

* Is there any feedback shown to the user explaining why the permission is needed?

**Security Issues:**

As developers we need to be conscious about our app security, we don’t want our user’s data to be leaked or their sessions stolen

* Is the HTTP client configured to use HTTPS?

* Is the HTTP client configured to use certificate pinning and messages authentication with HMAC?

* Is the application persisting user sensitive information? Where?

* Is the application persisting information out of the internal storage system?

* Is the application logging traces when running a release build?

* Is the application code obfuscated?

* Is the application exposing any Android content provider, receiver or service to other applications?

* Is the application "debuggable" value disabled in the release build?

**Push Notifications:**

Push is a great mechanism to keep our users informed about relevant content at any time, but it is a more complex problem that it looks at first glance

* Is the application using a third party library to implement the push notifications system?

* Is the GCM system used to send information to the application inside the push notifications or just to show messages to the user?

* What is the application behaviour when a push notification is received?

* What is the application behaviour if the info associated to the push notification is not the one expected?

* Are the notifications shown to the user using the compatibility API?

**Performance:**

Performance is critical. Nobody wants to use a crappy, sluggish app in their 400-600$ device. Performance is $.

* Does the application have any memory leak?

* Is any memory analyzer like "LeakCanary" configured in the development build?

* Is the Android Strict Mode enabled and configured in the development build?

* What is the application threading usage? Are you using async tasks, intent services or any other third party libraries?

* Is the number of background threads causing performance issues?

* Do you use any scheduler policy or just create threads on demand?

* Do you keep in mind the Android Doze Mode?

* Is the application listening to events related to the network state or any repetitive event from the operating system?

* Is the main thread used to perform tasks only related to the user interface code?

* Is the application using any caching policy?

* Is the HTTP client configured to use a timeout?

* Is the HTTP client configured to use GZIP?

* Is the application UI running at 60 frames per second?

* Is there any custom view implemented allocating a lot of memory or executing expensive tasks in the UI thread?

* Are you testing your app on lower-end devices?

* Is the recycler views scrolling sluggish? 

* Is the images handling implemented using any third party library or do you have your custom solution?

* Are the images consumed resized to the screen size or downloading the one associated to the device screen?

* Is the memory usage reasonable?

* Are they using using the java "static" modifier properly?

* Is any task related to images management handling more than one image at the same time?

* Is the stats tracking system working on a background thread configured with the correct priority?

* Is the code optimized in the release build?

**Java Packages Structure:**

A good packaging structure will make our code more scalable

* Are packages used to split the code by features or by concepts? E.g. Login vs User

* Are the java visibility modifiers used to hide implementation details inside packages?

* Are packages out of the root package?

* Is the tests folder following the same packages structure implemented in the source folder?

* Are the features organized using the same packages structure?

* Is there any class out of the correct package?

* Are the naming conventions followed so the packages are homogeneously named?

* Is the root package name related to the company name?

**Codestyle:**

A consistent code base in terms of styling helps our engineers to read code in an easier way. An engineer is suppose to read MUCH more code than she/he writes so this is an important concept

* Is the codestyle homogeneous?

* Do you use hungarian notation?

* Is there any checkstyle tool configured and passing?

* Does the code follow the Java codestyle?

* Do you use tabs or spaces?

* Are the classes correctly named?

* Do you use "I" as interfaces prefix or “Impl” as implementation suffixes?

* Do you use the correct names for variables?

* Do you use the correct names for fields?

* Do you use the correct names for methods?

* Are the attributes and method visibility modifiers used properly?

* Is the code in English?

* Do you use javadoc?

* Do you write code comments?

* Do you use constants or enums to avoid duplicated literals?

**Offline Implementation:**

Providing a good offline experience is a differentiating factor for our applications.

* Is the application usable when there is no internet connection?

* What is the application behaviour when the network connection is slow?

* What is the application behaviour when a request has been cut due to a network failure?

* Are the application data modifications synchronized with the application backend once the connection has been recovered?

* Is there any timeout configured related to the network connections?

* Is there any HTTP caching policy configured?

* Is the user session renegotiated automatically?

**Architecture:**

The application architecture from the code point of view is one of the parts of an audit that gives us more insight about the application. During the application architecture review we will be focused in concepts related to the S.O.L.I.D and Clean Code principles.

**Presentation Layer Implementation:**

* Is any pattern related to GUI implementation used in the application? Model View Presenter or Model View ViewModel could be two of the most commonly used patterns to develop applications. Is it implemented properly?

* Is the presentation layer implementation coupled to the view implementation?

* Is the view implementation coupled to the model implementation?

* Does the presentation layer implement business requirements?

* Does the view implementation use the Android SDK tools properly?

* Does you use third party libraries to simplify the view implementation?

* Are the different features implemented in different activities or fragments?

* Is the common UI behaviour centralized?

* Do you use custom views to reuse UI code?

**Domain Implementation:**

* Is there any domain layer or is all the business logic implemented inside the presentation layer?

* Are the domain rules and different application requirements expressed inside the main business logic entities?

* Is the domain layer implemented using the object oriented principles?

* Is the domain layer coupled to the Android SDK or any third party library?

* Is the domain layer coupled to the presentation layer?

* Is the domain model anemic?

* Do you use rich domain models?

* Is the code based on low coupled and high cohesive components?

* Is the error handling implemented using exceptions or any other error mechanism?

* Is the data mapped between different layers?

* Are the external components design (like the database schema or the json parsing) influencing the domain model design?

* Are the developers abusing inheritance?

* Is the code duplicated?

* Is there any dependency injection library or service locator configured?

* Is the class/method complexity too high?

**API Client Implementation:**

* Is the API client implementation coupled to the Android SDK.

* Is the API client leaking implementation details related to the HTTP client or the library used to implement the networking layer?

* Is the API client sending the correct headers?

* What is the API client behaviour based on different HTTP responses?

* Is the API client implementing authentication mechanisms?

* Is the renew session process properly implemented?

* Does the JSON serializer support obfuscation?

* Is the API client implementation segregated in different API clients?

**Storage Implementation:**

* Where is the information stored?

* Are you reading/writing data from/in the storage using transactions?

* Is the storage saving user sensitive information securely?

* Is the storage layer using any third party libraries?

* Is the storage layer leaking implementation details?

* Is the storage tables/schemas properly modeled?

* Are the queries sent to the storage optimized?

* Are the Android SDK persistence APIs used to store the data in the correct place? Data to the database, preferences or small data to the Shared Preferences and files into disk?

**Testability:**

* Does the application have tests?

* Is the application testable?

* Is the application coverage based on different (unit/integration/end-to-end) tests?

* Are the tests correctly named?

* Are the tests properly scoped?

* Is there overspecification in the tests?

* Is the execution time reasonable?

* Is the code coverage too low?

* Are there any ignored tests?

* Are there any flaky tests?

* Do you use the up to date testing frameworks?

* Are there any tests without asserts?

* Are tests written by the same developers implementing the production code?

* Do you have a manual QA team?

* Do you have a QA team automatizing part of the tests?

* Do you have any continuous integration system?

* Do you use builders, factories or mothers to reduce the effort needed to create some entities that are just needed for tests?

* Are the tests assertions properly written?

* Do you perform more than one logic assertion per test?

* Do you have different test suites related to the same project?

* Do you use different testing approaches to test different parts of the application?

* Do you use any monkeyrunner?

* Do you follow any TDD or BDD methodologies?

* Do you use java to write the test cases?

Based on this list related to different topics we can assert the application quality. There are other points that we also review but this list contains the most important ones. Are you giving the correct answers to all this questions?

***By Pedro Vicente Gómez Sánchez.***

