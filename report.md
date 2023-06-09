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

### getCentralValue() 
#### Mutant: Decrement/Increment double field lower/upper [SURVIVED]

The original unit tests for this method did not account for the modification of the class variables lower and upper. As such, in our new tests, we simply called the method twice; if the method modifies the class whether through a postfix or a prefix, then the unit test will catch it when measured against the second method call.


### toString()
#### Mutant: Decrement/Increment double field lower/upper [SURVIVED]

The original unit tests for this method did not account for the modification of the class variables lower and upper. As such, in our new tests, we simply called the method twice; if the method modifies the class whether through a postfix or a prefix, then the unit test will catch it when measured against the second method call.



### contains(double)
#### Mutant: Decrement/Increment double field lower/upper [SURVIVED]

The original unit tests for this method did not account for the modification of the class variables lower and upper. As such, in our new tests, we simply called the method twice; if the method modifies the class whether through a postfix or a prefix, then the unit test will catch it when measured against the second method call.


### shiftWithNoZeroCrossing(double, double)
#### Mutant: Substitute 0.0 with -1.0 [SURVIVED]

The original unit tests for this method did not test a range between [-1,1], essentially meaning if boolean clause would be marked “true” from the mutation and cause the test still to pass. To fix this, simply create a range such as [-0.5, 0.5] and shift it by 1.


### intersects(Range)
#### Mutant: Decrement/Increment double field lower/upper [SURVIVED]

The original unit tests for this method did not account for the modification of the class variables lower and upper. As such, in our new tests, we simply called the method twice; if the method modifies the class whether through a postfix or a prefix, then the unit test will catch it when measured against the second method call.


### expandToInclude(Range, double)
#### Mutant: Decrement double local variable number 1 [KILLED]

The original tests had this mutant on a return line, calling the Range constructor. So decrementing the local variable, value, would return an object that would be different from expected. Thus killing the mutant.

### expand(Range, double, double)
#### Mutant: Replaced double addition with multiplication [KILLED]

The original method is meant to generate a new Range object based on a series of calculations. And simply changing the equation would give a different parameter for the Range constructor and thus returning an object that would be different from expected and killing the mutant.


### shift(Range, double, boolean) 
#### Mutant: negated conditional [KILLED]

If the If-Statement was negated, then it would simply not call the correct constructor arguments and thus returning an object that would be different from expected and killing the mutant.

### shiftWithNoZeroCrossing(double, double)
#### Mutant: negated double local variable [KILLED]

The negated variable is used in the return statement, so unless ‘value’ is set as 0, the returned value would be different to the expected return, and thus killing the mutant.

### equals(Object)
#### Mutant: removed conditional - replaced equality check with true [KILLED]

If the equality check is simply set to ‘true’, then it will return false for all instances of this method call; regardless whether the argument object is equal to the current object. So in the scenario of the tests, an equivalent object will still return false, which would be different to the expected return of true, and thus killing the mutant.


# Report all the statistics and the mutation score for each test class
![](./RangeBefore.png)
![](./RangeAfter.png)
![](./DataUtilitiesBefore.png)
![](./DataUtilitiesAfter.png)


# Analysis drawn on the effectiveness of each of the test classes

Range

testInstersectSameLower()
This test was made to check the lower bound when it has the same value as the range. This will be able to kill mutants that were not being checked by the lower bound beforehand.

testInersectWithSameUpper()
This test was made to check the upper bound with the same value as the range, this test kills mutants that were not being checked by the upper bound beforehand. 

testIntersectDD_one() two () and three() 
This test the increments of the class variables, as there were many mutants were it changed the way it increments survived. Thus the purpose of these tests is to ensure that the way the function increments is always the same and is correct.

testConstrainWithLowerValue() 
Previously, we had mutations that survived the lower bound of this function as we did not take into consideration the lower bound, thus this test was designed to kill those mutants and has improved our mutation coverage by a large amount. 

testConstranWithUpperValue()
Similar to the lower bound, we also did not consider to the upper bound so we had to design tests that were able to kill the mutants that changed the upper bound of the function. Thus, this test was able to increase our mutation coverage greatly.

testShiftFalseBoolMutantTestone() two() and Three()
One of the mutants that were persistent was that a certain boolean value is replaced with the opposite when the result shouldn’t be. Thus, these three tests ensures the combinations of the booleans are tested to eliminate all the possibilities of the same type of mutant happening again.

DataUtilities

calcPosColPosVal2() 
This function is used to test the boundary conditions in DataUtilities as our previous tests fails to test the condition for row < rowCount where it needs a rowCount greater than the valid rows. As such this test case aims to have row being greater than 4 and the Count only being 1  by using mock objects.

calcPosRowPosVal2()
Our previous test still had a mutant where the boundary conditions were able to bypass the tests, therefore, this test aims to have a boundary condition where the row and rowcount are equal to each other. This will allow the running total of column to be zero since there is no path to be taken and has ensured that this mutant has been killed.

calcPosRowPosValNull2()
During our previous test there was a mutant where n!= null was able to survive because we did not test a specific part of the null conditions, this having this specific null value as n will make the row disregard this value when calculating the sum of the column. This tests aims to provide that negation for the null value being ignored.

calcPosRowPosValNull2()
There was another mutation where it dealt with conditional boundaries where the specific line of code was if(col < colCount). By passing 1 into the validRows, the function colCount and col will also get 1 as a value and therefore killing this specific mutant.

# A discussion on the effect of equivalent mutants on mutation score accuracy
As we have been taught in class, a mutant is considered to have been "killed" if it produces different outputs than the original program when running the same test case, while it is considered to have "survived" if it produces the same outputs. The accuracy of the mutant score is a measure of the test case's fault-revealing power. The more mutants killed, the higher the test case's power. However, a problem in mutation testing is the presence of equivalent mutants, which have the same behaviour as the original program. Since the test set does not actually "kill" these mutants, the accuracy of the mutation score can be inaccurate as a representation of the total killed mutants over the total mutations.



# A discussion of what could have been done to improve the mutation score of the test suites
The mutation score is based on the number of mutants that survive or are killed. To improve mutation scores, testers should write additional test cases that are aimed at killing all mutants. In our case, some mutants can be killed by further testing the boundary conditions, which are often overlooked in testing. This is particularly true for the Range class in Assignment 3. By carefully examining the code and identifying potential weaknesses, testers can create additional test cases that target these areas and improve the mutation score. By doing so, testers can increase the confidence in the code and ensure that it is more robust and reliable.





# Why do we need mutation testing? Advantages and disadvantages of mutation testing

By using mutation testing, testers can build a more robust and comprehensive testing suite, which reduces the probability of bugs in the program.

Mutation testing offers several advantages, including:

- Improving the quality of the test suite: By injecting faults into the code, mutation testing can reveal weaknesses in the test suite, allowing developers to improve the quality of the code by addressing potential issues.
- Helping testers find missed coverage in the test suite: Mutation testing can help identify areas of the code that have not been adequately covered by the test suite, allowing testers to create additional test cases to improve coverage.
- Providing evaluation and feedback of the test suite: Mutation testing provides feedback on the effectiveness of the test suite, allowing developers to determine whether the current tests are sufficient or require additional coverage.

Although mutation testing offers several benefits, it also has some disadvantages, including:

- Manual mutation can be time-consuming: Manually creating mutants can be a tedious and time-consuming process. Moreover, the quality of the mutation generated heavily relies on the expertise and experience of the developer.

- Requires a lot of mutants to have a good test on the test suite: Mutation testing typically requires a large number of mutants to generate useful results. This can make the process time-consuming and resource-intensive, as it can take a while to generate and run all the mutants.

- Equivalent mutants may cause inaccuracies in the mutation test result: Sometimes, two different mutants can have the same effect on the output of the code, even though the underlying code is different. These equivalent mutants can cause inaccuracies in the mutation test results, leading to false positives or false negatives.

# Explain your SELENUIM test case design process
Selenium is used for GUI testing. In this lab, we were asked to test one of three websites: Costco.ca, Amazon.ca, or Ikea.ca. After close inspection and simple testing of each website, we chose to test Costco.ca in this assignment. The simple, minimal design of the Costco website really helped the test run smoothly without many errors. Ikea.ca was also a good website to implement Selenium testing, but in some cases, when starting to record a new test, Selenium might take the tester to Ikea.com, even though we entered www.ikea.com/ca/en/ as our testing website.With Amazon.ca, the website is too complicated and has many dynamic objects and algorithms involved. When testing simple search functions, the search results might differ each time based on the current user settings. Additionally, due to the complicated website design, Selenium often freezes and stops responding. This has happened multiple times, preventing us from conducting any search-related GUI testing on Amazon.ca.
"The GUI test for Costco.ca aims to test basic day-to-day use cases. Initially, we tested functions related to the login process, such as logging in with incorrect information and logging out.Compared to Amazon.ca, Costco's search function is more straightforward and pages load quickly without any unresponsiveness issues. We have also added tests for searching and adding to the shopping cart. Additionally, we have designed a few test cases for useful links on the website. We made sure that contact information and necessary policies can be found on the website, and when clicking on them, they link to the correct page with accurate information.


# Explain the use of assertions and checkpoints
Selenium utilizes assertions and checkpoints to verify that the system behaves as intended. The application executes these checks automatically, making them easy to implement. After a user acts such as clicking a mouse, scrolling, or inputting text, Selenium applies these validations. During test case execution, if an unexpected or incorrect input is encountered, the test case will halt and fail at that specific checkpoint. This process is comparable to JUnit testing, where a failure occurs if the assertion is unsuccessful.


# how did you test each functionaity with different test data
During the test execution, we managed to modify the "Value" field using Selenium once the test case recording had been completed. This enabled us to validate the test behavior by testing various data. In cases where we added further input to the test after the initial input was utilized, we created multiple test cases. For instance, we created separate test cases for logging in with a correct and incorrect username, as each feature resulted in different outputs, and we wanted to preserve both outputs as tests.



# Discuss advantages and disadvantages of Selenium vs. Sikulix
Selenium and Sikulix are tools used for testing user interfaces, but they differ in how they store user input. Selenium uses locators based on HTML code, recording every click, scroll, and mouse position, while Sikulix uses image recognition to save user decisions. Depending on the UI being tested, one format may be more advantageous. For example, Sikulix may be better for interfaces with many buttons and images, while Selenium may be preferred for interfaces with lots of redirection and positioning. Both tools offer the advantage of automating test case execution, allowing users to record a test once without repeating the same actions. However, Sikulix may have the disadvantage of matching multiple elements on the interface. At the same time, Selenium may fail when something unexpected happens during test execution, such as not logging out before running the next test. Selenium also works on web-based applications, while Sikulix can be used for different GUI applications due to its image-based approach.


# How the team work/effort was divided and managed
The work was divided based of who did which class from the previous assignment, this is due to the fact that they would have a better idea of the class and also be able to determine where the mutation happened easier. Therefore, we are able to divide up the work evenly as the workload is also based off of the previous assignments assignments. 



# Difficulties encountered, challenges overcome, and lessons learned
For GUI testing, the Selenium software felt outdated and not really suitable for newer webpages with a lot of functionality. As mentioned above, Selenium often freezes and becomes unresponsive when running tests in certain circumstances.
Selenium also does not come with an auto-save or quick save feature, and it is very easy to close the software by accident. When this happens, Selenium does not prompt the user to save before closing. Therefore, it is possible for a tester to lose all of their test cases if the software is accidentally closed (not if that this has happened to me).
In addition, Selenium does not isolate the test environment. It will run on the current browser settings, including whether an account is already logged in or if there are items in the shopping cart. This is a bit of a hassle as it might allow the same test cases to run under different settings and generate different results.


# Comments/feedback on the lab itself
It is a bit difficult to set up pitest in Eclipse, mnore deatailed docutementation would help. In addition the pitest runs pretty slow, it might arrise some time issues during the lab demo. 
As of Selenium GUI testing, althrough it is very simple to use and covered in class, some more guide would be helpful. 


