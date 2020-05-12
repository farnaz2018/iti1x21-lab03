# ITI 1121 - Lab 03

## Submission

Please read the [junit instructions](JUNIT.md) for help
running the tests for this lab.

Please read the [Submission Guidelines](SUBMISSION.en.md) carefully.
Errors in submitting will affect your grades.

Submit your answers to

* Utils.java
* Rational.java


## Objectives

* **Understanding** when to use "==" or "equals"
* **Manipulating** arrays and references
* Introduction to unit testing
* Further understanding of **object-oriented** programming
* Problem solving using Java
* Explain JavaDoc in your own words
* Represent your comments with the help of JavaDoc
* Produce Web pages from JavaDoc specifications

### The method **equals**

As you know, the class **Object** defines a method **[equals](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html#equals-java.lang.Object-)**.

```java
public class Object {

    // ...

    public boolean equals(Object obj) {
        return this == other;
    }

}
```

Since in Java, every class inherits from the class **Object**, every class inherits the method **boolean equals(Object obj)**. This is true for the predefined classes, such as **String** and **Integer**, but also for any class that you will define.

The method **equals** is used to compare **references** variables. Consider two references, **a** and **b**, and the designated objects.

* If you need to compare the **identity** of two objects (do **a** and **b** designate the same object?), use "**==**" (i.e. **a == b** );
* If you need to compare the **content** of two objects (is the **content** of the two objects the same?), use the method "**equals**" (i.e. **a.equals(b)**).

### Manipulating arrays - FindAndReplace

Complete the implementation of the (static) class method **String[] findAndReplace(String[] in, String[] what, String[] with)** of the class **Utils**. The method returns a <u>copy</u> of the array **in** where each word occurring in the array **what** has been replaced by the word occurring at the corresponding position in the array **with**. The array designated by **in** must remain unchanged. You can assume that there are no duplicate words in the array **what**.

Later in the semester, we will learn about exceptions. Exceptions provide tools for handling **error** situations. In the meantime, the method **findAndReplace** returns **null** whenever one of the preconditions of the methods is violated:

* In particular, the formal parameters cannot be **null**.
* For all three arrays, none of the elements can be **null**.
* The query and replacement arrays must be of the same **length**.

You will hand this **exercise in**. Download and complete the starter file here:

* Utils.java

## Using tests to validate programs

Although "testing shows the presence, not the absence of bugs"<sup><small>1</small></sup>, testing is never the less an important activity of software development.

Tests are an essential part of software development. It is therefore important for you to know how to use them. Although it is possible to manually test simple programs, as your program gets more and more complex this becomes impossible, and automated tests are needed. The basic idea of an automatic test is to create a block of code – a test – that interacts with your program by doing one to many possible scenarios where we know the logical answer that we are supposed to get, and then make sure that it matches the answer that the programs returns. There exist many tools that can be used to help you test your code such as JUnit.

Use the test class **TestFindAndReplace.java** to test your program.

* TestFindAndReplace.java

Make all the necessary changes to your method **findAndReplace** so that it passes all the tests.


## Instance variable vs class variable

The instance variables are linked to an instance of the class. Therefore, each time that we create a new instance of a class (a new object), a new copy of the instance variable is created.

The class variables (also known as static variable) are linked to the class itself. There is only one copy of these variables and it is shared between each instance of this class.

```java
public class Person {
  String firstName; //instance variable
  String lastName; //instance variable

  [...]
  static int numberOfPersons = 0 //class variable
}
```

## Private variable

A **private** variable is a variable that can only be accessed from within the class itself; they cannot be accessed by other classes. It is therefore useful to use **setters** and **getters** to be able to interact with these variables (if we need to). The use of private variables is a good programming practice. It is important to make your instance variable private in your homework and exams.

**Note**: sometimes a method parameter has the same name as an instance variable. To indicate the difference between the two, we use the keyword **this** to indicate the instance variable; this is a reference to the object where the code is being executed

```java
public class Person {
  private String firstName;       //this variable is private
  private String lastName;        //this variable is private

  [...]

  static int numberOfPersons = 0

  [...]

  //example of a getter
  public String getFirstName(){
    return firstName;             //Here we do not need to use "this"
  }

  //example of a setter
  public void setFirstName(String firstName){
    this.firstName = firstName;   //Here we need to use the keyword "this"
  }
}
```

## Constructor

A **constructor** is a special method that is called when the instance of an object is created (the constructor is not called at any other moment). This method allows you to initialize the object and the necessary instance variables. The constructor method has to have the **same name as the class** and **it does not have any return type**.

A class can provide multiple constructors that differ in the number of parameters that they take (the arity). The constructors can also be explicitly called from a different constructor, using the **this** keyword. Such a call should always be the first statement in the. See the example below.

```java
public class Person {
  private String firstName; //this variable is private
  private String lastName; //this variable is private
  private String username; //this variable is private

  [...]

  static int numberOfPersons = 0;

  [...]

  //example of a constructor with a default value
  public Person(String firstName, String lastName){
    //no code before this call
    this(firstName, lastName, firstName + "." + lastName);
    //possibly more code here
  }

  //example of a constructor
  public Person(String firstName, String lastName, String username){
    this.firstName = firstName;
    this.lastName = lastName;
    this.username = username;
  }

  //example of a getter
  public String getFirstName(){
    return firstName; //Here we do not need to use "this"
  }

  //example of a setter
  public void setFirstName(String firstName){
    this.firstName = firstName; //Here we need to use the keyword "this"
  }
}
```

## Rational

You will hand in this exercise. Download and complete the starter file here:

* Rational.java

Implement a class to represent **rational** numbers. Each rational number consists of a numerator and a denominator, both of type **int**. Since each rational number has its own numerator and denominator, these must be instance variables. Furthermore, good object-oriented programming suggests that the visibility of the variables should be **private**.

### Constructors

The class **Rational** has two constructors. One of them has two formal parameters, which provide the initial values for both instance variables. The other constructor has a single parameter, which provides the initial value for the numerator; the denominator is assumed to be 1.

#### getters

Implement access methods that return the **numerator** and **denominator** of this rational, but no setter methods. An object that has no setter methods, and no other methods for transforming the state of the object, is said to be **immutable**. Immutable is a great property. Do you see why? Discuss this with your neighbors and TA.

#### plus

Implement the instance method **plus**. The method has **a single formal parameter**, of type **Rational**. The method returns a new **Rational** object that represents the **sum** of this number and that of the parameter.

#### plus (part 2)

Implement a class method **plus**. The method has **two formal parameters**, both of type Rational. The method returns a new **Rational** object that represents the sum of the two numbers.

#### gcd

Implement a private class method for calculating the **greatest common divisor** of two integers, which are the formal parameters of the method.

#### reduce

Implement a **private** instance method called **reduce** that transforms this number into its reduced form. (ex: 18/4 -> 9/2)

#### reduce (part 2)

Make all the necessary changes so that a rational number is **always** stored in reduced form.

#### equals

Implement the instance method **public boolean equals(Rational o)** that returns true if this fraction and the one designated by 'o' represent the same fraction (content equality).

#### toString

Add a method **public String toString()** that returns a String representation of this fraction with the **numerator** followed by the symbol **"/"**, followed by the **denominator**. If the denominator is 1 then the method returns a String consisting of the numerator only.

#### compareTo

Implements the instance method **int compareTo( Rational o )**. It compares this object with the specified object for order, by computing the difference. Returns a **negative integer, zero, or a positive integer** as this object is **less than, equal to, or greater than** the specified object.


## Documentation: JavaDoc

Another important aspect of software development is the documentation. JavaDoc is a format for your Java comments, and a set of tools for producing Web pages automatically. In ITI1121, we are asking you to document your code (variables, methods, etc.) using **JavaDoc**.

The JavaDoc documentation is a series of comments using a special syntax. These comments are a description of a class or a method. They start with **"/\*\*"**, after which the following lines must start with **"\*"**, and lastly the comment block is closed using **"\*/"**. If we want to change the paragraph, we use **"<p>"**.

Once the description is done, we use the "block tags". These tags start with the symbol **"@"**. There are many tags but we will focus on these:

* **@author** : Indicates who the author of the code is.
* **@param** : Has to be followed by the name of a parameter from the class to which it is related, and then a description of that parameter.
* **@return** : It is followed by a description of what the method returns.

For more information, see the [JavaDoc](http://www.oracle.com/technetwork/articles/java/index-137868.html) documentation.

Example :

```java
/**
* this class represents a person
* <p>
* Note: Giving proper comments in your program makes it more
* user friendly and it is assumed as a high quality code.
*
* @author  Bob Smith
*/
public class Person {

   private String firstName;
   private String lastName;
   private String username;

   [...]

  /**
   * Constructor method initializing the first and last name.
   * Sets the default value for the username as "firstName.lastName".
   * @param firstName The first name of the person
   * @param lastName The last name of the person
   */
  public Person(String firstName, String lastName) {
    //no code before this call
    this(firstName, lastName, firstName + "." + lastName);
    //possibly more code here
  }

  /**
   * Constructor method initializing the first name, last name and the username.
   * @param firstName The first name of the person
   * @param lastName The last name of the person
   * @param username The preferred username of the person
   */
  public Person(String firstName, String lastName, String username) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.username = username;
  }

  /**
   *this is a getter method
   *it is used to get the value of the variable firstName
   * @return String this returns the person's first name
   */
  public String getFirstName() {
    return firstName; //Here we do not need to use "this"
  }

  /**
   *this is a setter method
   *it is used to change the value of the variable firstName
   * @param firstName The value to assign to the instance variable firstName
   */
  public void setFirstName(String firstName){
    this.firstName = firstName; //Here we need to use the keyword "this"
  }
}
```

You must add JavaDoc comments for the file Utils.java.

1. Add JavaDoc comments to the method **findAndReplace**. Each comment should include a brief description of what the method does and descriptions of the parameters and the return value using JavaDoc format.
2. Add a brief description of the class **Utils**, using the JavaDoc syntax, making sure to include the name of the author of the class (you).

You can now produce HTML files automatically, either using your favorite IDE (DrJava, Eclipse, Netbeans, etc.) or by running the javadoc command in a shell. The parameters are -d doc, followed by the name(s) of the Java file(s) to be processed

```java
> javadoc -d doc Utils.java
```

When several files need to be processed simultaneously, use * in place of the names of the files.

```java
> javadoc -d doc *
```


## Resources

* [https://docs.oracle.com/javase/tutorial/getStarted/application/index.html](https://docs.oracle.com/javase/tutorial/getStarted/application/index.html)
* [https://docs.oracle.com/javase/tutorial/getStarted/cupojava/win32.html](https://docs.oracle.com/javase/tutorial/getStarted/cupojava/win32.html)
* [https://docs.oracle.com/javase/tutorial/getStarted/cupojava/unix.html](https://docs.oracle.com/javase/tutorial/getStarted/cupojava/unix.html)
* [https://docs.oracle.com/javase/tutorial/getStarted/problems/index.html](https://docs.oracle.com/javase/tutorial/getStarted/problems/index.html)
