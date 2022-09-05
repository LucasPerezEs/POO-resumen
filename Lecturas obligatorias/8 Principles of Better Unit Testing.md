# 8 Principles of Better Unit Testing

>***Unit tests***: *Unit tests are short, quick, and automated tests that make sure a specific part of your program works*.

### What makes a good unit test? 

A "good" unit test follows these rules:
- The test only fails when a new bug is introduced into the system or requirements change.
- When the test fails, it is easy to understand the reason for the failure.  

**To write good unit tests**, the developer that writes the tests needs to **follow these guidelines**:

### Guideline #1: Know what you're testing
A test written without a clear objective in mind is easy to spot. This type of test is long, hard to understand, and usually tests more than one thing.  
One trick is to **use the scenario tested and expected result as part of the test method name**, when a simple test fails, it is **easier to find the cause and fix it**.

### Guideline #2: Unit tests should be self-sufficient
A single test **should not depend on running other tests before it, nor should it be affected by the order of execution** of other tests. 

### Guideline #3: Tests should be deterministic
**A test should either pass all the time or fail until fixed**.  
Another “practice” that must be avoided is writing tests with random input. Using randomized data in a unit test introduces uncertainty.

### Guideline #4: Naming conventions
When a well-named test fails, it is easier to understand what was tested and why it failed.

### Guideline #5: Do repeat yourself
**Readability is very important in unit testing, so it is acceptable to have duplicate code**. Avoiding duplication in tests creates tests that are difficult to read and understand.

### Guideline #6: Test results, not implementation
There are a few rules that help avoid writing **fragile unit tests**. **These are tests that would fail due to an internal change** in the software that does not affect the user.  The problem is that implementation tends to change and the test will fail even if the result is the same.  
**Another issue arises when testing internal/private methods and objects**. They are not meant to be "seen" outside of the class and are part of the internal mechanics of the class. Only test private methods if you have a very good reason to do so. 

### Guideline #7: Avoid overspecification
It is tempting to create a well-defined, controlled, and strict test that observes the exact process flow during the test by setting every single object and testing every single aspect being tested. The problem is that this "locks" the scenario under test, preventing it from changing in ways that do not affect the result.  
**For example, try to avoid writing a test that expects a certain method to be called exactly three times**. 

### Guideline #8: Use an Isolation framework
**Writing good unit tests can be hard when the class under test has internal or external dependencies**, you may need a connection to a fully populated database or a remote server. When such dependencies need a complex setup for the automated test to run, the result is fragile tests that break, even if the code under test works perfectly.  
A mocking framework (or Isolation framework) is a third-party library and a huge time saver. **Instead of creating our fake objects by hand, we can use the framework to create them with only a few API calls**. 
