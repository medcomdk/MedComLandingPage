[Return](../../index.md)

# TouchStone - Getting Started
<hr>

**Table of contents**
* [1 How to register](#1-how-to-register)
* [2 How to run a Touchstone test script based on use cases](#2-how-to-run-a-touchstone-test-script-based-on-use-cases)
* [3 How to execute test scripts in a conformance suite](#3-How-to-execute-test-scripts-in-a-conformance-suite)

<!-- [3 Touchstone .NET client Demo](#3-touchstone-net-client-demo)
 [4 Java FHIR client setup](#4-java-fhir-client-setup) -->

This page presents a short introduction to the test tool called "TouchStone", which is used to perform tests of MedCom FHIR standards. The introduction is based on Touchstone's own guides and is divided into three sections: The first section explains how to register on Touchstone, the second section describes how to run a test script, while the third section explains how to execute test scripts in a conformance suite. 



## 1 How to register

1. To register, please go to <a href="https://touchstone.aegis.net/touchstone/login" target="_blank">Touchstone</a> <a href="https://touchstone.aegis.net/touchstone/userguide/html/registration-and-login/register.html" target= "_blank">and follow the steps.</a>

2. To execute a test, you need to be a member of an organization. If your organization already exists, assign yourself to it. If you are the first user from your organization, <a href="https://touchstone.aegis.net/touchstone/userguide/html/registration-and-login/membership.html#new-organization" target="_blank"> please create your organization by following the steps below.</a> 

3. You need to be part of the MedCom OrgGroup to access the test scripts. To become a member of the MedCom OrgGroup, you need to request membership via the dropdown menu 'Org Groups'. Search for MedCom in the search box and click 'Join'.

> Note: You need to wait until we accept your request before you can run the test. As soon as we accept your request, you will be notified via email. Please check your spam folder in case the email is directed there.
<br>

## 2 How to run a Touchstone test script based on use cases

1. To run Touchstone test scripts, you first need to create a test system. Sign into your TouchStone account click on the "Test system" button in the top menu and choose "New Test System". Follow the first two steps in the following  <a href="https://touchstone.aegis.net/touchstone/userguide/html/test-systems/creating.html" target="_blank">guide</a>. 
 >Note: When creating a "Test system", you need to choose whether the system that you want to test schould act as 'origin' or 'destination'.

2. Then create the "Test setup" by  <a href="https://touchstone.aegis.net/touchstone/userguide/html/executing-tests/test-setup.html" target="_blank"> following these steps</a>. 
<!-- 3. Ensure that you have a program that can build and use API to test   -->
3. To execute the test, choose the test script under “Test Definition” and <a href="https://touchstone.aegis.net/touchstone/userguide/html/executing-tests/test-execs.html" target="_blank">follow the steps</a>.  
4. To read the test results, follow these <a href="https://touchstone.aegis.net/touchstone/userguide/html/executing-tests/test-exec-results.html" target="_blank">steps</a>.

## 3 How to execute test scripts in a conformance suite

1. To be able to execute test scripts in a conformance suite, you need to have created a user, joined your organization, become a member of the MedCom OrgGroup, and set up a test system.

2. Go to "Conformance" → "Suites". Here you can find all the conformance suites available to you. You can filter the suites created by MedCom by using the "Owned by" filter.

3. Click on the suite you want to execute. When you see the list of scripts in the suite, select the test system you created earlier from the Client dropdown menu.

4. To execute the scripts, you can either:
* Run all scripts by marking them all and choosing Execute Selected.
* Or run individual scripts by selecting them separately.

<!-- ## 3 Touchstone .NET client Demo
[Demo of a .NET client](https://github.com/medcomdk/touchstone-client-demo-dotnet) calling the MedCom Touchstone test Suite 


## 4 Java FHIR client setup
[http://svn.medcom.dk/svn/drafts/TestProcedurer/Touchstone/MedcomTouchstoneTest/java%20FHIR%20client.pptx](http://svn.medcom.dk/svn/drafts/TestProcedurer/Touchstone/MedcomTouchstoneTest/java%20FHIR%20client.pptx) -->

<!-- ## 5 Release Notes

[The latest changes of this page can be found here.](ReleaseNotesTouchStoneGettingStarted.md) -->