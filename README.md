# Contents-and-Usage-of-Contained-Scripts
This is a landing page of demo assets that the field has found useful as part of a core demo or tailored demo.

**Most** of these scripts are not considered part of the "core" demo assets which means you will **not** find them delivered as part of the [devops.dockerapp](https://hub.docker.com/r/admpresales/devops.dockerapp/) or the [devops](https://hub.docker.com/r/admpresales/devops/) images.  Scripts that are shown on this page that are part of the core scripts delivered in the Devops image are noted with '(c)'.  For example:
```
leanft-gherkin (c)
```

Instructions on [How to add tests to devops container](#how-to-add-test-to-devops-container) can be found below. Alternatively, you could just clone or fork the test into the file system of NimbusClient or NimbusServer.  

Instruction and expectations for those developing new scripts can be found below:<br>
[Expectations for those developing new scripts](#Expectations-for-those-developing-new-scripts)

<b>Note that the following sections are "old" and do not completely reflect what I am proposing in this doc. Most of what I have added, and want feedback on, is in the "Expectations for those developing new scripts" section.
</b>

## LeanFT Scripts
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp
Script Name
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Note|
|----------------| ---------------------------------- |
|[leanft-gherkin](https://github.com/admpresales/leanft-gherkin) (c)| IntelliJ - maven project which uses LeanFT and gherkins feature |file and cucumber for execution.  This one actually executes a test against AOS |
|octane-gherkin](https://github.com/admpresales/octane-gherkin) (c)|Very similar to LeanFT_Gherkins with the exception that the Gherkin step definitions are left empty so it runs faster.  The intent here is used when focusing on Octane demos only and LFT is not a focus. |
|[aos-web-lft4se](https://github.com/admpresales/aos-web-lft4se) | Maven project demonstrating using LeanFT for Selenium in a simple project.  This was created using the Selenium OIC. |
|[simple-lft-selenium](https://github.com/admpresales/simple-lft-selenium)|Simple script demonstrating Selenium and LFT used together.  With webdriver launching and LFT attaching to browser and using the Verify and Reporter classes |
|[oscillating](https://github.com/admpresales/oscillating)|This script was used as part of a training session to demonstrate how areas of the Octane Pipeline Analysis screen gets populated based on how scripts run, pass, fail, etc. |
|[Mobile_AOS_Test - Android](https://github.com/panama69/Mobile_AOS_Test)|Simple LFT test against AOS on an Android device
|[Mobile AOS Test - iOS](https://github.com/admpresales/aos-ios-leanft)|LeanFT tests against AOS on an iOS device |
|[LeanFT_AppliTools](https://github.com/panama69/LeanFT_AppliTools)|Very simple LeanFT/AppliTools test using C#.  The code came from AppliTools website but I add information to readme to aid in setting things up |
|[LeanFT_Cross_Browser_Mobile](https://github.com/panama69/LeanFT_Cross_Browser_Mobile)|Simple script showing execution across the desktop Firefox browser and the iPhone Safari browser. |
|[testng-example](https://github.com/admpresales/testng-example)|Simple TestNG tests using LeanFT Reports to demonstrate how to run TestNG in parallel and pass arguments to a test |

## UFT Scripts
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Script Name |  Note
 ---------------- | ----------------------------------
[flight-api-with-gui-verification            ](https://github.com/admpresales/flight_api_with_gui_verification) | Demonstrates using API test interacting (calling) GUI test.  This script is great for showing customer the value of using API testing with their regression suites. Much of regression testing is setting up specific data scenarios to users can perform the actual test they need. Using API for the setup can drastically reduce the overall execution time.
[comprehensive-uft-test-flightgui](https://github.com/admpresales/comprehensive-uft-test-flightgui) | UFT script demonstrating several capabilites of UFT (courtesy Ron Sercely)

## VuGen scripts
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Script Name | Note |
| ---------------- | ---------------------------------- |
|[TruClient Native Mobile    ](https://github.com/admpresales/AOS_TruClient_buy_headphones_with_transactions) | This is a simple TruClient mobile script for iOS. Works against the AOS app|

## Utility scripts
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Script Name | Note |
| ---------------- | ---------------------------------- |
|[jenkins-jobs](https://github.houston.softwaregrp.net/AMSPreSales-Demos/jenkins-jobs)|This is a set of scripts to extract or deploy Jenkins views and jobs.  It also contains the jobs and views from the released version of the devops docker image|
|[Docker Server Scripts ](https://github.com/panama69/DockerScripts.git)|Scripts used to start various containers for the demos|

## Branching and Merging strategies
[A Successful Git Branching Model](http://nvie.com/posts/a-successful-git-branching-model/)

[Tags & Releases](https://softwareengineering.stackexchange.com/questions/255404/how-to-use-github-branches-and-automatic-releases-for-version-management)

[Git Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

[Git Tip: Tags](http://alblue.bandlem.com/2011/04/git-tip-of-week-tags.html)

## How to add test to devops container
If you can connect to www.github.com from your devops container, then from a terminal window on NimbusServer with the devops container up, run the following command:

```
docker exec devops bash -c "su -s /bin/bash -c 'git clone --mirror https://github.com/admpresales/aos-web-lft4se.git /gitrepo/aos-web-lft4se' apache"
```

If your container can not connect to the internet, then use these from your command window:

```
git clone --mirror https://github.com/admpresales/aos-web-lft4se.git aos-web-lft4se
```
```
docker cp aos-web-lft4se devops:/gitrepo
```
```
docker exec devops bash -c 'chown -R apache:apache /gitrepo/aos-web-lft4se'
```

**You would of course replace the url and name to the git project you wish to use in the above steps**

## Expectations for those developing new scripts
####README.md
All projects must have a useful README.md. Help on how to create the README.md using the github markdown language can be found:<br>
* [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
* [Markdown Cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* [Basic Writing and Formatting](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
* [Markdown Cheat sheet PDF](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)
```

If you are going to be a lot with Markdown, or something "fancy", you might want to install Markdownad, which allows you to develop Markdown where you see the "code" and results side by side:<br>
[Markdown editor for your desktop](http://markdownpad.com/news/2013/introducing-markdownpad-2)

To make it work on Windows 10 however, you will also need to install awesomium sdk:<br>
[awesomium sdk](http://markdownpad.com/download/awesomium_v1.6.6_sdk_win.exe)

#####Required sections/outline
| Field Name      | Required(Y/N|Other Comments
| ----------------| ---------------------------------- |
Script Name      | Y| Should be same as name of repository, except can use Camel-Case
Description : Y | Should be same as github repository description string
Table of Contents| N | This is a TOC for the README, in case the README is long
Usage| Y | How to use including prerequisites and dependencies
Send Feedback | Y |  Email(s)


####Best practices
#####General
Scripts should be named: <technology-type-target-short_description>

Examples:

	    uft-gui-aos-create_new_account
	    vugen-truclient-aos-sanity

If the technology supports it, there should be at least one checkpoint.

If the technology supports it, there should a parameterized value(s).

#####LeanFt
Test should be verified within both NimbusClient and NimbusServer.

Only maven projects should be used.

LeanFT version should be set to use the latest version of LeanFT by modifying the default pom.xml file. Specifically, in properties create a leanft.version tag, with a value of RELEASE.


    <properties>
        <leanft.version>RELEASE</leanft.version>
    </properties>

Then in each LeanFt <dependency>, replace the hard coded version with ${leanft.version}, as shown here:

    <dependency>
            <groupId>com.hp.lft</groupId>
            <artifactId>sdk</artifactId>
            <version>${leanft.version}</version>
    </dependency>

#####UFT
Web scripts should always be recorded with Internet Explorer so that the active screen is present.

Test replay should be tested against the 3 browsers installed on NimbusClient, i.e, IE, Chrome, Firefox.


#####VuGen

RonK or Michal?
