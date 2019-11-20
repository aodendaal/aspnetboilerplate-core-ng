# Unit Testing

## Guidelines
The AAA (Arrange, Act, Assert) pattern is a common way of writing unit tests for a method under test.

* The **Arrange** section of a unit test method initializes objects and sets the value of the data that is passed to the method under test.
* The **Act** section invokes the method under test with the arranged parameters.
* The **Assert** section verifies that the action of the method under test behaves as expected.

Taken from https://docs.microsoft.com/en-us/visualstudio/test/unit-test-basics?view=vs-2019

If you are finding you need to test a lot of private behavior, most likely you have a new 'class' hiding within the class you are trying to test, extract it and test it by its public interface.

Taken from https://stackoverflow.com/questions/9122708/unit-testing-private-methods-in-c-sharp
