| [How JUnit works](#How%20Junit%20works)
| [Core annotations](#Core%20annotations)
|--- [Test methods](#Test%20methods)
|--- [Life cycle methods](#Life%20cycle%20methods)
|--- [Display name](#Display%20name)
| [Assertion](#assertion)


# How JUnit works

JUnit creates an instance of the class containing tests before invoking each of the test methods.This ensures the independence of each of the test methods.
Note that tests must produce the same results independent of the order in which they are executed in

# Core annotations

## Test methods

A test method is generally annotated with *@Test* or it's related annotations.

```
@Test
public void testAdd() {
	Calculator calculator = new Calculator();
	double result = calculator.add(10, 50);
	assertEquals(60, result, 0);
}
```

Above we have a test method which is meant to test the add operation from calculator service by adding 10 with 50. The result is then checked by the static assertEquals method which is covered at [assertion](#assertion).

Test methods are methods that are annotated with one of below:
- @Test
- @ReapetedTest
- @ParameterizedTest
- @TestFactory
- @TestTemplate

Test methods must not be abstract and the return type must be void.

## Life cycle methods

Life cycle methods are methods meant to run before or after any all instances of test methods inside of a test class instance.
These methods are genedrally annotated with one of below:
- @BeforeEach
- @BeforeAll
- @AfterEach
- @AfterAll

## Display name

*@DisplayName* can be used to annotate test classes and methods. This annotation takes a parameter as *value* which will be the name of the respective test instance(methods/class).
```
@Log4j2  
@DisplayName(value = "test calculator operations")  
public class CalculatorTests {  
  
    @Test  
    @DisplayName("test addition of zeros")  
    @Disabled  
    public void testAdditionOfZeros() {  
        log.info("\ntesting addition of 0 + 0");  
        int result = calculatorService.add(0,0);  
        assertEquals(0, result, 5);  
    }  
} 
```

The code above will result in the following 

![[Pasted image 20230914161132.png]]

## Disabled

*@Disabled* is used to disable the execution of a test instance. It takes a parameter as *value* which is meant to represent the reason this test instance is disabled.                    

A class annotated with this annotation would have all it's test methods stopped from execution.

# Assertion