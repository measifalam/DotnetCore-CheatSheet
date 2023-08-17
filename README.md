


# 1. ArgumentNullException

### Guard Clause

The 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗡𝘂𝗹𝗹𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻.𝗧𝗵𝗿𝗼𝘄𝗜𝗳𝗡𝘂𝗹𝗹 method is a static method in the System namespace that throws an 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗡𝘂𝗹𝗹𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻 if the specified object is null. It is a convenient way to check for null parameters in your code. It can help to prevent runtime errors and make the code more concise.


💡 Advantages of 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗡𝘂𝗹𝗹𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻 𝗚𝘂𝗮𝗿𝗱 𝗖𝗹𝗮𝘂𝘀𝗲:

1- It is easy to use. Just pass the object you want to check for null to the method, and it will throw an exception if the object is null.

2- It reduces code size and makes it easy to read.


🔥 The ArgumentNullException Guard Clause is a more concise way of checking for null values, and it can help to prevent errors in your code.



𝗧𝗵𝗮𝗻𝗸 𝘆𝗼𝘂 𝗳𝗼𝗿 𝗿𝗲𝗮𝗱𝗶𝗻𝗴 😊

```csharp
public void Update(Student Student)
{
    if(Student is null)
    {
        throw new ArgumentNullException(nameof(Student));
    }
    StudentRepository.UpdateStudent(student);
}
```

Suggested Approach:

```csharp
public void Update(Student student)
{
    ArgumentNullException.ThrowIfNull(student);
    StudentRepository.UpdateStudent(student);
}

```

---


# 2. 𝗥𝗲𝗱𝘂𝗻𝗱𝗮𝗻𝘁 𝗰𝗮𝘀𝘁𝘀 𝘀𝗵𝗼𝘂𝗹𝗱 𝗻𝗼𝘁 𝗯𝗲 𝘂𝘀𝗲𝗱

💡 Explicit casting is not necessary in the following situations:

1- 𝗖𝗼𝗻𝘃𝗲𝗿𝘀𝗶𝗼𝗻𝘀 𝗳𝗿𝗼𝗺 𝗱𝗲𝗿𝗶𝘃𝗲𝗱 𝗰𝗹𝗮𝘀𝘀𝗲𝘀 𝘁𝗼 𝗯𝗮𝘀𝗲 𝗰𝗹𝗮𝘀𝘀𝗲𝘀: You can assign an instance of a derived class to a variable of its base class type without casting.

2- 𝗖𝗼𝗻𝘃𝗲𝗿𝘀𝗶𝗼𝗻𝘀 𝗳𝗿𝗼𝗺 𝘀𝗺𝗮𝗹𝗹𝗲𝗿 𝘁𝗼 𝗹𝗮𝗿𝗴𝗲𝗿 𝗶𝗻𝘁𝗲𝗴𝗿𝗮𝗹 𝘁𝘆𝗽𝗲𝘀: Implicit conversions are allowed from smaller to larger integral types without needing an explicit cast.


🔥 These conversions can be done implicitly without requiring explicit casting. However, be mindful of other scenarios where explicit casting might still be necessary, particularly when dealing with potentially unsafe conversions or types that don't have a direct inheritance relationship.


𝗧𝗵𝗮𝗻𝗸 𝘆𝗼𝘂 𝗳𝗼𝗿 𝗿𝗲𝗮𝗱𝗶𝗻𝗴 😊

Redundant casts should not be used:

```csharp
class Person {}
class Employee: Person {}
class Program 
{
    static void Main()
    {
        Employee employee = new Employee();
        Person person = (Person) employee; // THis is the Redundant cast
    }
}

```
should be

```csharp
class Person {}
class Employee: Person {}
class Program 
{
    static void Main()
    {
        Employee employee = new Employee();
        Person person = employee;
    }
}

```
---

# Use Task.WhenAll();
## How to execute tasks in parallel?
## How to be sure all the tasks are finished?


Task.WhenAll is a static method used when you want to do some operation with multiple tasks in parallel and wait until all of them have been completed.

It returns a single task that finishes only when all of the tasks you've passed to it have been completed.

It's useful when you have multiple independent tasks that can run in parallel, and you need to do something after they're all done.

If any of the tasks you pass to Task.WhenAll throws an exception, Task.WhenAll will also throw an exception.

This exception will be an AggregateException, which is a type of exception that can hold multiple inner exceptions. Each inner exception corresponds to one of the exceptions thrown by the tasks.

```csharp
public async Task CallAPIs()
{
 await CallApiOne();
 await CallApiTwo();
 await CallApiThree();
}
```
better way

```csharp
public async Task CallAPIs()
{
  await Task.WhenAll
  (
     CallApiOne(),
     CallApiTwo(),
     CallApiThree()
  );
}
```
---

# 𝗨𝘀𝗲 𝘀𝘁𝗿𝗶𝗻𝗴.𝗘𝗾𝘂𝗮𝗹𝘀 𝗶𝗻𝘀𝘁𝗲𝗮𝗱 𝗼𝗳 𝗧𝗼𝗨𝗽𝗽𝗲𝗿()/𝗧𝗼𝗟𝗼𝘄𝗲𝗿() 𝘄𝗵𝗲𝗻 𝗰𝗼𝗺𝗽𝗮𝗿𝗶𝗻𝗴 𝘀𝘁𝗿𝗶𝗻𝗴𝘀

🐌 Using 𝗧𝗼𝗨𝗽𝗽𝗲𝗿() and 𝗧𝗼𝗟𝗼𝘄𝗲𝗿() for case conversion in C# can impact performance due to memory allocation, string copying, and potential garbage collection, especially in situations involving large strings or frequent conversions.

🚀 𝗦𝘁𝗿𝗶𝗻𝗴.𝗘𝗾𝘂𝗮𝗹𝘀 is faster than ToUpper() or ToLower() due to direct character comparison, avoiding memory allocation, and reducing overhead for case-insensitive string comparison.

🔥 To perform string comparison, it's better to use built-in comparison methods like 𝗦𝘁𝗿𝗶𝗻𝗴.𝗘𝗾𝘂𝗮𝗹𝘀 with appropriate StringComparison options, which handle case-insensitivity and cultural considerations correctly while maintaining better performance and accuracy.

```csharp

public bool AreStringsEqual(string firstString, string secondString)
{
  return (firstString.ToUpper() == secondString.ToUpper())
}
```
optimized ways

```csharp
public bool AreStringsEqual(string firstString, string secondString)
{
  return string.Equals(firstString, secondString, StringComparison.OrdinalIgnoreCase);
}

```

---
# How I split the collection into smaller collections with the LINQ method 💡
Dealing with large collections in your application is often done with LINQ:

→ Skip
→ Take

The first one takes the number of elements that it needs to skip, and the second element to take from it.

And there is nothing wrong with this approach, there is a simpler way.

Introduces in .NET 6, Chunk will split the collection into groups of smaller ones with several elements provided.

If the number of remaining elements in the main collection is lower than provided, a new collection will be created with the rest from the main.

You can occur to two types of exceptions:

→ 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗡𝘂𝗹𝗹𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻 if the collection is null
→ 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗢𝘂𝘁𝗢𝗳𝗥𝗮𝗻𝗴𝗲𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻 if the provided number of elements is below 1

```charp
var chunckedUsers1 = users.skip(2).Take(2);
var chunckedUsers2 = users.Chunk(5);
```




