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
    
  * **Unchecked exceptions**
    
    An unchecked exception is an exception that occurs at the time of execution. These are also called as **Runtime Exceptions**. These include programming bugs, such as logic errors or improper use of an API. Runtime exceptions are ignored at the time of compilation.
    You've written the code, it all looks good to the compiler and when you go to run the code it falls over because it tried to access an element of an array that does not exist or a logic error caused a method to be called with a null value. For example, if you have declared an array of size 5 in your program, and trying to call the 6th element of the array then an _ArrayIndexOutOfBoundsExceptionexception_ occurs.
    ```Java
    public class Unchecked_Demo {
   
       public static void main(String args[]) {
         int num[] = {1, 2, 3, 4};
         System.out.println(num[5]);
       }
    }
   ```
   
  * **Errors**
  
    When an exception occurs the JVM will create an exception object. These objects all derive from the _Throwable_ class. The _Throwable_ class has two main subclasses -- _Error_ and _Exception_. The _Error_ class denotes an exception that an application is not likely to be able to deal with. 
    Errors are typically ignored in your code because you can rarely do anything about an error. For example, if a stack overflow occurs, an error will arise. It's possible for the application to catch the error to notify the user but typically the application is going to have to close until the underlying problem is dealt with.
  
  #### Exception Definition




6. **Memory management and garbage collection: How is memory management and garbage collection handled?**
7. Interfaces/protocols/?: How do interfaces/protocols/etc work?
8. Functional features: What functional features are supported and how do they work? (lambdas, closures, etc)
9. Reflection: What reflection abilities are supported?
10. **Procedural programming support: Can functions be created outside of classes or must all functions be methods of a class?**
11. Singleton: How to implement a thread-safe singleton.
12. Unique features: Describe any unique features of the language.


