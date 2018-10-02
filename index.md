---
---
# Karumi Android Audit

* [中文翻译 / Chinese Translation](CN/) by [Zaicheng Qi](https://github.com/vmlinz)
* [русский перевод / Russian Translation](RU/) by [Artem Kochkin](https://github.com/kolipass) and [maxpolezhaev](https://github.com/maxpolezhaev)
* [Portuguese Translation / Tradução Português](PT/)
 by [Tiago Barreto](https://github.com/tiagobarreto)

**Your Android app as a crime scene!**

Technical audits of iOS and Android applications have become an integral part of our daily job here at Karumi. Even though it can look easy, there are quite a few implementation details to review when performing such audit. In this document we are going to review what we believe are the most important things to check, separated by technical area. 

**Version Control System:**

Whether the engineers are using version control, which system and using what process tells us a lot of things about the software development process. 

* Do you have a properly configured *ignore file so IDE metadata files and other extraneous elements are not under version control?

* Are third party libraries versioned in the internal repository manager (Nexus, Artifactory, etc.) rather than configured as an external dependency?

* Do you use sufficiently concise and descriptive commit messages?

* Is the size of the commits reasonable?

* Are all the files in a commit related to the same issue or feature?

* Are you using branches following any branching scheme like "feature branch" or “git-flow”? 

* Are these branch names descriptive enough?

* Are you using the pull request/code review system before merging the code into master?

    * Do you have any guidelines regarding what to look for when reviewing a PR?

    * How many comments on average for every PR?

    * How many people review each PR?

    * How many +1 do you need before merging?

    * Who is responsible for closing the branch?

* Are you using release branches to prepare every release?

* How long are your staging process open?

* How many fixes do you introduce into your release candidate before to release it?

* Are you able to checkout the exact code used to build any of the published versions of your app?

* How many hotfixes have you released in the past year?

* Are you squashing the commits in a branch before merging it into the master/develop/ branch?

* Is the master/develop branch ready to be released at any time?

**Build Tools:** 

Being able to reproduce the build process on every developer machine and any other external system as continuous integration is key.

* How many libraries are being used in the project?

* Is the project splitted into different modules?

* Do they consume their dependencies from Maven or Gradle or are they using local jars?

* Is the project dangerously approaching to the dex method count limit? Is it already beyond that point?

* Are you using libraries your project does not need?

* Is the project using multidex?

* Are the external dependencies up to date?

* Are you respecting every third party library license?

* Is the project using any deprecated or abandoned/unmaintained third party library?

* Is the minimum SDK the one required by the product description?

* Is the target SDK up to date?

* Is proguard, or any other obfuscation tool, enabled and properly configured?

* Are the keystore credentials and Google Play Store credentials stored in a secure place?

* Is the application keystore and the credential stored in a secure place?

* Does the application use build types properly?

* Does the application use flavors properly?

* Is the release build type properly configured?

* Is the backup option enabled?

* Is lint enabled and successfully passing?

* Is there any static analysis tool configured and passing?

* Is there any checkstyle configured and passing?

* Is the application id and version name/code configured properly?

* Are you using any structure or strategy for versioning the id?

* Is there any continuous integration tool configured?

* Is the release process automated?

**Android Resources Usage:**

There is a wide range of devices in the Android world, each one with their own screen size, capabilities, etc. You need to be extra careful and leverage some of the Android tools to provide the best possible experience to your user regardless of their device.

* Are there any missing resources for densities, flavors or build types?

* Does the application support all the densities required by the product description?

* Does the application use drawable/mipmap, fonts or vectorial resources?

* Are there any missing translations?

* Is the translation process automated?

* What is the default language for translations?

* Does the application use custom fonts?

* Does the application use configuration values inside the String resources file?

* Is the naming convention used to assign names to the resources homogeneous?

* Are configuration parameters related to the device hardware configured properly?

* Are you supporting tablets?

**Android Layout Usage:**

As we have said before, there is a wide range of Android devices in the world, each one with it own screen size and density. Using Android Layouts correctly is key

* Does the number of layers in the application layouts produce performance issues?

* Do you use themes and styles?

* Do your reuse layouts using the "include" tag?

* Do you use the correct view group type in the layouts implementation?

* Are the layouts configured for different screen sizes?

* Is the naming convention used to assign names to the layouts and widgets homogeneous?

* Are the lists implemented using ListView or RecyclerView widgets?

* Is the Android Support Library properly used?

**Permissions Usage:**

Asking for the right permissions builds trust among your users and can help your app to walk the extra mile and seamlessly integrate with other services to deliver a delightful experience to your users.

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

* Is your security provider up to date?

* Are you using SafetyNet?

* Have you got security tests?

* Do you track/block rooted devices?

* Are you signing your app with the v2 signing key?

* Do you restrict your HTTP client to cipher suites that support perfect forward secrecy?

* Are you scanning your app for known vulnerabilities?

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

* Are they using the java "static" modifier properly?

* Is any task related to images management handling more than one image at the same time?

* Is the stats tracking system working on a background thread configured with the correct priority?

* Is the code optimized in the release build?

**Java Packages Structure:**

A good packaging structure will make our code more scalable

* Are packages used to split the code by features or by concepts? E.g. Login vs User.

* Are the java visibility modifiers used to hide implementation details inside packages?

* Are packages out of the root package?

* Is the tests folder following the same packages structure implemented in the source folder?

* Are the features organized using the same packages structure?

* Is there any class out of the correct package?

* Are the naming conventions followed so the packages are homogeneously named?

* Is the root package name related to the company name?

**Codestyle:**

A consistent code base in terms of styling helps our engineers to read code in an easier way. An engineer is suppose to read MUCH more code than she/he writes so this is an important concept.

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

* Do you use third party libraries to simplify the view implementation?

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

* Is the API client implementation coupled to the Android SDK?

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

