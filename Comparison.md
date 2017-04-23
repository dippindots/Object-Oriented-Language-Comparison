# Object Oriented language comparison
1. String comparisons: How are Strings values compared?
2. Null object references: What is the keyword for a null/nil/etc object reference?
3. Name of instance reference in instance method: What is the keyword for referring to an object instance in an instance method? (this/self/?)
4. Name spaces: How are name spaces implemented and used?
5. **Errors and exception handling: How are errors and/or exceptions handled/structured/implemented?**

   An Exception can be anything which interrupts program processing. When an exception occurs, the normal flow of the program gets terminated and doesn’t continue any further. In such cases we will get a system generated error message. Fortunately, most of time, exceptions can be handled.
   
* ### Java
  
  #### Exception Definition
  There are three categories of Exceptions in Java. 
  * **Checked exceptions**
    
    A checked exception is an exception that occurs at the compile time, these are also called as **compile time exceptions**. These exceptions cannot simply be ignored at the time of compilation, the programmer should take care of (handle) these exceptions.
    
    For example, if we would like to use the _FileReader_ class to read a character file. The _FileReader_ constructor definition in the Java api is as following:
    ```Java
    public FileReader(String fileName)
      throws FileNotFoundException
    ```
    
    So we would write following code to read the file
    ```Java
        public static void main(String[] args){
        FileReader fileInput = null;
        fileInput = new FileReader("test.txt");
    }
    ```
    
    Syntactically the statements are correct but this code will never compile. The compiler knows the _FileReader_ constructor can throw a _FileNotFoundException_ and it's up to the calling code to handle this exception. There are two ways to handle this exception. First of all, we could use the same _throws_ clause:
    ```Java
     public static void main(String[] args) throws FileNotFoundException{
        FileReader fileInput = null;
        fileInput = new FileReader("test.txt");
    }
    ```
    
    Or we could handle with the exception:
    ```Java
        public static void main(String[] args){
        FileReader fileInput = null;
        try
        {
           fileInput = new FileReader("Untitled.txt");
        }
        catch(FileNotFoundException ex)
        {
            //tell the user to go and find the file
        }
    }
    ```
    In conclusion, all exceptions that the compiler checks them during compilation to see whether the programmer has handled them or not. If these exceptions are not handled/declared in the program, it will give compilation error, such as _ClassNotFoundException_, _IllegalAccessException_, _NoSuchFieldException_, _EOFException_ etc.
    
  * **Unchecked exceptions**
    
    An unchecked exception is an exception that occurs at the time of execution. These are also called as **Runtime Exceptions**. These include programming bugs, such as logic errors or improper use of an API. Runtime exceptions are ignored at the time of compilation.
    
    You've written the code, it all looks good to the compiler and when you go to run the code it falls over because it tried to access an element of an array that does not exist or a logic error caused a method to be called with a null value. For example, if you have declared an array of size 5 in your program, and trying to call the 6th element of the array then an _ArrayIndexOutOfBoundsExceptionexception_ occurs.
    ```Java
    public class Unchecked_Exceptions {
    
       public static void main(String args[]) {
         int num[] = {1, 2, 3, 4};
         System.out.println(num[5]);
       }
    }
    ```
    In conclusion, These exceptions need not be included in any method’s throws list because compiler does not check to see if a method handles or throws these exceptions, but it’s the duty of the programmer to handle these exceptions and provide a safe exit, such as _ArithmeticException_, _ArrayIndexOutOfBoundsException_, _NullPointerException_, _NegativeArraySizeException_ etc.


  * **Errors**
  
    When an exception occurs the JVM will create an exception object. These objects all derive from the _Throwable_ class. The _Throwable_ class has two main subclasses -- _Error_ and _Exception_. The _Error_ class denotes an exception that an application is not likely to be able to deal with. 
    
    Errors are typically ignored in your code because you can rarely do anything about an error. For example, if a stack overflow occurs, an error will arise. It's possible for the application to catch the error to notify the user but typically the application is going to have to close until the underlying problem is dealt with.
    
    Error defines problems that are not expected to be caught under normal circumstances by our program, such as memory error, hardware error, JVM error etc.
  
  #### Catching Exceptions
  A method catches an exception using a combination of the **try** and **catch** keywords. A try/catch block is placed around the code that might generate an exception. 
  
  * **Single catch blocks**
  
    Code within one try/catch block is referred to as protected code, as following:
    ```Java
    try {
      // Protected code
    }catch(ExceptionName e1) {
      // Catch block
    }
    ```
    If an exception occurs in protected code then the control of execution is passed to the catch block from try block. The exception is caught up by the corresponding catch block. A single try block can have multiple catch statements associated with it, but each catch block can be defined for only one exception class. The program can also contain nested try-catch-finally blocks.
    
    After the execution of all the try blocks, the code inside the finally block executes. It is not mandatory to include a finally block at all, but if you do, it will run regardless of whether an exception was thrown and handled by the try and catch blocks.
    
    A catch block must be associated with a try block. The corresponding catch block executes if an exception of a particular type occurs within the try block. Every try block should be immediately followed either by a catch block or finally block.
    
    For example, the following is an array declared with 2 elements. Then the code tries to access the 3rd element of the array which throws an exception:
    ```Java
    import java.io.*;
    public class ExcepTest {

       public static void main(String args[]) {
          try {
             int a[] = new int[2];
             System.out.println("Access element three :" + a[3]);
          }catch(ArrayIndexOutOfBoundsException e) {
             System.out.println("Exception thrown  :" + e);
          }
          System.out.println("Out of the block");
       }
    }
    ```
    and the output is as following:
    ```Java
    Exception thrown  :java.lang.ArrayIndexOutOfBoundsException: 3
    Out of the block
    ```
    
  * **Multiple catch blocks**
  
    A try block can be followed by multiple catch blocks, as following:
    ```Java
    try {
      // Protected code
    }catch(ExceptionType1 e1) {
      // Catch block
    }catch(ExceptionType2 e2) {
      // Catch block
    }catch(ExceptionType3 e3) {
      // Catch block
    }
    ```
    If an exception occurs in the protected code, the exception is thrown to the first catch block in the list. If the data type of the exception thrown matches ExceptionType1, it gets caught there. If not, the exception passes down to the second catch statement. This continues until the exception either is caught or falls through all catches, in which case the current method stops execution and the exception is thrown down to the previous method on the call stack.
    
    The order of those multiple exception blocks should be from specific to generic.
    ```Java
    class Example2{
       public static void main(String args[]){
         try{
            int a[]=new int[7];
            a[4]=30/0;
            System.out.println("First print statement in try block");
         }
         catch(ArithmeticException e){
           System.out.println("Warning: ArithmeticException");
         }
         catch(ArrayIndexOutOfBoundsException e){
           System.out.println("Warning: ArrayIndexOutOfBoundsException");
         }
         catch(Exception e){
           System.out.println("Warning: Some Other exception");
         }
       System.out.println("Out of try-catch block...");
       }
    }
    ```
   
   
  * **The final block**
  
    The finally block follows a try block or a catch block. A Using a finally block allows you to run any cleanup-type statements that you want to execute, no matter what happens in the protected code. A finally block appears at the end of the catch blocks, as following:
    ```Java
    try {
      // Protected code
    }catch(ExceptionType1 e1) {
      // Catch block
    }finally {
      // The finally block always executes.
    }
    ```
    The finally block of code always executes, irrespective of occurrence of an Exception.
    ```Java
    class JavaFinally
    {
       public static void main(String args[])
       {
         System.out.println(JavaFinally.myMethod());  
       }
       public static int myMethod()
       {
         try {
           return 112;
         }
         finally {
           System.out.println("This is Finally block");
           System.out.println("Finally block ran even after return statement");
         }
       }
     }
     ```
    
  #### User-defined Exceptions
  * **Create your own exceptions**
  
    We need to extend the predefined Exception class to create our own Exception. These are considered to be checked exceptions. We can define our own Exception class as below:
    ```Java
    class MyException extends Exception {
    }
    ```
    For example:
    ```Java
    class MyException extends Exception{
       String str1;
       MyException(String str2) {
          str1=str2;
       }
       public String toString(){ 
          return ("Output String = "+str1) ;
       }
     }
     ```
     In order to throw user defined exceptions, throw keyword is being used. In this tutorial, we will see how to create a new exception and throw it in a program using throw keyword.
    
  * **The Throws/Throw Keywords**
  
    If a method does not handle a checked exception, the method must declare it using the _throws_ keyword. The _throws_ keyword appears at the end of a method's signature. You can throw an exception, either a newly instantiated one or an exception that you just caught, by using the _throw_ keyword. The _throws_ keyword is used to postpone the handling of a checked exception and the _throw_ keyword is used to invoke an exception explicitly.
  

  


6. **Memory management and garbage collection: How is memory management and garbage collection handled?**
7. Interfaces/protocols/?: How do interfaces/protocols/etc work?
8. Functional features: What functional features are supported and how do they work? (lambdas, closures, etc)
9. Reflection: What reflection abilities are supported?
10. **Procedural programming support: Can functions be created outside of classes or must all functions be methods of a class?**
11. Singleton: How to implement a thread-safe singleton.
12. Unique features: Describe any unique features of the language.


