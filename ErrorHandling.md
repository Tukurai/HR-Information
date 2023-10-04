# Error handling, Debugging, Troubleshooting & Logging

## Table of Contents  
  
1. [Introduction to Error Handling](#introduction-to-error-handling)  
2. [Understanding Error Messages](#understanding-error-messages)
3. [Common Error Types in Python](common-error-types-in-python)  
4. [Common Error Types in C#](common-error-types-in-c#)  
5. [Debugging Tools and Techniques](#debugging-tools-and-techniques)  
6. [Logging and Monitoring](#logging-and-monitoring)
7. [Error Prevention and Best Practices](#error-prevention-and-best-practices)
8. [Enterprise Solutions for Error Handling](#chapter-8)  
    - Review of enterprise-level solutions for error tracking and handling  
    - Integration of error handling into CI/CD pipeline  
    - Handling errors in distributed systems  
9. [Exercises and Solutions](#chapter-11)  
    - Practice exercises to identify and fix errors  
    - Solution walkthroughs for each exercise  
10. [Conclusion](#chapter-12)  
    - Recap of the course  
    - Further resources for learning  

## Introduction to Error Handling  
Error handling is an indispensable aspect of programming. It concerns the way your program responds when things don't go as planned.

Without proper error handling, a program may crash, produce incorrect results, or behave unpredictably. These issues can have significant consequences, especially in real-world applications.  

### Catastrophic failures in the real world
Here are three notable examples where inadequate error handling led to catastrophic failures:

1. **Therac-25 Radiation Therapy Machine**: In the mid-1980s, a medical device called the Therac-25, used for radiation therapy, was responsible for at least six incidents where patients were given radiation doses that were hundreds of times greater than intended. The cause was traced back to a race condition in the machine's software, which was not properly handled.

> In this case, inadequate error handling not only led to severe harm to patients but also resulted in a significant setback for the manufacturer, AECL, both financially and reputation-wise.  
> Source: [Wikipedia, Therac-25](https://en.wikipedia.org/wiki/Therac-25)  
 
3. **Mars Climate Orbiter**: In 1998, NASA's Mars Climate Orbiter was lost in space due to a failure to handle unit conversion errors. The navigation team used English units (pound-seconds) while the team that built the spacecraft used metric units (Newton-seconds) for a key spacecraft operation.

> This mismatch was not caught during the checking of the software, leading to the loss of the $327.6 million mission. This incident highlights the importance of communication, but also proper error handling and checks in software, especially in mission-critical applications.  
> Source: [Mars Climate Orbiter](https://en.wikipedia.org/wiki/Mars_Climate_Orbiter)
 
3. **Ariane 5 Rocket**: In 1996, the European Space Agency's Ariane 5 rocket exploded shortly after launch. A software error in the inertial reference system led to a 64-bit floating point number relating to the horizontal velocity of the rocket with respect to the platform being converted to a 16-bit signed integer. The number was larger than what could be represented by a 16-bit signed integer, leading to an overflow that the software wasn't designed to handle.

> The unhandled exception led to the onboard computer crashing, and the rocket self-destructed less than a minute after launch. The total loss was about $370 million. This incident serves as a stark reminder of the potential cost of unhandled errors in systems where reliability is paramount.  
> Source: [Wikipedia, Ariane flight V88](https://en.wikipedia.org/wiki/Ariane_flight_V88)

These examples underscore the importance of proper error handling in software systems. In Python and C#, as in many other languages, we handle errors by catching exceptions. Exceptions are events that occur during the execution of programs that disrupt the normal flow of instructions.

### Differentiating Between Compile-Time and Runtime Errors
 
Errors in programming languages like Python and C# can occur at two stages: compile-time and runtime.

**Compile-time errors**, as the name suggests, occur during the compilation of the code. In interpreted languages like Python, these are usually syntax errors that prevent the code from running. In compiled languages like C#, these could be syntax errors or type checking errors.

```C#
// An example of a C# compile-time error  
public class Program  
{  
    public static void Main()  
    {  
        int x = "Hello World"; // This will cause a compile-time error  
    }  
}  
```

**Runtime errors** occur during the execution of the program. These could be due to logical errors in the code or unexpected inputs.

```Python
# An example of a Python runtime error  
def divide(x, y):  
    return x / y  
  
print(divide(1, 0))  # This will cause a runtime error  
```
 
In the next chapter, we will dig deeper into understanding error messages and their components.

## Understanding Error Messages
Understanding error messages is a crucial skill in debugging. Error messages provide valuable insight into what went wrong during your program's execution.

### Explanation of Syntax of Error Messages
 
Error messages often have a specific structure. While the exact structure can vary between different programming languages, they generally contain similar elements.

In Python, a typical error message might look something like this:
```Python
Traceback (most recent call last):  
  File "<stdin>", line 1, in <module>  
ZeroDivisionError: division by zero  
```
In C#, an error message might be structured like this:
```C#
System.DivideByZeroException: 'Attempted to divide by zero.'  
   at Program.Main() in C:\path\to\your\file.cs:line 14  
 ```

Despite the different formats, the error messages above both provide:
- The type of error (`ZeroDivisionError` in Python, `System.DivideByZeroException` in C#)
- The location of the error (`<stdin>, line 1` in Python, `C:\path\to\your\file.cs:line 14` in C#)
- A brief description of the error (`division by zero` in Python, `Attempted to divide by zero`. in C#)

### Understanding the Components of Error Messages 
Let's break down each component:

#### Error Type
The error type helps you understand the nature of the problem. In Python, `ZeroDivisionError` is a built-in exception raised when the second argument of a division or modulo operation is zero. In C#, `System.DivideByZeroException` is thrown when you attempt to divide an integral or decimal value by zero.

#### Location of the Error
This tells you where in your code the error occurred. In Python, it's the file name and line number (e.g., `<stdin>, line 1`). In C#, it's the method that threw the exception and the file path with line number (e.g., `Program.Main() in C:\path\to\your\file.cs:line 14`).

#### Error Description
This is a human-readable description of the error. It can provide additional information about what went wrong.

Understanding how to read error messages will allow you to quickly identify and address issues in your code.

## Common Error Types in Python
In this chapter, we will delve into some of the most common error types you'll encounter when programming in Python. Understanding these errors, their causes, and how to correct them, is a crucial skill for any programmer. By the end of this chapter, you should be able to identify these common errors and know how to go about resolving them.

### SyntaxError
This is probably the most common error you will encounter, especially if you are new to Python. A `SyntaxError` is raised when the interpreter encounters syntactical issues in your code.
```python
print "Hello, world!"
```
Here, the parentheses are missing around the string. The correct code should be:
```python
print("Hello, world!")
```

### NameError
A `NameError` is raised when you try to use a variable or a function name that has not been defined.
```python
print(hello)
```
In this case, `hello` is not defined. You might want to define it first or check the spelling if you have already defined it.

### TypeError
A `TypeError` is raised when an operation or function is applied to an object of inappropriate type.
```python
"2" + 2
```
You cannot add a string to an integer. You need to convert the integer to a string first.
```python
"2" + str(2)
```

### ValueError
A `ValueError` is raised when a function's argument is of an inappropriate type, but the operation could be applied to some value of that type.
```python
int("hello")
```
In this case, you cannot convert the string "hello" to an integer. The function `int()` can only be applied to numeric strings.

### IndexError
An `IndexError` is raised when you try to access an index which is out of range in sequences like a list or a tuple.
```python
my_list = [1, 2, 3]
print(my_list[3])
```
Here, the index 3 is out of range. The maximum index for this list is 2.

Remember, understanding the type of error is the first step in debugging your code. In the next chapter, we will discuss common error types in C#.

## Common Error Types in C#
This chapter focuses on common error types that you might encounter while programming in C#. We will compare these errors with those discussed in the previous chapter on Python, giving you a comparative understanding of how different languages handle errors.

### Compilation Error
The most common errors you'll encounter in C# are compilation errors. These errors occur when the code violates the syntax rules of the C# language. This can be compared to a `SyntaxError` in Python.
```C#
int x = "hello";
```
In this case, we're trying to assign a string to an integer variable, which is a violation of the type safety rules in C#.

### NullReferenceException 
A `NullReferenceException` is thrown when you try to access a member on a type whose value is `null`. This is somewhat analogous to a `NameError` in Python, where a non-existent variable is accessed.
```
string str = null;  
Console.WriteLine(str.Length);  
```
In this example, we're trying to access the `Length` property of a `null` `string`, which will result in a `NullReferenceException`.

### InvalidCastException
An `InvalidCastException` is thrown when you attempt to cast a value to a type that it cannot be converted to. This is similar to a `TypeError` in Python, where an operation is applied to an object of inappropriate type.
```C#
object obj = "hello";  
int num = (int)obj;  
```
In this case, we're trying to cast a string object to an integer, which will raise an InvalidCastException.

### ArgumentOutOfRangeException
An `ArgumentOutOfRangeException` is thrown when the value of an argument is outside the allowable range of values as defined by the invoked method. This is comparable to a `ValueError` in Python.
```C#
List<int> numbers = new List<int> {1, 2, 3};  
Console.WriteLine(numbers[3]);  
```
Here, we're trying to access the fourth element of a `list` that only has three elements, which will raise an `ArgumentOutOfRangeException`. This is similar to an `IndexError` in Python.

Understanding these common error types in C# and their Python counterparts will help you become a more effective programmer in both languages. In the next chapter, we will dive into tools and techniques for debugging these and other errors.

## Debugging Tools and Techniques 
Debugging is an essential part of programming. Regardless of the language you use, understanding how to efficiently debug your code can save you a lot of time and effort. This chapter will introduce you to debugging tools and techniques in Python and C#, as well as some general strategies that can be applied in any language.

### Debugging in Python
Python offers several powerful tools and libraries for debugging, with the built-in `pdb` module being one of the most popular. `pdb` provides an interactive source code debugger for your Python programs, allowing you to pause your program, look at the values of variables, and watch program execution step-by-step, so you can understand what your code is actually doing and why.
```python
import pdb  
  
def add_to_list_in_dict(thedict, listname, element):  
    if listname not in thedict:  
        thedict[listname] = []  
    pdb.set_trace()  # Set a breakpoint here  
    thedict[listname].append(element)  
  
mydict = {}  
add_to_list_in_dict(mydict, 'mylist', 'myelement')  
```
 
Running this code will start the debugger right before `thedict[listname].append(element)` is executed. At the `(Pdb)` prompt, you can type commands such as `list` to show where you are in the code, or `print thedict` to display the current value of `thedict`.

### Debugging in C#
In C#, the most common debugging tool is the one built into the Visual Studio IDE. Like `pdb` in Python, the Visual Studio debugger allows you to set breakpoints in your code, step through it line by line, and inspect the values of variables at any point.
```C#
public void AddToListInDict(Dictionary<string, List<string>> thedict, string listname, string element)  
{  
    if (!thedict.ContainsKey(listname))  
    {  
        thedict[listname] = new List<string>();  
    }  
    // Set a breakpoint on the next line using the Visual Studio IDE  
    thedict[listname].Add(element);  
}  
  
Dictionary<string, List<string>> mydict = new Dictionary<string, List<string>>();  
AddToListInDict(mydict, "mylist", "myelement");  
``` 
To set a breakpoint in Visual Studio, you can simply click in the left margin next to the line of code where you want to pause execution. When you run your code in debug mode (by pressing F5), execution will pause at your breakpoints, and you can inspect the current state of your program.

### Print Statements for Debugging
One of the simplest yet most powerful debugging techniques is the use of print statements to display the values of variables at certain points in your code. This can be particularly useful when you're trying to understand the flow of execution through your program and the state of your data.
```python
def add_to_list_in_dict(thedict, listname, element):  
    if listname not in thedict:  
        thedict[listname] = []  
    print(f'The dictionary before adding the element: {thedict}')  # Debugging print statement  
    thedict[listname].append(element)  
    print(f'The dictionary after adding the element: {thedict}')  # Debugging print statement  
``` 
In this Python code, the print statements allow us to see how `thedict` changes as the function is executed.

### Understanding and Using Stack Traces
 
When an error occurs in your program, most languages will provide a stack trace, which is a record of what the program was doing when it crashed. Understanding how to read a stack trace is an essential skill for debugging. A stack trace will typically show you the line of code where the error occurred and the sequence of function calls that led to that point.

Consider the following Python code:
```python
def level_3_function():  
    raise Exception("An error occurred")  
  
def level_2_function():  
    level_3_function()  
  
def level_1_function():  
    level_2_function()  
  
level_1_function()  
 ```
Try it yourself in the [Online W3School Tryit editor](https://www.w3schools.com/python/trypython.asp?filename=demo_default), replace the basic code with the code block above.

Running this code will result in the following stack trace:
```python
Traceback (most recent call last):
  File "./prog.py", line 10, in <module>
  File "./prog.py", line 8, in level_1_function
  File "./prog.py", line 5, in level_2_function
  File "./prog.py", line 2, in level_3_function
Exception: An error occurred
```
The stack trace displays a list of the function calls that were in progress at the time of the error. This list is known as the call stack. The function where the error occurred, `level_3_function`, is at the bottom of the stack, and the sequence of calls that led to this error are displayed above it.

Understanding a stack trace can help you pinpoint not only where an error occurred, but also how and why the program got to that point. This can be incredibly valuable when trying to debug complex issues.

In the next chapter, we will discuss the importance of logging in error handling, and introduce Python and C# logging frameworks.

## Logging and Monitoring

In this chapter, we will discuss the importance of logging in error handling, introduce you to Python and C# logging frameworks, and discuss effective log management strategies.

Even with the most rigorous testing and debugging, it's virtually impossible to completely eliminate all bugs and exceptions from your code. This is due to a variety of factors. First, it's often impractical or even impossible to test every possible input, especially for large or complex programs. Second, some errors only occur under specific circumstances or in certain environments that might not be replicated in testing. Finally, human error plays a role. As humans, we're fallible and prone to making mistakes, and even the most experienced programmers aren't immune.

Given that we can't eliminate all bugs, it's crucial to have a strategy for managing them when they do occur. This is where logging and monitoring come in.

### Importance of Logging in Error Handling
Logging is the process of recording events in your code and is a crucial tool for diagnosing and understanding bugs that emerge in your software. When an error occurs, logs can provide a wealth of information about what the code was doing when the error occurred, making it easier to diagnose and fix the issue.

A crucial point to understand is that errors will not always occur during development or testing stages. Many errors only surface under specific conditions that are hard to replicate, such as high load or specific user interactions. These are known as production errors, and they can be particularly tricky to diagnose and fix.

Reproduction is often the first step in fixing a bug. If you can reliably reproduce the error, you can observe it happening, experiment with solutions, and confirm when it's been fixed. However, reproducing production errors can be challenging. The specific conditions under which the error occurs may be difficult to recreate in a testing environment.

This is where logging comes in. By providing a detailed record of events leading up to an error, logs can help you understand the conditions under which the error occurred. They can provide valuable clues that help you reproduce the error, even if it only occurs under specific conditions in production.

For example, logs might reveal that an error only occurs when a certain type of data is input, or when multiple processes access a resource simultaneously. With this information, you can set up your testing environment to match these conditions, allowing you to reproduce the error and work on a fix.

In addition, logs provide a historical record of your application. This means you can use them to track changes over time and identify when and why a particular error first started occurring. This can be invaluable in diagnosing and fixing complex issues.

In the next sections, we'll discuss logging frameworks in Python and C#, and effective log management strategies.

### Python Logging Framework
Python's built-in `logging` module provides a flexible framework for emitting log messages from Python programs.
```python
import logging  
  
logging.basicConfig(level=logging.INFO)  
logger = logging.getLogger(__name__)  
  
def divide(x, y):  
    try:  
        result = x / y  
    except ZeroDivisionError:  
        logger.error("Tried to divide by zero")  
    else:  
        return result  
  
divide(1, 0)  
``` 

### C# Logging Frameworks
In C#, there are several popular logging frameworks such as log4net and NLog. Here's an example using NLog:
```C#
using NLog;  
  
public class Example  
{  
    private static Logger logger = LogManager.GetCurrentClassLogger();  
  
    public void Divide(int x, int y)  
    {  
        try  
        {  
            int result = x / y;  
        }  
        catch (DivideByZeroException ex)  
        {  
            logger.Error(ex, "Tried to divide by zero");  
        }  
    }  
}  
  
Example example = new Example();  
example.Divide(1, 0);  
``` 

### Effective Log Management Strategies
Effective log management strategies can help you get the most out of your logs. Some best practices include:

- Using different log levels (e.g., INFO, WARNING, ERROR) to categorize your logs. This can make it easier to filter logs and focus on the ones that matter.
- Including detailed contextual information in your logs, such as the time of the event, the location in the code, and the state of relevant variables.
- Regularly reviewing and cleaning your logs. Old logs that are no longer relevant can take up space and make it harder to find important information.
- Using a log management tool. These tools can aggregate logs from different sources, provide search and filter functionality, and offer analytics and visualization.

In the next chapter, we'll discuss coding best practices to prevent errors, and delve into the concept of exception handling and its importance.

## Error Prevention and Best Practices
 In this chapter, we focus on the proactive ways to avoid errors from happening in the first place. We'll cover some coding best practices and introduce the concept of exception handling.

### Coding Best Practices to Prevent Errors
There are some general coding practices that can help prevent errors in your code. Here are a few fundamental ones:

- **Comment your code**: This helps not only you but also others who might be reading your code to understand what each part is doing. It can prevent misunderstanding that could lead to errors.
- **Use descriptive variable and function names**: This will make your code easier to read and understand, reducing the likelihood of errors.
- **Follow a coding style guide**: Consistency in your code can help prevent errors. Both Python and C# have style guides that you should follow.
- **Keep functions small and focused**: A function should do one thing and do it well. This makes it easier to test and less prone to errors.
- **Use version control systems**: They help you keep track of changes and if an error pops up, you can easily revert to an earlier version of your code. [More on that](https://github.com/Tukurai/HR-Information/blob/main/SourceControl.md).

```python
# Good Practice  
def add_numbers(num1, num2):  
    """  
    This function takes two numbers and returns their sum.  
    """  
    return num1 + num2  
  
# Bad Practice  
def do_stuff(a, b):  
    return a + b  
 ```

### Introduction to Exception Handling and Its Importance
Exceptions are events that occur during the execution of programs that disrupt the normal flow of the program's instructions. When these occur, if not handled, the program will crash. To avoid this, you can predict where the code might fail and handle the exception accordingly. This is achieved through try/except blocks in Python and try/catch blocks in C#.

```python
# Python Exception Handling  
try:  
    # code that might raise an exception  
    x = 1 / 0  
except ZeroDivisionError:  
    # code that will run if there's a ZeroDivisionError  
    x = 0  
```

```C#
// C# Exception Handling  
try  
{  
    // code that might raise an exception  
    int x = 1 / 0;  
}  
catch (DivideByZeroException)  
{  
    // code that will run if there's a DivideByZeroException  
    int x = 0;  
}
```
In both cases, instead of the program crashing, the exception is caught and the program can continue running. Exception handling is a crucial part of writing robust, resilient code.

### Defensive Programming
Defensive programming is a practice where the programmer anticipates problems with the code execution and safeguards against them. This approach helps to reduce bugs, simplify debugging, and improve system reliability.

While best coding practices aim to make code more readable, maintainable, and efficient, defensive programming specifically targets reducing bugs and errors. Best practices help you write code that is easy to understand, while defensive programming techniques make your code more robust and less prone to errors.

Here are a few techniques:
- **Input validation**: Always validate inputs before using them. If your function expects a number, check that it is a number before using it.
- **Assertions**: These are used to set up conditions that your program expects to be true. In Python, you can use the `assert` keyword; in C#, use the `Debug.Assert()` function.
- **Error handling**: We've already discussed exception handling, but error handling in general is an important part of defensive programming.
- **Code consistency**: Consistency in coding style makes your code easier to understand, and therefore easier to debug and maintain.

Below are examples of defensive programming in Python and C#:
```python
# Python Defensive Programming  
def divide_numbers(num1, num2):  
    assert num2 != 0, "Cannot divide by zero"  
    return num1 / num2  
```

```C#
// C# Defensive Programming  
public static double DivideNumbers(double num1, double num2)  
{  
    Debug.Assert(num2 != 0, "Cannot divide by zero");  
    return num1 / num2;  
}
```
You can find more information on defensive programming in this [article by Spyros Argalias](https://programmingduck.com/articles/defensive-programming).
