**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#4 – Mutation Testing and Web app testing**

| Group \#:      |     |
| -------------- | --- |
| Student Names: | Chachi Han    |
|                | Zirui Wang    |
|                | David Tran    |
|                | Bismarck Leung    |

# Introduction
The primary objective of this lab assignment was to acquaint ourselves with mutation testing and the Selenium tool, both of which were introduced in the lectures. To conduct mutation testing, our group utilized the PIT testing tool in Eclipse to determine the mutation coverage. In the second part of the assignment, we employed the Selenium IDE extension on our respective browsers. The purpose of mutation testing was to enhance the error detection capability of the source code by identifying weak spots that needed to be thoroughly tested by creating test cases. The lab also focused on GUI testing, which provided a glimpse into automating test cases and centred on the user interface as the foundation for recording and executing scripts.

# Analysis of 10 Mutants of the Range class 

# Report all the statistics and the mutation score for each test class



# Analysis drawn on the effectiveness of each of the test classes

# A discussion on the effect of equivalent mutants on mutation score accuracy

# A discussion of what could have been done to improve the mutation score of the test suites

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

# Explain your SELENUIM test case design process
Selenium is used for GUI testing. In this lab, we were asked to test one of three websites: Costco.ca, Amazon.ca, or Ikea.ca. After close inspection and simple testing of each website, we chose to test Costco.ca in this assignment. The simple, minimal design of the Costco website really helped the test run smoothly without many errors. Ikea.ca was also a good website to implement Selenium testing, but in some cases, when starting to record a new test, Selenium might take the tester to Ikea.com, even though we entered www.ikea.com/ca/en/ as our testing website.With Amazon.ca, the website is too complicated and has many dynamic objects and algorithms involved. When testing simple search functions, the search results might differ each time based on the current user settings. Additionally, due to the complicated website design, Selenium often freezes and stops responding. This has happened multiple times, preventing us from conducting any search-related GUI testing on Amazon.ca.
"The GUI test for Costco.ca aims to test basic day-to-day use cases. Initially, we tested functions related to the login process, such as logging in with incorrect information and logging out.Compared to Amazon.ca, Costco's search function is more straightforward and pages load quickly without any unresponsiveness issues. We have also added tests for searching and adding to the shopping cart. Additionally, we have designed a few test cases for useful links on the website. We made sure that contact information and necessary policies can be found on the website, and when clicking on them, they link to the correct page with accurate information.

# Explain the use of assertions and checkpoints
Selenium utilizes assertions and checkpoints to verify that the system behaves as intended. The application executes these checks automatically, making them easy to implement. After a user acts such as clicking a mouse, scrolling, or inputting text, Selenium applies these validations. During test case execution, if an unexpected or incorrect input is encountered, the test case will halt and fail at that specific checkpoint. This process is comparable to JUnit testing, where a failure occurs if the assertion is unsuccessful.

# how did you test each functionaity with different test data

# Discuss advantages and disadvantages of Selenium vs. Sikulix
Selenium and Sikulix are tools used for testing user interfaces, but they differ in how they store user input. Selenium uses locators based on HTML code, recording every click, scroll, and mouse position, while Sikulix uses image recognition to save user decisions. Depending on the UI being tested, one format may be more advantageous. For example, Sikulix may be better for interfaces with many buttons and images, while Selenium may be preferred for interfaces with lots of redirection and positioning. Both tools offer the advantage of automating test case execution, allowing users to record a test once without repeating the same actions. However, Sikulix may have the disadvantage of matching multiple elements on the interface. At the same time, Selenium may fail when something unexpected happens during test execution, such as not logging out before running the next test. Selenium also works on web-based applications, while Sikulix can be used for different GUI applications due to its image-based approach.

# How the team work/effort was divided and managed


# Difficulties encountered, challenges overcome, and lessons learned
For GUI testing, the Selenium software felt outdated and not really suitable for newer webpages with a lot of functionality. As mentioned above, Selenium often freezes and becomes unresponsive when running tests in certain circumstances.
Selenium also does not come with an auto-save or quick save feature, and it is very easy to close the software by accident. When this happens, Selenium does not prompt the user to save before closing. Therefore, it is possible for a tester to lose all of their test cases if the software is accidentally closed (not if that this has happened to me).
In addition, Selenium does not isolate the test environment. It will run on the current browser settings, including whether an account is already logged in or if there are items in the shopping cart. This is a bit of a hassle as it might allow the same test cases to run under different settings and generate different results.

# Comments/feedback on the lab itself
It is a bit difficult to set up pitest in Eclipse, mnore deatailed docutementation would help. In addition the pitest runs pretty slow, it might arrise some time issues during the lab demo. 
As of Selenium GUI testing, althrough it is very simple to use and covered in class, some more guide would be helpful. 