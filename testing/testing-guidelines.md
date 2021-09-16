# Testing guidelines

Try to write tests first. You don't need to practice TDD, but if you write a test first it will make it easier for yourself to write the correct code.

## **red, green, refactor** 

Always start a test with red \(**failing test**\). If your test is green from the beginning you might not catch potential bugs. Always make sure the **tests fail first**, even if you wrote the correct code already. Use a different assumption then, to make sure the test fails and you see the actual output. After the test is **green**, try to **refactor** your code \(make it better\).

Don't write your test assertions by using the output of a failing test. You should know the output \(assertion\) before the test runner tells you the failure.

## What to test

The ideal set of tests tends to result in ...

* small but right number of unit tests.
* large number of integration tests. 
* small number of E2E tests as kind off smoke tests. 

### **Always test edge cases.** 

Do not only test the obvious path but also the not so obvious. Use parameterized tests in pytest for that.

Test business logic, don't test libraries. We assume library code is tested by the developers of those libraries. If not the integration and e2e tests will catch those. **Business logic**: All code that is unique, that provides value to the codebase. That drives the app. CRUD is not business logic. State management is usally not business logic.

### Unit tests

We want to test code in isolation. It is ok to mock most of the side effects. Although side affects are a smell and should be investigated. If you find yourself mocking a lot of parts or have a hard time writing a test: This is a signal, refactor your code!

Side effects are things like database updates or sending messages.

### Integration Tests

Integration tests test at least two parts of a unit. It is ok to mock certain boundaries but be precise and document what these boundaries are. Integration tests don't test the UI. Either use an unit test or an E2E test for that.

Typical boundaries:

* API calls
* User Interface
* Third party services

