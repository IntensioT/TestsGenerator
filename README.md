**MPP FOURTH LAB. TESTS GENERATOR**

Here is implemented a multi-threaded test class boilerplate generator for one of the testing libraries (NUnit, xUnit, MSTest) for the classes under test.

**Input data**

* List of files for classes from which it is necessary to generate test classes.
* Path to the folder where the generated files will be written.
* Restrictions on conveyor sections (see below).

**Output data**
* Test class files: Each output file should have only one test class corresponding to one test class, regardless of where the test classes were located in the source files.
For example: Input.cs (with classes Foo and Bar) -> FooTests.cs, BarTests.cs.
* All generated test classes should compile when included in a separate project that has a reference to the project with the classes under test.
* All generated tests must fail.

Generation should be performed in a producer-consumer pipeline and consist of three stages:

1. parallel loading of sources into memory (with a limit on the number of files loaded at a time); 
2. generation of test classes in multi-threaded mode (with a limit on the maximum number of simultaneously processed tasks);
3. parallel writing of results to disk (with a limit on the number of simultaneously written files).
