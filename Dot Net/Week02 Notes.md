# Week 2 Notes
## TDD
- What are the 5 steps of TDD?
    1. Write the test
    2. Do just enough to make the test compile
    3. Watch it fail
    4. Do just enough to make the test pass
    5. Refactor and generalize
- What makes a good test?
    1. Focused - Tests only 1 thing
    2. Easy to read - Self documenting and clear
    3. Simple - No loops or decisions, only a sequence
    4. Independent - Should stand alone and have no dependencies
    5. Flexible - Can be re-used in different projects
- Three keys of tests
    - Arrange
    - Act
    - Assert
## NUnit
- What is NUnit?
    - Testing framework for all .NET languages
    - Needs the test adapterto give the platform to run NUnit
    - A nuget package
    - Like JUnit from Java
- How do you install packages for .NET?
    - First way:
        - Open the package manager console
            - View -> Other Windows -> Package Manager Console
            - For JUnit:
                - https://www.nuget.org/packages/NUnit/4.0.0-beta.1
    - Second way:
        - Nuget Package Manager
            - Right click on class library -> Manage NuGet Packages
- How do you uninstall packages for .NET?
    - Right click class library -> manage nuget packages -> installed -> uninstall.
- What do you need for testing in .NET?
    - NUnit
    - NUnit3TestAdapter
    - Microsoft.NET.Test.SDK
- Attributes
    - Same as annotations in Java
    - Key attributes in NUnit
        - [TestFixture]
            - Marks a class that contains tests with optional setup or teardown methods
        - [Test]
            - Mark a method inside a TestFixture class as a test
        - [TestCase(12, 3, 4)]
            - Serves the dual purpose of marking a method with parameters as a test method and providing inline data to be used when invoking that method.
        - [OneTimeSetUp]    
            - Performs prior to executing any of the tests in a fixture.
        - [OneTimeTearDown]
            - Performs after executing ALL tests in a fixture.
        - [SetUp]
            - Performs before each test method is called
        - [TearDown]
            - Performs after each test method is called
- Assertions
    - NUnit Assertions
        - https://docs.nunit.org/index.html
- Running a NUnit test
    - Test -> Run All Tests