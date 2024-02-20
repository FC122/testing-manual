# Software Testing Manual

## Goal
The goal of this Software Testing Manual is to provide a comprehensive overview of software testing principles, methodologies, and best practices. It aims to equip developers, testers, and stakeholders with the necessary knowledge and strategies to ensure the quality, reliability, and robustness of software products.

## Objectives
1. Understanding Testing Fundamentals: To familiarize readers with the fundamental concepts of software testing, including its importance, objectives, and principles.

2. Exploring Testing Techniques: To explore various testing techniques such as black-box testing, white-box testing, integration testing, and regression testing, among others, along with their respective advantages and limitations.

3. Implementing Test Automation: To discuss the significance of test automation and provide insights into selecting appropriate tools and frameworks for automating testing processes.

4. Ensuring Test Coverage: To emphasize the importance of comprehensive test coverage and provide strategies for effectively designing test cases to validate software functionalities and requirements.

5. Managing Test Data and Environments: To address challenges related to test data management and environment setup, and to offer strategies for creating realistic test environments and managing test data effectively.

6. Performing Performance and Security Testing: To highlight the significance of performance and security testing in ensuring the reliability, scalability, and security of software applications, and to discuss best practices for conducting such tests.

7. Evaluating Testing Metrics and Reporting: To introduce key testing metrics and reporting mechanisms for assessing test effectiveness, identifying defects, and communicating testing progress and results to stakeholders.

8. Continuous Improvement and Adaptation: To promote a culture of continuous improvement by emphasizing the importance of feedback, collaboration, and adaptation in the software testing process.

## Scope
This Software Testing Manual covers a wide range of topics related to software testing, including but not limited to manual testing, automated testing, performance testing, security testing, and test management. It caters to individuals involved in software development, quality assurance, and testing roles, as well as stakeholders interested in understanding the testing process and its implications for software quality and reliability.

## Contribution
Contributions to this manual, including suggestions, corrections, and additional content, are highly encouraged. Please feel free to submit pull requests or raise issues to improve the quality and relevance of this resource for the benefit of the software testing community.

## Writing Test Cases
### Test case writing - best practice
- Make it simple, KISS - Write test cases as simple as possible while giving the most information. They should be clear and concise.
- Write it from the perspective of an end user - Put yourself in the shoes of an end user and write test cases as such. If there are multiple different users/stakeholders write test cases that cover those situations as well.
- Don't repeat it, DRY - If two test cases do the same thing in a similar manner consider if it truly makes sense to have both.
- Do not assume - Do not assume functionality and features of your software application while preparing test cases. Follow the requirements document.
- Ensure 100% Coverage - Make sure that your tests cover all requirements present in the documentation
- Implement testing techniques - It is hard to perfectly analyze a feature, that's why it is a good practice to rely on existing testing techniques such as boundary value analysis and equivalence partitioning.
- Peer review - After creating test cases, let your colleagues review them. Your peers come with a different frame of mind and may fill in the blanks you accidentally left. No one is perfect.
- Don’t just cover happy paths -It is important to cover as many cases as possible. Think about all the wrongs that can happen and that user can do. Cover as many negative cases as possible.
- Verify - Write test cases to verify user requirements. Verification in context of software testing means that product should follow the requirements
- Validate - Write test cases to validate user needs. Validation in the context of software testing means that the product should do what the user needs from it. The product should be useful.

### Test case types
There are multiple test case types. We usually separate them in positive and negative test cases which is good enough. But it is good to be aware of different types while writing test cases. That way you can have a more structured approach to test case writing.

- Happy paths 
Basic positive tests. The most basic type. These test cases cover the core of functionality that is being tested.
Example:
Check that user can create a project

- Positive + optional parameters
These test cases cover the core functionality with optional parameters if there are any.
Example:
Check that user can create a project marked with red collar

- Negative - invalid input
These test cases cover actions that should not succeed with invalid inputs. Refers to validation tests.
Example:
Check that user can't create a project with name longer that 300 characters

- Negative - valid input
These test cases cover actions that should not succeed with valid inputs. Different from validations test such that the tests pass validation set on the input but can't finish the inferred action
Example:
Check that user can’t create two projects with the same name

#### Test case formula
Formula:
Check + {the thing you're checking}  + {action (optional if implicit)} + {where you're checking it (optional if implicit)} + {expected result (optional if implicit)}

- {the thing you're checking}:
  - user login
  - some element
  - response

- {action (optional if implicit)}:
  - get/post/put/delete 

- {where you're checking it (optional if implicit)}:
  - login page
  - dashboard
  - settings page

- {expected result (optional if implicit)}:
  - request is sent
  - validation message is shown
  - response status is 200

#### Examples:
Check user login with valid data

Check element visibility on dashboard page

Check response when get users request is sent

Check response when get users request is sent with empty parameters

Check validation message for minimum number of characters on Name input filed

Check that request is sent after clicking Create button

Check if user receives a notification after creating an entity

Check that response status is 200 on get users request

### Test Case Writing Metodologies

#### Combinatorial Test Design (CTD)
This is a systematic method to generate test cases where different combinations of input values are used. Tools like PICT (Pairwise Independent Combinatorial Testing) are often used to generate combinations.
- Generates test cases using combinations of inputs.
- Reduces the number of tests by focusing on variable combinations.
- Ensures interactions of input variables are tested.
- Useful when there are multiple inputs with many possible values.
- Often uses tools like PICT for generating combinations.
- Good read: https://embeddedcomputing.com/technology/debug-and-test/the-importance-of-combinatorial-test-design

#### Equivalence Class Partitioning (ECP)
This technique divides input data of a software unit into partitions of equivalent data from which test cases can be derived.
- Divides input data into equivalent classes.
- Reduces tests by assuming that all members of a class behave similarly.
- Tests are derived from each class, usually one test per class.
- Helps identify classes of valid and invalid inputs.
- Ensures coverage without exhaustive testing.
- Good read: https://www.geeksforgeeks.org/equivalence-partitioning-method/

#### Boundary Value Analysis (BVA)
This is closely related to ECP and focuses on values at boundaries of these partitions.
- Focuses on testing the edge or boundary values.
- Derived from equivalence class partitioning.
- Assumes bugs are likely at the boundaries of input domains.
- Commonly tests the values just inside and outside boundaries.
- Complements ECP by catching edge case bugs.
- Good read: https://www.geeksforgeeks.org/software-testing-boundary-value-analysis/?ref=rbp

#### Decision Tables
These tables help in understanding how different combinations of inputs produce different outputs. It's especially helpful when there are multiple inputs that can vary.
- Represents combinations of inputs to determine outputs.
- Useful when logic involves multiple conditions.
- Each row in the table represents a unique combination.
- Ensures that all possible combinations are considered.
- Makes complex decision logic easier to understand.
- Good read: https://www.guru99.com/decision-table-testing.html

#### State Transition Testing
If the software system can be represented as a finite number of states and transitions between those states based on certain inputs/events, this method is applicable. It ensures coverage of all states and transitions.
- Models software as a system of states and transitions.
- Tests are derived from state changes based on inputs/events.
- Ensures that all states and transitions are tested.
- Useful for systems with predictable state sequences.
- Often represented using state transition diagrams.
- Good read: https://www.guru99.com/state-transition-testing.html

#### Use Case Testing
This approach derives test cases from use cases. Each use case provides a sequence of events, and the derived test cases ensure coverage of these sequences.
- Derives test cases from system use cases.
- Each use case represents a sequence of events or actions.
- Focuses on user's perspective and how they interact with the system.
- Ensures all user interactions are tested.
- Can reveal gaps in functionality or user experience.
- Good read: https://www.guru99.com/use-case-testing.html

#### Path Testing
This method is about ensuring every possible route through a given piece of software is executed.
- Ensures all paths through the software are tested.
- Derived from the software's control flow graph.
- Identifies all possible routes a user can take through the software.
- Can be complex for large systems due to numerous paths.
- Ensures code robustness by testing all execution paths.
- Good read: https://www.guru99.com/basis-path-testing.html

#### Error Guessing
Error Guessing relies on the tester's skill and experience rather than a formalized approach. While it might sound informal, it can be very effective in catching defects that structured testing might miss. Combining error guessing with other testing methods can provide more comprehensive test coverage
- It's a testing technique based on the tester's experience.
- Testers use their intuition and knowledge to guess where defects might occur.
- Not systematic, but complements formal testing techniques.
- Often used to identify high-risk areas or common mistakes in code.
- It's valuable because it leverages the expertise of seasoned testers who can predict potential issues based on past experiences.
- Good read: https://www.geeksforgeeks.org/error-guessing-in-software-testing/?ref=lbp
