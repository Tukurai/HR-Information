# Regular Expressions

## Table of Contents

1.  Introduction to Regular Expressions
2.  Using Regular Expressions in Python and C#
3.  Advanced Topics in Regular Expressions
4.  Conclusion
5.  Exercises and Solutions
6.  Appendix

## Chapter 1: Introduction to Regular Expressions  
   
### 1.1 Definition and Purpose of Regular Expressions  
A regular expression, often abbreviated as "regex" or "regexp", is a sequence of characters that forms a search pattern. This search pattern can be used to match, locate, and manage text. They are a powerful and flexible tool used in many aspects of programming, including text processing, data validation, and string manipulation.  
Regular expressions are utilized in a wide range of programming languages, including Python and C#, and they play a crucial role in modern programming tasks such as text searching, data extraction, data validation, and string operations.  
The primary purpose of regular expressions is to provide a concise and flexible means to "match" (specify and recognize) strings of text, such as particular characters, words, or patterns of characters.  

### 1.2 Basic Terminology in Regular Expressions  
   
- **Pattern**: A pattern is a sequence of characters that you specify for the regular expression engine to match within the input text. For example, the pattern `\d` can match any digit.  
- **Metacharacters**: Metacharacters are special characters that have unique meanings. Examples of metacharacters include `.` (dot), `*` (asterisk), `+` (plus), `?` (question mark), `{}` (curly braces), `[]` (square brackets), `()` (parentheses), `^` (caret), `$` (dollar), `|` (pipe), `\` (backslash).  
- **Literal**: A literal is a character that matches itself. For example, the pattern `a` will match the character 'a' in the input text.  
- **Escape Sequences**: Escape sequences are used to specify special characters like metacharacters. For example, to match a literal dot, you can use the escape sequence `\.`.  
- **Quantifiers**: Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to occur. Examples of quantifiers include `*` (0 or more), `+` (1 or more), `?` (0 or 1), `{n}` (exactly n), `{n,}` (n or more), `{n,m}` (between n and m).  
- **Character Classes**: Character classes are a set of characters enclosed in square brackets `[]`. They are used to match any single character within the brackets. For example, the pattern `[abc]` will match any of the characters 'a', 'b', or 'c'.  
- **Grouping**: Parentheses `()` are used for grouping in regular expressions. The grouped characters are treated as a single unit and can be quantified.  
- **Alternation**: The pipe symbol `|` is used for alternation (similar to boolean OR). It matches the pattern before or the pattern after it. For example, the pattern `a|b` will match either 'a' or 'b'.  
- **Anchors**: Anchors are used to specify the position of the pattern in relation to a line of text. The caret `^` matches the position at the start of the text, and the dollar sign `$` matches the position at the end of the text.  

In the next chapter, we will explore how to use regular expressions in Python and C#, including the relevant modules and functions.

## Chapter 2: Using Regular Expressions in Python and C#  
   
### 2.1 Introduction to the 're' Module in Python  
   
The 're' module in Python provides support for regular expressions. This module contains several functions that use regular expressions to perform operations on strings. Before using any function in this module, you need to import it into your python script with the following line of code:  
   
```python  
import re  
```  
   
Here are some of the most commonly used functions in the 're' module:  
- **re.match(pattern, string)**: This function attempts to match the pattern at the start of the string. If the match is found, it returns a match object; otherwise, it returns None.  
- **re.search(pattern, string)**: This function searches the string for a match to the pattern. It returns a match object if the pattern is found; otherwise, it returns None.  
- **re.findall(pattern, string)**: This function returns all non-overlapping matches of the pattern in the string as a list of strings.  
- **re.split(pattern, string, maxsplit=0)**: This function splits the string by the occurrences of the pattern. The 'maxsplit' parameter is optional and specifies the maximum number of splits.  
- **re.sub(pattern, repl, string, count=0)**: This function replaces all occurrences of the pattern in the string with 'repl'. The 'count' parameter is optional and specifies the maximum number of replacements.  
   
Here is an example of using the 're' module to find all words in a string:  
   
```python  
import re  
   
text = 'Python is a great programming language.'  
pattern = '\w+'  
words = re.findall(pattern, text)  
   
print(words)  # Output: ['Python', 'is', 'a', 'great', 'programming', 'language']  
```  
   
In this example, the pattern `\w+` matches one or more word characters (equivalent to `[a-zA-Z0-9_]`). The `re.findall()` function finds all words in the string and returns them as a list.  
   
In the next section, we will introduce the 'System.Text.RegularExpressions' namespace in C# and explore its regex functions.

### 2.2 Introduction to the 'System.Text.RegularExpressions' Namespace in C#  
   
In C#, regular expressions are included in the 'System.Text.RegularExpressions' namespace. It provides a powerful class called 'Regex' which is used to create and work with regular expressions.  
   
To use the 'Regex' class in a program, you need to include the namespace using the following line of code:  
   
```csharp  
using System.Text.RegularExpressions;  
```  
   
The most commonly used methods in the 'Regex' class are:  
   
- **Regex.IsMatch(input, pattern)**: This method determines if the regular expression finds a match in the input string.  
   
- **Regex.Match(input, pattern)**: This method searches the input string for the first occurrence of the regular expression specified in the pattern parameter.  
   
- **Regex.Matches(input, pattern)**: This method searches the input string for all occurrences of a regular expression and returns all the successful matches.  
   
- **Regex.Replace(input, pattern, replacement)**: This method replaces all strings that match a regular expression pattern with a specified replacement string.  
   
### 2.3 RegEx Functions in Python and C#: findall, search, split, sub, IsMatch, Match, Matches, Replace  
   
As we have seen in the previous sections, Python and C# both provide functions for matching regular expressions, searching for patterns, replacing matched substrings, and splitting strings based on pattern matches.  
   
In Python, these are primarily achieved through the functions in the 're' module: `re.findall()`, `re.search()`, `re.split()`, and `re.sub()`.  
   
In C#, the equivalent functionality is provided through the methods of the 'Regex' class in the 'System.Text.RegularExpressions' namespace: `Regex.IsMatch()`, `Regex.Match()`, `Regex.Matches()`, and `Regex.Replace()`.  
   
Although the names and usage of these functions/methods differ somewhat between Python and C#, they essentially achieve the same objectives in their respective languages.  
   
### 2.4 RegEx Metacharacters in Python and C#  
   
Metacharacters are special characters that have a unique meaning for regular expressions. Both Python and C# recognize the following metacharacters:  
   
- `.`: Matches any character except newline (`\n`).  
- `^`: Matches the start of the string.  
- `$`: Matches the end of the string.  
- `*`: Matches 0 or more repetitions of the preceding regex.  
- `+`: Matches 1 or more repetitions of the preceding regex.  
- `?`: Matches 0 or 1 repetitions of the preceding regex.  
- `{m,n}`: Matches at least `m` and at most `n` repetitions of the preceding regex.  
- `\`: Used to escape special characters or denote special sequences.  
- `[]`: Used to define a character set.  
- `|`: Acts as a boolean OR, matches the pattern before or the pattern after it.  
- `()`: Defines a group.  
- `#`: A comment. The rest of the line is ignored.  
   
In the next sections, we will explore how to use these metacharacters in more detail, along with special sequences and predefined character classes, to create more complex and powerful regular expressions in both Python and C#.

### 2.5 RegEx Special Sequences and Predefined Character Classes in Python and C#  
   
Special sequences and predefined character classes make regular expressions more versatile and easier to read. Both Python and C# support a similar set of special sequences:  
   
- `\d`: Matches any decimal digit; equivalent to the set `[0-9]`.  
- `\D`: Matches any non-digit character; equivalent to the set `[^0-9]`.  
- `\s`: Matches any whitespace character; equivalent to `[ \t\n\r\f\v]`.  
- `\S`: Matches any non-whitespace character; equivalent to `[^ \t\n\r\f\v]`.  
- `\w`: Matches any alphanumeric character; equivalent to `[a-zA-Z0-9_]`.  
- `\W`: Matches any non-alphanumeric character; equivalent to `[^a-zA-Z0-9_]`.  
   
### 2.6 RegEx Sets in Python and Match Object in C#  
   
In Python, a set is a set of characters inside a pair of square brackets `[]` with a special meaning. Sets are used when you want to match any one of a group of characters at a point in the input. Brackets are used to construct character set inputs. For example, `[abc]` will match 'a', 'b', or 'c'.  
   
In C#, a Match object is the result of a regular expression search in a string. It contains all the information about the search and the result. A Match object is immutable and has no public constructor.  
   
### 2.7 Practical Examples of Regular Expressions in Python and C#  
   
To illustrate the use of regular expressions, let's look at a couple of practical examples in both Python and C#.  
   
**Python Example: Extracting Email Addresses**  
   
```python  
import re  
   
text = "Contact us at contact@company.com and sales@company.com"  
pattern = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'  
   
emails = re.findall(pattern, text)  
   
print(emails)  # Output: ['contact@company.com', 'sales@company.com']  
```  
   
**C# Example: Validating Phone Numbers**  
   
```csharp  
using System;  
using System.Text.RegularExpressions;  
   
public class Example  
{  
    public static void Main()  
    {  
        string pattern = @"^\(?\d{3}\)?-? *\d{3}-? *-?\d{4}$";  
        string[] inputs = { "(123) 456-7890", "123-456-7890", "123.456.7890", "1234567890" };  
          
        foreach (var input in inputs)  
        {  
            if (Regex.IsMatch(input, pattern))  
            {  
                Console.WriteLine($"{input} is a valid phone number.");  
            }  
            else  
            {  
                Console.WriteLine($"{input} is not a valid phone number.");  
            }  
        }  
    }  
}  
```  
   
In the next chapter, we will dive into more advanced topics in regular expressions, including performance considerations, debugging techniques, common pitfalls, and best practices.

## Chapter 3: Advanced Topics in Regular Expressions  
   
### 3.1 Regular Expression Performance in Python and C#  
Regular expressions can be a powerful tool, but they can also lead to performance issues if not used correctly. The performance of a regex largely depends on its complexity and the size of the input text.  
In Python, using the `re.compile()` function to compile a regex into a pattern object can improve performance when the regex will be used several times. The compiled pattern can be reused, saving the cost of compiling the regex each time it's used.  
In C#, the static `Regex` methods (like `Regex.Match()`, `Regex.Matches()`, and `Regex.Replace()`) automatically cache the regular expressions they use, improving the performance of repeated calls with the same regex.  
Using simpler regex patterns, limiting backtracking, and reducing the use of quantifiers can also improve regex performance in both languages.  
   
### 3.2 Debugging Regular Expressions  
Debugging regular expressions can be challenging due to their compact and abstract syntax. Here are some tips for debugging regex:  
   
- **Test iteratively**: Start with a simple version of your regex and test it against your input. Gradually add complexity and test each change.  
- **Use online regex testers**: Online tools such as regex101.com allow you to test your regular expressions against sample inputs and provide explanations of your regex.  
- **Use verbose mode**: In Python, the `re.VERBOSE` flag allows you to write regular expressions that are more readable by allowing you to add whitespace and comments.  
- **Log matches**: When testing your regex, print or log the matches it finds. This can help you see what is being matched and why.     
- **Understand common errors**: Understanding common regex errors, such as excessive backtracking or misuse of quantifiers, can help you debug issues.  
   
### 3.3 Common Regular Expression Pitfalls  
Regular expressions can be tricky to work with. Here are some common pitfalls to be aware of:  

- **Greedy vs lazy matching**: By default, quantifiers in regex are greedy, meaning they match as much as possible. This can lead to unexpected results. To make a quantifier lazy and match as little as possible, you can follow it with a `?`.  
- **Special characters**: Special characters like `.`, `*`, `+`, and `?` have special meaning in regex and must be escaped with a backslash (`\`) to be treated as literals.  
- **Complexity**: Regular expressions can become very complex and hard to understand. It's often better to use multiple simpler regexes instead of one complex one.  
- **Overuse**: Regular expressions are a powerful tool but they aren't always the best solution. If a string method or a parsing library can solve your problem, it might be a better choice.  
   
### 3.4 Regular Expression Best Practices  
Here are some best practices for working with regular expressions:  
   
- **Keep it simple**: A simple, understandable regex is usually better than a complex one. Don't sacrifice readability for a slight performance gain.  
- **Comment your regex**: Regular expressions can be hard to understand. Adding comments explaining what your regex does can be very helpful.  
- **Avoid excessive backtracking**: Backtracking can cause performance issues. Try to structure your regex to minimize backtracking.  
- **Use tools**: Online regex testers and debuggers can be very helpful for testing and understanding your regex.  
   
In the next chapter, we'll wrap up our discussion on regular expressions and provide additional resources for further learning.

## Chapter 4: Conclusion  
   
### 4.1 Recap of Regular Expressions in Python and C#     
We have covered a lot of ground in this training on regular expressions. We started with the basics of what regular expressions are and their purpose, and then we dove into how to use them in Python and C#. We explored different functions and methods available in both languages for working with regular expressions, such as `findall`, `search`, `split`, `sub` in Python and `IsMatch`, `Match`, `Matches`, `Replace` in C#.  
We also discussed special sequences, predefined character classes, and sets which can be used to create more complex patterns. We worked through some practical examples to illustrate how regular expressions can be used in real-world scenarios.  
In the advanced topics, we talked about performance considerations, debugging techniques, common pitfalls, and best practices when using regular expressions.  
   
### 4.2 Further Reading and Resources  
If you want to dive deeper into regular expressions, there are many resources available:  
   
- Python's official documentation on the 're' module: https://docs.python.org/3/library/re.html  
- Microsoft's documentation on the 'System.Text.RegularExpressions' namespace: https://docs.microsoft.com/en-us/dotnet/api/system.text.regularexpressions.regex  
- Online regex testers like https://regex101.com/ or https://www.regexpal.com/ can be very helpful for testing and debugging regular expressions.  
- Books like "Mastering Regular Expressions" by Jeffrey E.F. Friedl provide a deep dive into the subject.  
   
Remember, regular expressions are a powerful tool but they can be complex. Don't be discouraged if you don't understand everything right away. With practice, you will get more comfortable with them.  
   
In the next section, we provide some exercises for you to practice what you've learned. Try to solve them on your own, but don't hesitate to look at the solutions if you're stuck. The most important thing is to learn and improve. Happy coding!

## Chapter 5: Exercises and Solutions  
After learning about regular expressions, it's time to put your knowledge into practice. Here are some exercises that will help you do just that.  
   
### 5.1 Exercise: Email Validation  
Write a regular expression in both Python and C# that can be used to validate email addresses. The regular expression should match any email address following the standard format (example@example.com).  
   
### 5.2 Exercise: Phone Number Validation  
Write a regular expression in both Python and C# that can be used to validate phone numbers. The regular expression should match any 10-digit phone number regardless of its format (e.g., 1234567890, 123-456-7890, (123) 456-7890, etc.).  
   
### 5.3 Exercise: Web Scraping with Regular Expressions  
Write a script in Python using regular expressions to scrape a webpage and extract all URLs from it. Use the 'requests' and 're' modules for this task.  
   
## 5.4 Solutions  

### Solution to 5.1  
   
**Python:**  
   
```python  
import re  
   
email = "example@example.com"  
pattern = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'  
   
if re.match(pattern, email):  
    print("Valid email address")  
else:  
    print("Invalid email address")  
```  
   
**C#:**  
   
```csharp  
using System;  
using System.Text.RegularExpressions;  
   
public class Example  
{  
    public static void Main()  
    {  
        string pattern = @"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$";  
        string email = "example@example.com";  
          
        if (Regex.IsMatch(email, pattern))  
        {  
            Console.WriteLine("Valid email address");  
        }  
        else  
        {  
            Console.WriteLine("Invalid email address");  
        }  
    }  
}  
```  
   
### Solution to 5.2  
   
**Python:**  
   
```python  
import re  
   
phone = "123-456-7890"  
pattern = r'^\(?[\d]{3}\)?[\s-]?[\d]{3}[\s-]?[\d]{4}$'  
   
if re.match(pattern, phone):  
    print("Valid phone number")  
else:  
    print("Invalid phone number")  
```  
   
**C#:**  
   
```csharp  
using System;  
using System.Text.RegularExpressions;  
   
public class Example  
{  
    public static void Main()  
    {  
        string pattern = @"^\(?\d{3}\)?-? *\d{3}-? *-?\d{4}$";  
        string phone = "123-456-7890";  
          
        if (Regex.IsMatch(phone, pattern))  
        {  
            Console.WriteLine("Valid phone number");  
        }  
        else  
        {  
            Console.WriteLine("Invalid phone number");  
        }  
    }  
}  
```  
   
### Solution to 5.3  
   
**Python:**  
   
```python  
import re  
import requests  
   
response = requests.get("https://www.example.com")  
   
urls = re.findall('http[s]?://(?:[a-zA-Z]|[0-9]|[$-_@.&+]|[!*\\(\\),]|(?:%[0-9a-fA-F][0-9a-fA-F]))+', response.text)  
   
print(urls)  
```  
   
In the next chapter, we'll provide additional resources for further learning.

## Chapter 6: Appendix  
This appendix provides additional documentation and resources that can be helpful when working with regular expressions in Python and C#.  
   
### A.1 Python 're' Module Full Documentation  
The official Python documentation provides a comprehensive overview of the 're' module, including descriptions of all the functions, special characters, and sequences you can use in regular expressions.  
   
https://docs.python.org/3/library/re.html  
   
### A.2 C# 'System.Text.RegularExpressions' Namespace Full Documentation  
The Microsoft documentation provides a detailed look at the 'System.Text.RegularExpressions' namespace, including descriptions of the 'Regex' class and all its methods.  
   
https://docs.microsoft.com/en-us/dotnet/api/system.text.regularexpressions.regex  
   
### A.3 RegEx Cheat Sheet for Python and C#  
A cheat sheet can be a handy reference when working with regular expressions. Here are a few that might be helpful:  
   
- Python RegEx Cheat Sheet: https://www.debuggex.com/cheatsheet/regex/python  
   
Remember, the best way to learn regular expressions is through practice. Use these resources to further your understanding and become more proficient in using regular expressions in Python and C#.
