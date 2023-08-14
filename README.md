


# ArgumentNullException
============================================================================================
### Guard Clause

The 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗡𝘂𝗹𝗹𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻.𝗧𝗵𝗿𝗼𝘄𝗜𝗳𝗡𝘂𝗹𝗹 method is a static method in the System namespace that throws an 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗡𝘂𝗹𝗹𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻 if the specified object is null. It is a convenient way to check for null parameters in your code. It can help to prevent runtime errors and make the code more concise.


💡 Advantages of 𝗔𝗿𝗴𝘂𝗺𝗲𝗻𝘁𝗡𝘂𝗹𝗹𝗘𝘅𝗰𝗲𝗽𝘁𝗶𝗼𝗻 𝗚𝘂𝗮𝗿𝗱 𝗖𝗹𝗮𝘂𝘀𝗲:

1- It is easy to use. Just pass the object you want to check for null to the method, and it will throw an exception if the object is null.

2- It reduces code size and makes it easy to read.


🔥 The ArgumentNullException Guard Clause is a more concise way of checking for null values, and it can help to prevent errors in your code.



𝗧𝗵𝗮𝗻𝗸 𝘆𝗼𝘂 𝗳𝗼𝗿 𝗿𝗲𝗮𝗱𝗶𝗻𝗴 😊

```
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

```
public void Update(Student student)
{
    ArgumentNullException.ThrowIfNull(student);
    StudentRepository.UpdateStudent(student);
}

```

============================================================================================


# 𝗥𝗲𝗱𝘂𝗻𝗱𝗮𝗻𝘁 𝗰𝗮𝘀𝘁𝘀 𝘀𝗵𝗼𝘂𝗹𝗱 𝗻𝗼𝘁 𝗯𝗲 𝘂𝘀𝗲𝗱

💡 Explicit casting is not necessary in the following situations:

1- 𝗖𝗼𝗻𝘃𝗲𝗿𝘀𝗶𝗼𝗻𝘀 𝗳𝗿𝗼𝗺 𝗱𝗲𝗿𝗶𝘃𝗲𝗱 𝗰𝗹𝗮𝘀𝘀𝗲𝘀 𝘁𝗼 𝗯𝗮𝘀𝗲 𝗰𝗹𝗮𝘀𝘀𝗲𝘀: You can assign an instance of a derived class to a variable of its base class type without casting.

2- 𝗖𝗼𝗻𝘃𝗲𝗿𝘀𝗶𝗼𝗻𝘀 𝗳𝗿𝗼𝗺 𝘀𝗺𝗮𝗹𝗹𝗲𝗿 𝘁𝗼 𝗹𝗮𝗿𝗴𝗲𝗿 𝗶𝗻𝘁𝗲𝗴𝗿𝗮𝗹 𝘁𝘆𝗽𝗲𝘀: Implicit conversions are allowed from smaller to larger integral types without needing an explicit cast.


🔥 These conversions can be done implicitly without requiring explicit casting. However, be mindful of other scenarios where explicit casting might still be necessary, particularly when dealing with potentially unsafe conversions or types that don't have a direct inheritance relationship.


𝗧𝗵𝗮𝗻𝗸 𝘆𝗼𝘂 𝗳𝗼𝗿 𝗿𝗲𝗮𝗱𝗶𝗻𝗴 😊

Redundant casts should not be used:

```
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

```
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
