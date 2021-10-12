## Continuous testing
Continuous testing is the execution of tests repeatedly against a code base and deployment environment. In practice, continuous testing is the most difficult part of a continuous delivery pipeline to keep up to date. Continuous testing provides quality gates throughout the pipeline and increases confidence in code long before production.


* **Automation is the key.** Automated unit, integration, coded UI, and load tests are common in continuous testing.
* **Use an iterative and incremental approach.** Depth of testing often progresses as an environment gets closer to production.

## Beta Testing and Progressive Exposure <br>
Beta testing and progressive exposure are important strategies in DevOps to receive critical feedback in production.

* **Beta Testing** <br>
This is a form of external user acceptance testing where beta versions of an application are released to a limited audience, known as beta testers. Versions are released to groups of people for more testing, and sometimes made available to the public for more feedback.

* **Progressive Exposure**<br>
This technique entails switching small numbers of users over to a new version of software for feedback, then progressively exposing more users to the features over time.

Both techniques involve a small group of users who test new versions of an application. Rapid feedback means that you will quickly know which features are relevant and that you will have the information you need to strategize and implement ways to improve the application. Any performance issues will only affect the small number of users testing the new version. These topics are covered in more depth in the section on application performance monitoring later in this course.

## Understanding the AAA (Arrange-Act-Assert) Pattern
The **Arrange-Act-Assert (AAA) Pattern** should be followed when writing a test, to achieve the best results and fast feedback from the test. As the name suggests, it consists of three steps:

* **Arrange:** Eponymously, this step contains all the actions that help arrange the test, for example, initialization of things required later while running the test, setting up the environment, and much more.

* **Act:** This is when the test performs the desired interaction with the application, such as entering text, pushing a button, and so on.

* **Assert:** Assert is when our test asserts whether the interaction gave us the desired outcome or not, such as verifying that an error message was displayed.
