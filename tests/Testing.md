# Software Testing
 - A testing framework is a set of tools used for automating the testing process of an application.
   - A testing framework typically includes libraries, tools, and guidelines enabling developers or automation Quality Assurance engineers to write, structure, and execute tests. 
   - Test frameworks also provide reporting tools that generate test results, thus making it easier to identify bugs.

## QA, QC, and QE: What's the Difference?
### Quality Assurance
 - Defines the testing process such as smoke and regression test, but doesn't do actual testing.
   - **Smoke testing**, also called build verification testing or confidence testing, is a software testing method that is used to determine if a new software build is ready for the next testing phase. This testing method determines if the most crucial functions of a program work but does not delve into finer details.
   - **Regression Testing** is a type of testing in the software development cycle that runs after every change to ensure that the change introduces no unintended breaks.

### Quality Control
 - Does the actual testing performed on the software such as executing test runners and reporting defects

### Quality Engineer
 - Quality Control that involves implementing and developing testing software.
 - Interchangeable with with Quality Control

## Testing Methods
![Types of Testing](https://d2i2xyh28mr8fx.cloudfront.net/wp-content/uploads/2023/04/18113310/TYPES-OF-TESTING.png)

### Unit testing
 - Unit testing checks individual units of code (functions or methods) in isolation from the rest of the application. It catches errors early and ensures changes to the code do not introduce new bugs or disrupt existing functionality.
### Integration testing
 - Integration testing checks how multiple units of code work when combined. It defines possible conflicts between application components (modules or subsystems) and ensures their coherent functioning.
### Functional testing (E2E)
 - Functional or end-to-end testing focuses on testing the overall app functionality. In this case, developers simulate real-world scenarios using special JS test tools and check whether the application operates as intended.

## Testing Tool Types
 - **Test runners** automate the execution of test cases and provide feedback on results. They can also generate reports and perform debugging. Popular test runners include Karma, Jest, Jasmine, and Cypress.
 - **Assertion libraries** help to ensure the code operates as expected. They are often used in unit testing and allow for time savings as they contain ready functions. Jasmine, Jest, and Cypress frameworks come with assertions included.
 - **Mocking tools** allow for the creation of fake objects and simulation of different scenarios. This enables quicker and safer integration and functional testing. Popular frameworks with mocking include Jest, Nightwatch, and Playwright.
 - **Browser test tools** automate JavaScript browser testing. They allow the simulation of user interactions such as clicking buttons and scrolling. Popular browser frameworks include Puppeteer, Cypress, and WebdriverIO.
 - **Test reporting tools** generate data on which automated tests pass or fail and streamline error detection. Most JavaScript test frameworks such as Mocha, Jasmine, Cypress, and Playwright include these tools.
 - **Test coverage tools** measure how much of the code was tested. This helps to find untested code and reduces the risk of undetected bugs. Frameworks like Jest, Cypress, and Storybook provide coverage reports by default.
 - **Visual regression tools** allow developers to obtain screenshots of the application’s UI before and after changes. This helps detect unintended changes and ensure UI consistency. Popular frameworks providing this feature are Puppeteer, Storybook, and Playwright.

### Top JavaScript Testing Frameworks
Name        | Advantages        | Abilities
----        | --------------        | ---------
[Jest](https://jestjs.io/)        | React-Based           | Unit, Integration, E2E
[Storybook](https://storybook.js.org/)   | UI Components         | UI
[Mocha](https://mochajs.org/)&[Chai](https://www.chaijs.com/)       | Well-Documented       | TDD, BDD
[Cypress](https://www.cypress.io/)     | Mocha+                | E2E, Cross-Browser, Headless, API, Functional, Perfomance, Component, Accessibility, Visual
[Vitest](https://vitest.dev/api/mock.html)        | Jest-Compatible           | Unit, Integration, E2E
[Jasmine](https://jasmine.github.io/)     | Open-Source, BDD      | BDD
[Cucumber](https://cucumber.io/docs/installation/javascript/)    | Open-Source, BDD      | BDD
[Playwright](https://playwright.dev/)  | C#/Typescript         | E2E, Cross-Browser, Headless, API, Functional
[Puppeteer](https://pptr.dev/)   | High-Level Library    | E2E, Headless Browser
[Nightwatch](https://nightwatchjs.org/)  | Selenium sever        | E2E, Visual
[Selenium](https://www.selenium.dev/)    | Browser-based         | E2E, Cross-Browser, Headless, API, Functional, UI, Database


![Mocha & Chai](https://miro.medium.com/v2/resize:fit:1200/0*gV7fEaDKRGwpprdj.png)

## [Test Patterns](https://mobilelive.medium.com/tdd-vs-bdd-vs-ddd-which-one-should-you-choose-e562e313f955#:~:text=TDD%20vs%20BDD%20vs%20DDD%3A%20Key%20Differences&text=Here%20are%20the%20key%20differences,uses%20a%20domain%2Dspecific%20language.)
### Test Driven Development (TDD)
 - TDD is an agile software development process where developers write automated tests before writing the code.
   - The idea behind TDD is that if you write the tests first, you will have a better understanding of what the code should do.
   -  The tests act as a specification for the code. TDD ensures that the code is testable, maintainable, and extensible.
   -  The steps involved in TDD are:
      -  Write a *fail*ing test
      -  Write the code to make the test *pass*
      -  *Refactor* the code to improve its quality

### Behavior Driven Development (BDD)
- BDD is a software development process that focuses on the behavior of the software.
  - BDD is an extension of TDD, where tests are written in a more natural language that stakeholders can understand.
  - BDD ensures that the software is developed based on the user’s needs and behaviors.
    - The steps involved in BDD:
      - Define the behavior of the software
      - Write tests that describe the behavior
      - Write code to make the tests pass
      - Refactor the code to improve its quality

### Domain-Driven Design (DDD)
 - DDD is an approach to software development that focuses on the domain of the software.
   - The domain is the problem space that the software is intended to solve.
   - DDD ensures that the software is built around the domain and that it solves the problem in the best possible way.
   - The steps involved in DDD:
     - Understand the domain of the software
     - Define the domain model
     - Implement the domain model in code
     - Continuously refine the domain model

## Quality Control Tools
> "As much as 95% of quality problems can be solved with seven fundamental tools" - Kaoru Ishikawa
### Flow Charts
> "If you can't describe what you're doing as a process you don't know what you're doing!" -W. Edwards Deming
 - A visual tool that depicts the flow or sequence of a process.

![Flow Chart](https://miro.com/blog/wp-content/uploads/2023/09/Blog_How-to-make-a-flow-chart-process_.png)

### Check Sheets
 - The check sheet is a simple tool for collecting, organizing and analyzing data such as defects that we can then triage.
 - Additionally, check sheet collect metadata about our data e.g. who, when, where.

![Check Sheet](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Check_sheet_for_motor_assembly.svg/1200px-Check_sheet_for_motor_assembly.svg.png)

### Pareto Charts
> "Wow I just discovered the 80/20 rule! - Vilfredo Pareto probably"
 - The Pareto Chart is a bar chart that allows for analysis of data in search of the Pareto Principle or the 80/20 rule.

![Jordan Peterson](https://hips.hearstapps.com/hmg-prod/images/longform-lead-credit-jake-stangel-1525106191.jpg?crop=1xw:1xh;center,top&resize=1200:*)

### Cause & Effect Diagrams
 - The cause and effect diagram is a visual tool to explore all the potential factors that may be causing or contributions to a particular problem (effect).
![Fishbone Diagram](https://slidemodel.com/wp-content/uploads/03-fishbone-diagram-key-components-slide-design.png)

### Histograms
 - A histogram is a type pf Bar Chart that graphs the frequency of occurrence of continuous data and is a useful tool for displaying, summarizing, and analyzing data.
   - Every process has some level of variation that will occur in a pattern.
   - The best way to see this pattern of variation is to graph your data using a histogram.

![Distribution Graphs](https://api.www.labxchange.org/api/v1/xblocks/lb:LabXchange:10d3270e:html:1/storage/17__histogram-31626365193365-3b46e339f410f97cfae66fc8c127ea02.png)

### Scatter Diagrams
 - A scatter diagram is visual tools that show the possible relationship between two variables.

![Scatter Graph](https://www.internetgeography.net/wp-content/uploads/2020/09/Types-of-scatter-graph.png)

### Control Charts
 - Statistical Process Control is a collection of statistical tools (control charts) that allow you to ensure that your process is in control (stable).
   - We can use control charts to determine `special cause varitions` which are variations that were not observed previously and are unusual, non-quantifiable variations.

![Control Chart](https://pmri.in/wp-content/uploads/2020/10/control-chart-example-pmri.jpg)

## Resources

Video | Author | Duration
----- | ------ | --------
[Cypress End-to-End Testing](https://www.youtube.com/watch?v=7N63cMKosIE) | Fireship | (00:09:33)
[Test-Driven Development](https://www.youtube.com/watch?v=Jv2uxzhPFl4) | Fireship | (00:12:54)
[Test-Driven Development](https://www.youtube.com/watch?v=EH9Suo_J4Ks) | Jack Herrington | (00:19:34)
[Intro to BDD](https://www.youtube.com/watch?v=u5cLK1UrFyQ&list=WL&index=108&t=147s) | Travery Media | (02:31:55)
[Stop Writing So Many Tests](https://www.youtube.com/watch?v=4-_0aTlkqK0) | Web Dev Simplified | (00:10:01)