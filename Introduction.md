There are some fundamental classes in Reflection API:
 - the class Class
 - the class Method
 - the class Field
 - the class Constructor
 - the class Annotation (This was added later in the API)
 
# The class Class
We can't create an instance of this class. Then how to get a reference to this class instance?
- Query an already existing object of the class
- We can get a class by it's name, known at compile time
- We can get a class by it's name, known at run time

```java
String hello = "Hello";
Class helloClass = hello.getClass();
```
The getClass method is defined in the Object class.


```java
String hello = "Hello";
Class helloClass = hello.getClass();

String world = "World";
Class worldClass = world.getClass();

helloClass == worldClass // returns true
```
There is only one instance of class for a given class. Above are two references on the same class object. Java loads the class only once and at any point of time you have only one instance of the class available.

```java
Class<?> getClass() // Signature of get class function
```

```java
Class<?> helloClass = "Hello".getClass(); // Works fine
Class<String> helloClass = "Hello".getClass(); // Compile time error 
Class<Object> helloClass = "Hello".getClass(); // Compile time error 
```
This happens because generics in java works in this way. Class<String> and Class<Object> are not extension of Class<?> in java. to achieve this we use Class<? extends String> or Class<? extends Object>


## Getting the super class of a given class
getSuperClass() returns the only super class
The super class of Object class is Null.
getInterfaces() returns the array of interfaces implemented

## Getting the declared and the non-declared fields of the class
The `declared` elements in the class are the elements declared inside the class
- private
- protected
- public
with no inherited elements.

The `non-declared` elements of a class are the elements declared in this class and all the super class, but only the public ones

```java
class Person {
 private int age;
 private String name;
 
 // getters and setters
}
```

```java
Person.class.getFields(); // gives an empty array because fields are private
Person.class.getDeclaredFields(); // gives the array of Fields[] 
```

Similarly getMethods(), getConstructors() and getDeclaredMethods() function exist for method.
getDeclaredConstructors() donot return constructors of the super class which is a difference with it's counter functions for fields and methods.
