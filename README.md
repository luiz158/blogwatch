# Blog Watch

This project contains UI tests for baeldung.com


### Overview

The project uses Selenium framework, Crawler4J and REST Assured for UI tests . The tests can be run in GUI or headless mode. UI browser has been configured with Firefox using gecodriver and tested with Firefox 56.0 (64 bit) on Windows. Headless mode works with PhantomJS and HtmlUnit browsers.


### Running Tests from the IDE

The default configuration executes tests with headless mode in windows environment and target URL is https://www.baeldung.com. The configuration can be changed using following properties:

  - _spring.profiles.active_ - environment variable to either "headless-browser" and "ui-browser"
  - _target.env_ - environment variable should be set to "win" or "linux" for headless browser
  - _base.url_ - to target base URL, for example _http://www.baeldung.com_

These can be set as environment variables via the Eclipse run configuration. 


### Running Tests Using Maven 

Three Maven profiles are available for running tests: 
  - _headless-browser-windows_
  - _headless-browser-linux_ 
  - _ui-brower-windows_

The target URL for all profiles is https://www.baeldung.com. The can be changed using following property

- _base.url_ - to target base URL, for example _http://www.baeldung.com_

### Headless Browser selection

Available headless browsers

- _PhantomJS_ (default)
- _HtmlUnit_

Headless browser can be configured using following system property

- _headless.browser.name_


### Updating List of Posts and Pages


Run _UpdateArticlesAndPagesLinks#updateLinks_ test for updataing list of articles and pages. 

### JUnit Tags

Following tags are available for running tests selectively. Refer Java docs in _GlobalConstants.java_ for details
  - _hourly_
  - _daily_
  - _weekly_
  - _editorial_
  - _github-related_
  - _technical_

### Excluding a URL for tests running in the bi-monthly bild

URLs can be added to the follwoing file to skip a specific test from the bi-monthly build - https://github.com/eugenp/blogwatch/blob/master/src/main/resources/exceptions-for-tests-hitting-all-urls.yaml

### Launch Mode
 
Set environment variable "LAUNCH_FLAG" to either _true_ or _false_ to set launch mode. Default is _false_


### On Jenkins
 
 The tests are running here, [on Jenkins](http://jenkins.baeldung.com/view/site-monitor/view/site-watch/job/sites-monitor/job/site-watch/)
 
### Tests
 The tests which are crossed out are disabled.

| Sr. | Test Name |
| --- | --------- |
| 2 | **givenOnTheHomePage_whenPageLoads_thenJavaWeeklyLinksMatchWithTheLinkText** <br/><br/> daily <br/><br/> Verifies that the Java weekly issue links in the homepage point to correct URLs |
| 3 | **givenOnTheHomePage_whenPageLoads_thenItContainsCategoriesInTheFooterMenu** <br/><br/> daily <br/><br/> Verifies that the CATEGORY menu is available in the homepage footer |
| 4 | **givenOnTheHomePageUrlWithoutWWWPrefix_whenUrlIsHit_thenItRedirectsToWWW** <br/><br/> daily <br/><br/> If we hit http://baeldung.com, it should redirect to http://www.baeldung.com |
| 5 | **givenOnTheHomePage_whenHomePageLoaded_thenNoSevereMessagesInBrowserLog** <br/><br/> daily <br/><br/> This test looks for JS error in the browser console falling in server category |
| 6 | **givenOnTheMicroservicesGuidePage_whenOptinPopupIsLoaded_thenItContainsImages** <br/><br/> daily <br/><br/> This test verifies that the images are displayed properly on _Download Guide_ popup in following URL - http://www.baeldung.com/spring-microservices-guide |
| 7 | **givenArticleWithPopup_whenPopupOpens_thenPopupHasCloseButton** <br/><br/> daily <br/><br/> This test checks that the pop-up, the one which auto lods,  has close button on the following page - http://www.baeldung.com/rest-with-spring-series/ |
| 8 | **givenTheArticleWithSeries_whenArticleLoads_thenPluginLoadsProperly** <br/><br/> daily <br/><br/> Verifies the series plugin on the following page - http://www.baeldung.com/spring-security-registration |
| 9 | **givenTheArticleWithPersistenceEBookDownload_whenPageLoads_thenFooterImageIsDisplayed** <br/><br/> daily <br/><br/> This test checks that the image is displayed properly in the EBook download widget available at the end of following page - http://www.baeldung.com/hibernate-spatial |
| 10 | **givenTheArticleWithGoogleAnalytics_whenArticleLoads_thenArticleHasAnalyticsCode** <br/><br/> daily <br/><br/> This test looks for the Google Analytics code in the following post - http://www.baeldung.com/persistence-layer-with-spring-and-hibernate |
| 11 | **givenThePageWithGoogleAnalytics_whenPageLoads_thenPageHasAnalyticsCode** <br/><br/> daily <br/><br/> This test looks for the Google Analytics code in the following page - http://www.baeldung.com/rest-with-spring-course |
| 12 | **givenBaeldungFeedUrl_whenUrlIsHit_thenItRedirectsToFeedburner** <br/><br/> daily <br/><br/> Baeldung feed URL - http://www.baeldung.com/feed/ should redirect to http://feeds.feedburner.com/Baeldung |
| 13 | **givenTheCategoryPage_whenPageLoads_thenItContainsNoindexRobotsMeta** <br/><br/> daily <br/><br/> For testing that the category pages should have a _robots_ meta tag with _noindex_. Following URL is tested - http://www.baeldung.com/category/series/ |
| 14 | **givenThePagesWithBlankTitle_whenPageLoads_thenItDoesNotContainNotitleText** <br/><br/> daily <br/><br/> This test verifies that the pages which have no title set do not show invalid title - _No Title_. The test runs against a list of following five pages. http://www.baeldung.com/java-weekly-sponsorship/ , http://www.baeldung.com/webinar-rest-with-spring-thank-you , http://www.baeldung.com/webinar-api-security-thank-you , http://www.baeldung.com/webinar-api-discoverability-thank-you , http://www.baeldung.com/webinar-cqrs-thank-you |
| 15 | **givenTheTagArticle_whenArticleLoads_thenItContainsNoindexRobotsMeta** <br/><br/> daily <br/><br/> Verifies that the tag pages should have a _robots_ meta tag with _noindex_. Following URL is tested - http://www.baeldung.com/tag/activiti/ |
| 16 | **givenOnTheHomePage_whenPageLoads_thenItHasOneAboutMenuInTheFooter** <br/><br/> daily <br/><br/> The test verifies that exactly one _ABOUT_ menu is available in the footer of Homepage|
| 17 | **givenOnTheCoursePage_whenPageLoads_thenTrackingIsSetupCorrectly** <br/><br/> daily <br/><br/> Verifies tracking on the course pages. Tracking details are here - https://github.com/eugenp/blogwatch/blob/master/src/main/resources/blog-url-list/coursePagesBuyLinks.json |
| 18 | **givenAllURLs_whenURlLoads_thenItReturns200OK** <br/><br/> weekly <br/><br/> Loops over full list of posts & pages, and verifies that 200OK is returned |
| 19 | **givenAllArticles_whenAnArticleLoads_thenItHasSingleShortcodeAtTheTop** <br/><br/> twice-a-month <br/><br/> Technical<br/><br/> This Test verifies that a single short code is available at the start of every post |
| 20 | **givenAllArticles_whenAnArticleLoads_thenItHasSingleShortcodeAtTheEnd** <br/><br/> twice-a-month<br/><br/> Technical <br/><br/> Test verifies that a single short code is available at the start of every page |
| 21 | **givenAllArticles_whenAnArticleLoads_thenArticleHasNoEmptyDiv** <br/><br/> twice-a-month <br/><br/>Technical<br/><br/> This test loops over all the articles and looks for empty div in code samples. |
| 22 | **givenAllArticles_whenAnArticleLoads_thenImagesPointToCorrectEnv** <br/><br/> twice-a-month <br/><br/>Technical<br/><br/> Verifies that the images in the posts point to live env |
| 23 | **givenAllPages_whenAPageLoads_thenImagesPointToCorrectEnv** <br/><br/> twice-a-month <br/><br/>Technical<br/><br/> Verifies that the images in the pages point to live env |
| 24 | **givenAllArticles_whenAnArticleLoads_thenTheMetaDescriptionExists** <br/><br/> twice-a-month <br/><br/>Editorial<br/><br/> This test verifies that all posts have meta description defined |
| 25 | **givenAllPages_whenAPageLoads_thenTheMetaDescriptionExists** <br/><br/> twice-a-month<br/><br/>Editorial <br/><br/> This test verifies that all pages have meta description defined |
| 26 | **givenArticlesWithALinkToTheGitHubModule_whenTheArticleLoads_thenTheGitHubModuleLinksBackToTheArticle** <br/><br/> twice-a-month<br/><br/>GitHub Related <br/><br/> Almost every post has a link to GitHub module containing the working code. The test verifies that the linked GitHub module links back to the post.  The test looks for a back-link in the, 1- URL linked from the Article 2- Master module (immediate child of /master) 3- Immediate parent of initial(1st) URL, 4- Immediate child of main repository (/eugenp or /Baeldung) |
| 27 | **givenAllArticles_whenAnArticleLoads_thenTheAuthorIsNotFromTheExcludedList** <br/><br/> twice-a-month<br/><br/>Editorial <br/><br/> Loops over all the post and verifies that the author is not from the restricted list. Here is excluded list - https://github.com/eugenp/blogwatch/blob/73b841bedeee0803cc7ee0ae0c28d0d70161805b/src/main/resources/blog.properties#L14 |
| 28 | **givenAnArticleWithTheDripScript_whenTheArticleLoads_thenTheArticleHasTheDripScrip** <br/><br/> daily <br/><br/> Verifies the Drip script on https://www.baeldung.com/spring-cache-tutorial |
| 29 | **givenAPageWithTheDripScript_whenThePageLoads_thenThePageHasTheDripScrip** <br/><br/> daily <br/><br/> Verifies the Drip script on https://baeldung.com/spring-tutorial |
| 30 | **givenOnTheCoursePage_whenThePageLoads_thenAGeoIPApiProviderWorks** <br/><br/> daily <br/><br/> This test loads http://baeldung.com/learn-spring-security-course/ and verifies that any of the following messages is logged in the browser console: </br>VAT Calc Notice: geoIP API provider is set to ipdata </br>VAT Calc Notice: geoIP API provider is set to ipinfo.io</br>VAT Calc Notice: geoIP API provider is set to ipapi.com|
| 31 | **givenOnTheCoursePage_whenThePageLoadsInEUCountry_thenTheVATPricesAreShown** <br/><br/> daily <br/><br/> This test loads http://baeldung.com/learn-spring-security-course/ with EU proxy and verifies that VAT prices are available. The test run on HtmlUnit browser|
| 32 | **givenTheGitHubModuleReadme_theArticlesLinkedInTheGitHubMouduleLinkForwardTotheSameGitHubModule** <br/><br/> twice-a-month<br/><br/>GitHub Related <br/><br/> This test verifies that articles linked in GitHub READMEs link forward to the same GitHub module.</br> The test also documents no of articles linked from READMEs.</br> As of now, the test scans only tutorials (https://github.com/eugenp/tutorials) repo.|
| 33 | **givenTheGitHubModule_theModuleHasANonEmptyReadme** <br/><br/> twice-a-month<br/><br/>GitHub Related <br/><br/> This test verifies that GitHub modules have non empty README. A README not linking to an article is also considered empty. As of now, the test scans only tutorials(https://github.com/eugenp/tutorials) repo.|
| 34 | **givenAllArticles_whenAnArticleLoads_thenMetaOGImageAndTwitterImagePointToTheAbsolutePath** <br/><br/> twice-a-month <br/><br/>Technical<br/><br/> This test verifies that image links in the og:image and twitter:image parameters are absolute. The rest runs on all the posts|
| 35 | **givenAllPages_whenAPageLoads_thenMetaOGImageAndTwitterImagePointToTheAbsolutePath** <br/><br/> twice-a-month<br/><br/>Technical <br/><br/> This test verifies that image links in the og:image and twitter:image parameters are absolute. The test runs on all the pages|
| 36 | **givenOnTheBaeldungRSSFeed_whenTheFirstUrlIsHit_thenItPointsToTheBaeldungSite** <br/><br/> daily <br/><br/> This test verifies that the first link in the Baeldung RSS feed ( https://www.baeldung.com/rss/ ) points to the www.baeldung.com |
| 37 | **givenOnCoursePages_whenAPageLoads_thenItContainsImportantAnchors** <br/><br/> daily <br/><br/> This test verifies that the LSS and RWS course pages contain following anchors: </br>#table</br>#master-class</br>#certification-class |
| 38 | **givenAllArticles_whenAnArticleLoads_thenTheArticleDoesNotCotainWrongQuotations** <br/><br/> twice-a-month<br/><br/>Editorial <br/><br/> This test verifies that the articles does not contain ”> or ”"> characters |
| 39 | **givenAllTheArticles_whenAnArticleLoads_thenJavaClassesAndMethodsCanBeFoundOnGitHub** <br/><br/> on-demand <br/><br/> This test verifies that the Java Classs, Interfaces and Methods match with the code on the GitHub. Job link: http://jenkins.baeldung.com/job/sites-monitor/job/site-watch/job/blogwatch-test-article-code-matches-github/ |
| 40 | **givenAllArticles_whenAnArticleLoads_thenTheArticleHasProperTitleCapitalization** <br/><br/> twice-a-month<br/><br/>Editorial <br/><br/> This test verifies that first character of every word in titles has capital case. |
| 41 | **givenTheBaeldungMediaKitURL_whenPageLoads_thenItReturns200OK** <br/><br/> daily <br/><br/> This test verifies that Baeldung Media Kit URL returns 200OK. Media Kit URL - https://s3.amazonaws.com/baeldung.com/Baeldung+-+Media+Kit.pdf |
| 42 | **givenAllArticles_whenAnalyzingCategories_thenTheArticleDoesNotContainUnnecessaryCategory** <br/><br/> twice-a-month<br/><br/>Editorial <br/><br/> This test reports posts having _Spring_ as well as one or more of following labels: <br/>Spring Security <br/>SpringBoot <br/>Spring Cloud <br/>Spring Web<br/> Spring MVC <br/> |
| 44 | **givenAllArticles_whenAnalyzingCodeBlocks_thenCodeBlocksAreRenderedProperly** <br/><br/> twice-a-month<br/><br/>Technical <br/><br/> This test looks for _&lt;pre&gt;_ tags having _brush_ css class. These tags could be found in the page if code blocks are not rendered properly.  |
| 45 | **givenArticlesWithALinkToTheGitHubModule_whenTheArticleLoads_thenTheArticleTitleAndGitHubLinkMatch** <br/><br/> twice-a-month<br/><br/>GitHub Related <br/><br/> This test verified that Article Title match with the link given in the GitHub Module.  |
| 46 | **givenAllArticles_whenAnalyzingCodeBlocks_thenCodeBlocksAreRenderedProperly** <br/><br/> twice-a-month<br/><br/>Technical <br/><br/> This test verifies that all GitHub links in articles return 200OK|
| 47 | **givenAllArticles_whenAnArticleLoads_thenItDoesNotContainOverlappingText** <br/><br/> twice-a-month<br/><br/>Technical <br/><br/> The test looks for overlapping text in the all posts|
| 48 | **givenAllPages_whenAPageLoads_thenItDoesNotContainOverlappingText** <br/><br/> twice-a-month<br/><br/>Technical <br/><br/> The test looks for overlapping text in the all pages|
| 49 | **givenTheBaeldungRSSFeed_whenAnalysingFeed_thenItIsUptoDate** <br/><br/> daily<br/><br/>Technical <br/><br/> The test loads https://www.baeldung.com/rss, and verifies that the RSS feed is up to date.|
| 50 | **givenURLsWithAnchorsLinkingWithinSamePage_whenAnaysingPage_thenAnHtmlElementExistsForEachAnchor** <br/><br/> daily<br/><br/> This test verifies that page has HTHML elements corresponding to anchors linking within same page. The test reads test data from https://github.com/eugenp/blogwatch/blob/master/src/main/resources/data-for-anchor-test.json|
| 51 | **givenTheContactForm_whenAMessageIsSubmitted_thenItIsSentSuccessfully** <br/><br/> daily<br/><br/> This test verifies that contact form works fine. The test runs on HtmlUnit browser.|
