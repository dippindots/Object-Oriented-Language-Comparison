# Object Oriented language comparison
1. String comparisons: How are Strings values compared?

    ### Java
    We can compare string in java on the basis of content and reference.It is used in authentication (by equals() method), sorting (by compareTo() method), reference matching (by == operator)

    There are three ways to compare string in java:

    * By equals() method
    * By = = operator
    * By compareTo() method

    #### 1) String compare by equals() method
    The String equals() method compares the original content of the string. It compares values of string for equality. String class provides two methods:
     * public boolean equals(Object another) compares this string to the specified object.
     * public boolean equalsIgnoreCase(String another) compares this String to another string, ignoring case.

    ```Java
      class Stringequals
      {  
        public static void main(String args[])
        {  
         String s1="Hello";  
         String s2="Hello";  
         String s3=new String("Hello");  
         String s4="Hella";  
         System.out.println(s1.equals(s2));//true  
         System.out.println(s1.equals(s3));//true  
         System.out.println(s1.equals(s4));//false  
       }  
      }  
    ```

    ```Java
      class StringequalsIgnorecase
      {  
        public static void main(String args[])
        {  
         String s1="Hello";  
         String s2="hello";  
         System.out.println(s1.equals(s2));//false  
         System.out.println(s1.equalsIgnoreCase(s2));//true
       }  
      }  
    ```  

    #### 2) String compare by == operator
    The = = operator compares references not values.
    ```Java
        class Stringequalequal
        {  
          public static void main(String args[])
          {  
            String s1="Hello";  
            String s2="Hello";  
            String s3=new String("Hello");  
            System.out.println(s1==s2);//true (because both refer to same instance)  
            System.out.println(s1==s3);//false(because s3 refers to instance created in nonpool)  
         }  
        }  
    ```     

    #### 3) String compare by compareTo() method
    The String compareTo() method compares values lexicographically and returns an integer value that describes if first string is less than, equal to or greater than second string.

    Suppose s1 and s2 are two string variables. If:

     * s1 == s2 :0
     * s1 > s2   :positive value
     * s1 < s2   :negative value

    ```Java
        class StringCompareto
        {  
          public static void main(String args[])
          {  
            String s1="Hello";  
            String s2="Hello";  
            String s3="H";  
            System.out.println(s1.compareTo(s2));//0  
            System.out.println(s1.compareTo(s3));//1(because s1>s3)  
            System.out.println(s3.compareTo(s1));//-1(because s3 < s1 )
         }  
        }  
    ```   

    ### Python
      There are three ways to compare string content in Python.

      * By cmp() method
      * By == operator
      * By is method

      #### 1)String compare by cmp() method
      The return value is:
      * A negative number if x is less than y.
      * Zero if x is equal to y.
      * A positive number if x is greater than y.

      The built-in cmp() function will typically return only the values -1, 0, or 1. However, there are other places that expect functions with the same calling sequence, and those functions may return other values. It is best to observe only the sign of the result.

      ```python
      In [1]: cmp('aabbccdd','aabbccde')
      Out[1]: -1
      ```   

      #### 2)String compare by == method    
      **==** is for value equality. Use it when you would like to know if two objects have the same value.
      ```python
      string1 = "what's this"
      string2 = "it's a string"

      if string1 == string2:
          print("equal")
      else:
          print("not equal")
      ```       

      #### 3)String compare by is== method    
      **is** is for reference equality. Use it when you would like to know if two references refer to the same object.
      ```python
      string1 = "what's this"
      string2 = "what's this"

      if string1 is string2:
          print("same object")
      else:
          print("not same")
      ```    

2. Null object references: What is the keyword for a null/nil/etc object reference?

    ### Java
    Null is a special value used in Java. It is mainly used to indicate that no value is assigned to a reference variable. One application of null is in implementing data structures like linked list and tree. Other applications include Null Object pattern  and Singleton pattern. The Singleton pattern ensures that only one instance of a class is created and also, aims for providing a global point of access to the object.

    A sample way to create at most one instance of a class is to declare all its constructors as private and then, create a public method that returns the unique instance of the class:
      ```Java
          // To use randomUUID function.
          import java.util.UUID;
          import java.io.*;

          class Singleton
          {
          // Initializing values of single and ID to null.
          private static Singleton single = null;
          private String ID = null;

          private Singleton()
          {
              /* Make it private, in order to prevent the
                 creation of new instances of the Singleton
                 class. */

              // Create a random ID
              ID = UUID.randomUUID().toString();
          }

          public static Singleton getInstance()
          {
              if (single == null)
                  single = new Singleton();
              return single;
          }

          public String getID()
          {
              return this.ID;
          }
          }

          // Driver Code
          public class TestSingleton
          {
          public static void main(String[] args)
          {
              Singleton s = Singleton.getInstance();
              System.out.println(s.getID());
          }
          }
      ```
      Output:
      ```Java
      10099197-8c2d-4638-9371-e88c820a9af2
      ```

      In above example, a static instance of the singleton class. That instance is initialized at most once inside the Singleton getInstance method.

      ### handling the NullPointerException
      To avoid the NullPointerException, we must ensure that all the objects are initialized properly, before you use them. When we declare a reference variable, we must verify that object is not null, before we request a method or a field from the objects. Following are the common problems with the solution to overcome that problem.

      #### 1)String comparison with literals
      A very common case problem involves the comparison between a String variable and a literal. The literal may be a String or an element of an Enum. Instead of invoking the method from the null object, consider invoking it from the literal.
      ```Java
        // A Java program to demonstrate that invoking a method
        // on null causes NullPointerException
        import java.io.*;

        class GFG
        {
            public static void main (String[] args)
            {
                // Initializing String variable with null value
                String ptr = null;

                // Checking if ptr.equals null or works fine.
                try
                {
                    // This line of code throws NullPointerException
                    // because ptr is null
                    if (ptr.equals("gfg"))
                        System.out.print("Same");
                    else
                        System.out.print("Not Same");
                }
                catch(NullPointerException e)
                {
                    System.out.print("NullPointerException Caught");
                }
            }
        }
      ```
      Output:
      ```Java
      NullPointerException Caught
      ```      
      We can avoid NullPointerException by calling equals on literal rather than object.
      ```Java
      // A Java program to demonstrate that we can avoid
      // NullPointerException
      import java.io.*;

      class GFG
      {
          public static void main (String[] args)
          {
              // Initialing String variable with null value
              String ptr = null;

              // Checking if ptr is null using try catch.
              try
              {
                  if ("gfg".equals(ptr))
                      System.out.print("Same");
                  else
                      System.out.print("Not Same");            
              }
              catch(NullPointerException e)
              {
                  System.out.print("Caught NullPointerException");
              }
          }
      }
      ```
      Output:
      ```Java
      Not Same
      ```     

      #### 2)Keeping a Check on the arguments of a method     
      Before executing the body of your new method, we should first check its arguments for null values and continue with execution of the method, only when the arguments are properly checked. Otherwise, it will throw an **IllegalArgumentException** and notify the calling method that something is wrong with the passed arguments.
      ```Java
      // A Java program to demonstrate that we should
      // check if parameters are null or not before
      // using them.
      import java.io.*;

      class GFG
      {
          public static void main (String[] args)
          {
              // String s set an empty string  and calling getLength()
              String s = "";
              try
              {
                  System.out.println(getLength(s));
              }
              catch(IllegalArgumentException e)
              {
                  System.out.println("IllegalArgumentException caught");
              }

              // String s set to a value and calling getLength()
              s = "GeeksforGeeks";
              try
              {
                  System.out.println(getLength(s));
              }
              catch(IllegalArgumentException e)
              {
                  System.out.println("IllegalArgumentException caught");
              }

              // Setting s as null and calling getLength()
              s = null;
              try
              {
                  System.out.println(getLength(s));
              }
              catch(IllegalArgumentException e)
              {
                  System.out.println("IllegalArgumentException caught");
              }
          }

          // Function to return length of string s. It throws
          // IllegalArgumentException if s is null.
          public static int getLength(String s)
          {
              if (s == null)
                  throw new IllegalArgumentException("The argument cannot be null");
              return s.length();
          }
      }
      ```
      Output:
      ```Java
      0
      13
      IllegalArgumentException caught
      ```     
      #### 3)Use of Ternary Operator
      The ternary operator can be used to avoid NullPointerException. First, the Boolean expression is evaluated. If the expression is **true** then, the value1 is returned, otherwise, the value2 is returned. We can use the ternary operator for handling null pointers:     
      ```Java
      // A Java program to demonstrate that we can use
      // ternary operator to avoid NullPointerException.
      import java.io.*;

      class GFG
      {
          public static void main (String[] args)
          {
              // Initializing String variable with null value
              String str = null;
              String message = (str == null) ? "" :
                                str.substring(0,5);
              System.out.println(message);

              // Initializing String variable with null value
              str = "Geeksforgeeks";
              message = (str == null) ? "" : str.substring(0,5);
              System.out.println(message);
          }
      }
      ```
      Output:
      ```Java
      Geeks
      ```     

      ### Python
      The sole value of types.NoneType. None is frequently used to represent the absence of a value, as when default arguments are not passed to a function.

      ```python
        item = None
        if item != None: # better: if item is not None
            print('pass')
        else:
            print('fail')
      ```   

      Python also can use the try catch block to handle the exception of none reference:
      ```python
      item = None
      try:
          if item != None: # better: if item is not None
              print('pass')
          else:        
              raise TypeError
      except TypeError:
          print('fail')
      ```  

3. Name of instance reference in instance method: What is the keyword for referring to an object instance in an instance method? (this/self/?)
    ### Java
    The keyword **this** is a Java language keyword that represents the current instance of the class in which it appears. It is used to access class variables and methods. Since all instance methods are virtual in Java, this can never be null. You can refer to any member of the current object from within an instance method or a constructor by using this.

    **1.this: to refer current class instance variable**

    The this keyword can be used to refer current class instance variable. If there is ambiguity between the instance variables and parameters, this keyword resolves the problem of ambiguity. In the example, we are using this keyword to distinguish local variable and instance variable.
    ```Java
    class Student{  
    int rollno;  
    String name;  
    float fee;  
    Student(int rollno,String name,float fee){  
    this.rollno=rollno;  
    this.name=name;  
    this.fee=fee;  
    }  
    void display(){System.out.println(rollno+" "+name+" "+fee);}  
    }  

    class TestThis2{  
    public static void main(String args[]){  
    Student s1=new Student(111,"ankit",5000f);  
    Student s2=new Student(112,"sumit",6000f);  
    s1.display();  
    s2.display();  
    }}  
    ```
    Output:
    ```Java
    111 ankit 5000
    112 sumit 6000  
    ```
    If local variables(formal arguments) and instance variables are different, there is no need to use this keyword like in the following program:
    ```Java
    class Student{  
    int rollno;  
    String name;  
    float fee;  
    Student(int r,String n,float f){  
    rollno=r;  
    name=n;  
    fee=f;  
    }  
    void display(){System.out.println(rollno+" "+name+" "+fee);}  
    }  

    class TestThis3{  
    public static void main(String args[]){  
    Student s1=new Student(111,"ankit",5000f);  
    Student s2=new Student(112,"sumit",6000f);  
    s1.display();  
    s2.display();  
    }}    
    ```

    **2.this() : to invoke current class constructor**

    The this() constructor call can be used to invoke the current class constructor. It is used to reuse the constructor. In other words, it is used for constructor chaining. It maintains the chain between the constructors i.e. it is used for constructor chaining.

    Calling default constructor from parameterized constructor:
    ```Java
    class Student{  
    int rollno;  
    String name,course;  
    float fee;  
    Student(int rollno,String name,String course){  
    this.rollno=rollno;  
    this.name=name;  
    this.course=course;  
    }  
    Student(int rollno,String name,String course,float fee){  
    this(rollno,name,course);//reusing constructor  
    this.fee=fee;  
    }  
    void display(){System.out.println(rollno+" "+name+" "+course+" "+fee);}  
    }  
    class TestThis7{  
    public static void main(String args[]){  
    Student s1=new Student(111,"ankit","java");  
    Student s2=new Student(112,"sumit","java",6000f);  
    s1.display();  
    s2.display();  
    }}
    ```
    Output:
    ```Java
    111 ankit java null
    112 sumit java 6000
    ```
    Call to this() must be the first statement in constructor.
    ```Java
    class Student{  
    int rollno;  
    String name,course;  
    float fee;  
    Student(int rollno,String name,String course){  
    this.rollno=rollno;  
    this.name=name;  
    this.course=course;  
    }  
    Student(int rollno,String name,String course,float fee){  
    this.fee=fee;  
    this(rollno,name,course);//C.T.Error  
    }  
    void display(){System.out.println(rollno+" "+name+" "+course+" "+fee);}  
    }  
    class TestThis8{  
    public static void main(String args[]){  
    Student s1=new Student(111,"ankit","java");  
    Student s2=new Student(112,"sumit","java",6000f);  
    s1.display();  
    s2.display();  
    }}
    ```
    Output:
    ```Java
    Compile Time Error: Call to this must be first statement in constructor
    ```

    **3.this: to pass as argument in the constructor call**
    We can pass the this keyword in the constructor also. It is useful if we have to use one object in multiple classes.
    ```Java
    class B{  
      A4 obj;  
      B(A4 obj){  
        this.obj=obj;  
      }  
      void display(){  
        System.out.println(obj.data);//using data member of A4 class  
      }  
    }  

    class A4{  
      int data=10;  
      A4(){  
       B b=new B(this);  
       b.display();  
      }  
      public static void main(String args[]){  
       A4 a=new A4();  
      }  
    }  
    ```
    Output:
    ```Java
    Output:10
    ```
    ### Python
    The keywords **self** is a reference to the class instance. Self is a conventional name, you could put anything else (being coherent) in its stead. For example there are self.name and self.age for student objects. It refers to the object itself, so when you are using it, you are declaring that .name and .age are properties of the Student objects. "Self" signifies an instance of a class. Whenever a new instance of a class is created, "self" indicates that it will have its own variables that aren't shared with other instances.
    We could declare variables within a class without using the self reference, but then those variables would be shared by all instances of that class, which may not be what we intended. For the example above, self.age = age and self.name = name are declaring "instance variables" (as opposed to "class variables"), the values of which would be unique to the instantiated objects of that class. Otherwise, all students would have the same name and age!
    The code should be like this:
    ```Python
    class Student:
        #called each time you create a new Student instance
        def __init__(self,name,age): #special method to initialize
            self.name=name
            self.age=age

        def __str__(self): #special method called for example when you use print
            return "Student %s is %s years old" %(self.name,self.age)

        def call(self, msg): #silly example for custom method
            return ("Hey, %s! "+msg) %self.name

    #initializing two instances of the student class
    bob=Student("Bob",20)
    alice=Student("Alice",19)

    #using them
    print bob.name
    print bob.age
    print alice #this one only works if you define the __str__ method
    print alice.call("Come here!") #notice you don't put a value for self

    #you can modify attributes, like when alice ages
    alice.age=20
    print alice
    ```
    ### Difference

    Technically both self and this are used for the same thing. They are used to access the variable associated with the current instance. Only difference is, you have to include self explicitly as first parameter to an instance method in Python, whereas this is not the case with Java. Moreover, the name self can be anything. It's not a keyword, as you already know. you can even change it to this, and it will work fine. But people like to use self, as it has now become a bit of a convention.
    Here's a simple instance method accessing an instance variable in both Python and Java:

    Python
    ```Python
    class Circle(object):
        def __init__(self, radius):
            # declare and initialize an instance variable
            self.radius = radius

    # Create object. Notice how you are passing only a single argument.  
    # The object reference is implicitly bound to `self` parameter of `__init__` method
    circle1 = Circle(5);
    ```
    Java
    ```Java
    class Circle {
        private int radius;

        public Circle(int radius) {
            this.radius = radius;
        }
    }
    Circle circle1 = new Circle(5);
    ```  


4. Name spaces: How are name spaces implemented and used?
  ### java
  In Java, the idea of a namespace is embodied in Java packages. All code belongs to a package, although that package need not be explicitly named. Code from other packages is accessed by prefixing the package name before the appropriate identifier, for example
  ```java
  class Strin
  ```
  in  
  ```Java
  package java.lang
  ```
   can be referred to as
   ```java
   java.lang.String (this is known as the fully qualified class name).
   ```
    Java offers a construct that makes it unnecessary to type the package name (import). However, certain features (such as reflection) require the programmer to use the fully qualified name.

    Namespaces in Java are not hierarchical as far as the syntax of the language is concerned. However, packages are named in a hierarchical manner. For example, all packages beginning with java are a part of the Java platform—the package
  ```java
  java.lang
  ```
  contains classes core to the language, and
  ```java
  java.lang.reflect
  ```
   contains core classes specifically relating to reflection.

   In Java (and Ada, C#, and others),
   ```java
   namespaces/packages
   ```
    express semantic categories of code.  How specific these categories are and how deep the hierarchies go differ from language to language.

  Function and class scopes can be viewed as implicit namespaces that are inextricably linked with visibility, accessibility, and object lifetime.

   **How are name spaces implemented?**

   The names of Java packages should be all lower case and consist of one or more identifiers, separated by dots (periods), such as one.two.three.

   If you want the contents of several Java source code files to be part of a package called one.two.three, then the following line of code must be the first non-comment line in each of those files:
   ```java
   package one.two.three;
   ```
   All files in a given package must be located in a single subdirectory corresponding to the package name, and the package name will be "translated" to a directory path on the local system (with each dot becoming a separator character beween portions of the path).

   For example, on a Unix or Linux system the class files of the package one.two.three must be stored at a location like this
   ```java
   /rest_of_path/one/two/three
   ```
   while on a Windows system it might be
   ```java
   C:\rest_of_path\one\two\three
   ```
   In addition, the part of the path down to one/two/three (or one\two\three) must be part of the classpath for the given system.

   If you plan to make your Java classes available to the world at large, it is recommended that you register an Internet domain name, and begin the name of each of your packages with your domain name reversed. This will guarantee a globally unique name for each of your packages. And this really does mean "globally", in the sense of "anywhere in the world".

   **How are name spaces used?**

   You get access to all the classes in a package with an import statement like this:
   ```java
   import one.two.three.*;
   ```
   You can also import just one specific class, as in
   ```java
   import one.two.three.SomeClass;
   ```
   When you have access to a class via an import statement, you use its unqualified name like this:
   ```java
   SomeClass myObject = new SomeClass();
   ```
   You can even use a specific class without an import statement, inconvenient and longwinded though that might be, as in
   ```java
   one.two.three.SomeClass myObject = new one.two.three.SomeClass();
   ```
   ### python
   **What is name space?**

   Generally speaking, a namespace (sometimes also called a context) is a naming system for making names unique to avoid ambiguity. Everybody knows a namespacing system from daily life, i.e. the naming of people in firstname and familiy name (surname). Another example is a network: each network device (workstation, server, printer, ...) needs a unique name and address. Yet another example is the directory structure of file systems. The same file name can be used in different directories, the files can be uniquely accessed via the pathnames.

   Many programming languages use namespaces or contexts for identifiers. An identifier defined in a namespace is associated with that namespace. This way, the same identifier can be independently defined in multiple namespaces. (Like the same file names in different directories) Programming languages, which support namespaces, may have different rules that determine to which namespace an identifier belongs.

   Namespaces in Python are implemented as Python dictionaries, this means it is a mapping from names (keys) to objects (values). The user doesn't have to know this to write a Python program and when using namespaces.

   Some namespaces in Python:

   1.global names of a module

   2.local names in a function or method invocation
   built-in names: this namespace contains built-in functions (e.g. abs(), cmp(), ...) and built-in exception names.

   **How are name spaces implemented?**
   We can picture a namespace as a Python dictionary structure, where the dictionary keys represent the names and the dictionary values the object itself (and this is also how namespaces are currently implemented in Python), e.g.,
   ```python
   a_namespace = {'name_a':object_1, 'name_b':object_2, ...}
   ```
   Now, the tricky part is that we have multiple independent namespaces in Python, and names can be reused for different namespaces (only the objects are unique, for example:
   ```python
   a_namespace = {'name_a':object_1, 'name_b':object_2, ...}
   b_namespace = {'name_a':object_3, 'name_b':object_4, ...}
   ```
   For example, everytime we call a for-loop or define a function, it will create its own namespace. Namespaces also have different levels of hierarchy (the so-called “scope”), which we will discuss in more detail in the next section.

   **How are name spaces used?**

   The "from ... import ..." can be used to insert the relevant names directly into the calling module's namespace, and those names can be accessed from the calling module without the qualified name :
   ```python
   # assume modulea defines two functions : func1() and func2() and one class : class1
   from modulea import func1

   func1()
   func2() # this will fail as an undefined name, as will the full name modulea.func2()
   a = class1() # this will fail as an undefined name, as will the full name modulea.class1()
   ```
   Since this directly imports names (without qualification) it can overwrite existing names with no warnings.

   A special form is "from ... import *", which imports all names defined in the named package directly in the calling modules namespace. Use of this form of import, although supported within the language, is generally discouraged as it pollutes the namespace of the calling module and will cause already defined names to be overwritten in the case of name clashes.

   Python also supports "import x as y" as a way of providing an alias or alternative name for use by the calling module:

   ```python
   import numpy as np
   a = np.arange(1000)
   ```

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
    If we would like to use the exception we defines above, we could use the _throw_ keywork as below:
    ```Java
    class CustomException{
       public static void main(String args[]){
          try{
             throw new MyException("Custom");
             // I'm throwing user defined custom exception above
          }
          catch(MyException exp){
             System.out.println("Hi this is my catch block") ;
             System.out.println(exp) ;
          }
       }
    }
    ```
    And the output is as below:
    ```Java
    Hi this is my catch block
    Output String = Custom
    ```


* ### Python

  #### Exception handling
  Here is a list of some standard exceptions in Python:

  EXCEPTION NAME | DESCRIPTION
  --- | ---
  Exception	 | Base class for all exceptions
  StopIteration	 | Raised when the next() method of an iterator does not point to any object.
  SystemExit	 | Raised by the sys.exit() function.  
  StandardError	 | Base class for all built-in exceptions except StopIteration and SystemExit.
  ArithmeticError	 | Base class for all errors that occur for numeric calculation.
  OverflowError	 | Raised when a calculation exceeds maximum limit for a numeric type.
  FloatingPointError   | Raised when a floating point calculation fails.
  ZeroDivisionError	 | Raised when division or modulo by zero takes place for all numeric types.
  AssertionError	 | Raised in case of failure of the Assert statement.
  AttributeError	 | Raised in case of failure of attribute reference or assignment.
  EOFError	 | Raised when there is no input from either the raw_input() or input() function and the end of file is reached.
  ImportError	 | Raised when an import statement fails.
  KeyboardInterrupt	 | Raised when the user interrupts program execution, usually by pressing Ctrl+c.
  LookupError	 | Base class for all lookup errors.
  IndexError   |  Raised when an index is not found in a sequence.
  IOError    | Raised when an input/ output operation fails, such as the print statement or the open() function when trying to open a file that does not exist.
  SystemError	  | Raised when the interpreter finds an internal problem, but when this error is encountered the Python interpreter does not exit.
  SystemExit	  | Raised when Python interpreter is quit by using the sys.exit() function. If not handled in the code, causes the interpreter to exit.
  TypeError	  | Raised when an operation or function is attempted that is invalid for the specified data type.
  ValueError	  | Raised when the built-in function for a data type has the valid type of arguments, but the arguments have invalid values specified.
  RuntimeError	  | Raised when a generated error does not fall into any category.
  NotImplementedError	  | Raised when an abstract method that needs to be implemented in an inherited class is


  This part is similar to the exception handling in Java, as following:

  ```Python
  while True:
     try:
         x = int(input("Please enter a number: "))
         break
     except ValueError:
         print("Oops!  That was no valid number.  Try again...")
  ```

  The try statement works as follows.
  * First, the try clause (the statement(s) between the try and except keywords) is executed.
  * If no exception occurs, the except clause is skipped and execution of the try statement is finished.
  * If an exception occurs during execution of the try clause, the rest of the clause is skipped. Then if its type matches the exception named after the except keyword, the except clause is executed, and then execution continues after the try statement.
  * If an exception occurs which does not match the exception named in the except clause, it is passed on to outer try statements; if no handler is found, it is an unhandled exception and execution stops with a message as shown above.

  A try statement may have more than one except clause, to specify handlers for different exceptions. At most one handler will be executed. Handlers only handle exceptions that occur in the corresponding try clause, not in other handlers of the same try statement. An except clause may name multiple exceptions as a parenthesized tuple, for example:

  ```Python
  except (RuntimeError, TypeError, NameError):
     pass
  ```

  #### Assertions
  An assertion is a sanity-check that you can turn on or turn off when you are done with your testing of the program.

  **Here is a big difference between Java and Python since there is no _assertion_ in Java. If you would like to realize an _assertion_, you have to use a _throw-if_ statement (or to be more accurate, a _throw-if-not_ statement). An expression is tested, and if the result comes up false, an exception is threw.**

  The syntax for assert is:

  ```Python
  assert Expression[, Arguments]
  ```

  If the assertion fails, Python uses ArgumentExpression as the argument for the AssertionError. AssertionError exceptions can be caught and handled like any other exception using the try-except statement, but if not handled, they will terminate the program and produce a traceback.
  This is a function that converts a temperature from degrees Kelvin to degrees Fahrenheit. Since zero degrees Kelvin is as cold as it gets, the function bails out if it sees a negative temperature:

  ```Python
  #!/usr/bin/python

    def KelvinToFahrenheit(Temperature):
       assert (Temperature >= 0),"Colder than absolute zero!"
       return ((Temperature-273)*1.8)+32

    print KelvinToFahrenheit(273)
    print int(KelvinToFahrenheit(505.78))
    print KelvinToFahrenheit(-5)
  ```

  When the above code is executed, it produces the following result:

  ```Python
    32.0
    451
    Traceback (most recent call last):
      File "test.py", line 9, in <module>
        print KelvinToFahrenheit(-5)
      File "test.py", line 4, in KelvinToFahrenheit
        assert (Temperature >= 0),"Colder than absolute zero!"
    AssertionError: Colder than absolute zero!
  ```



  #### Raising Exception

  The raise statement allows the programmer to force a specified exception to occur. The sole argument to raise indicates the exception to be raised. This must be either an exception instance or an exception class (a class that derives from Exception). If an exception class is passed, it will be implicitly instantiated by calling its constructor with no arguments. The general syntax for the raise statement is as follows.

  ```Python
    raise [Exception [, args [, traceback]]]
  ```

  Exception is the type of exception (for example, NameError) and argument is a value for the exception argument. The argument is optional; if not supplied, the exception argument is None.The final argument, traceback, is also optional (and rarely used in practice), and if present, is the traceback object used for the exception.
  If you need to determine whether an exception was raised but don’t intend to handle it, a simpler form of the raise statement allows you to re-raise the exception.For example, an exception can be a string, a class or an object. Most of the exceptions that the Python core raises are classes, with an argument that is an instance of the class. Defining new exceptions is quite easy and can be done as follows:

  ```Python
    def functionName( level ):
       if level < 1:
          raise "Invalid level!", level
          # The code below to this would not be executed
          # if we raise the exception
  ```

  **This _raise_ phrase realizes similar functionalities with the _throw/throws_ phrase in Java.**

  Python also allows you to create your own exceptions by deriving classes from the standard built-in exceptions, which is similar to Java -- Writing your own exceptions and then throwing the exceptions.

  This is an example related to RuntimeError. One class is created that is subclassed from RuntimeError. This is useful when you need to display more specific information when an exception is caught.

  In the try block, the user-defined exception is raised and caught in the except block. The variable e is used to create an instance of the class Networkerror.

  ```Python
    class Networkerror(RuntimeError):
       def __init__(self, arg):
          self.args = arg
    So once you defined above class, you can raise the exception as follows −

    try:
       raise Networkerror("Bad hostname")
    except Networkerror,e:
       print e.args
  ```

  #### Finally blocks

  **Similarly, Python also has _finally_ clause like _final_ blocks in Java.** A _finally_ clause is always executed before leaving the _try_ statement, whether an exception has occurred or not. When an exception has occurred in the _try_ clause and has not been handled by an except clause (or it has occurred in an except or else clause), it is re-raised after the _finally_ clause has been executed. The _finally_ clause is also executed “on the way out” when any other clause of the _try_ statement is left via a _break_, _continue_ or _return_ statement.

  ```Python
  def divide(x, y):
     try:
         result = x / y
     except ZeroDivisionError:
         print("division by zero!")
     else:
         print("result is", result)
     finally:
         print("executing finally clause")
  ```

  executing: divide(2, 1)
  ```
    result is 2.0
    executing finally clause
  ```
  executing: divide(2, 0)
  ```
    division by zero!
    executing finally clause
  ```
  executing: divide("2", "1")
  ```
    executing finally clause
  ```

  The TypeError raised by dividing two strings is not handled by the except clause and therefore re-raised after the finally clause has been executed.

  #### Predefined Clean-up Actions

  **There is another big difference between Java and Python, which is the fact that Java doesn't have _with_ statment but Python does.**
  When we are trying to open a file and print its contents to the screen by using the following code.

  ```Python
  for line in open("myfile.txt"):
    print(line, end="")
  ```

  The problem with this code is that it leaves the file open for an indeterminate amount of time after this part of the code has finished executing. This is not an issue in simple scripts, but can be a problem for larger applications. The with statement allows objects like files to be used in a way that ensures they are always cleaned up promptly and correctly.

  ```Python
  with open("myfile.txt") as f:
    for line in f:
        print(line, end="")
  ```

  It is much convenient to use the _with_ statement when opening a file, however, in Java, you still need to use _try-catch_ statement to catch the exceptions could happened during opening files.



6. **Memory management and garbage collection: How is memory management and garbage collection handled?**

   Memory management is the process of allocating new objects and removing unused objects to make space for those new object allocations.

* ### Java
  #### The Heap and the Nursery

  Java objects reside in an area called the _heap_. The _heap_ is created when the JVM starts up and may increase or decrease in size while the application runs. When the _heap_ becomes full, _garbage_ is collected. During the _garbage collection_ objects that are no longer used are cleared, thus making space for new objects.

  Object creation is faster because global synchronization with the operating system is not needed for every single object. An allocation simply claims some portion of a memory array and moves the offset pointer forward. The next allocation starts at this offset and claims the next portion of the array.

  When an object is no longer used, the garbage collector reclaims the underlying memory and reuses it for future object allocation. This means there is no explicit deletion and no memory is given back to the operating system.

  The _heap_ is sometimes divided into two areas (or generations) called the _nursery_ (or young space) and the _old space_. The _nursery_ is a part of the _heap_ reserved for allocation of new objects. When the _nursery_ becomes full, _garbage_ is collected by running a special young collection, where all objects that have lived long enough in the _nursery_ are promoted (moved) to the _old space_, thus freeing up the _nursery_ for more object allocation. When the _old space_ becomes full garbage is collected there, a process called an _old collection_.

  The reasoning behind a _nursery_ is that most objects are temporary and short lived. A _young collection_ is designed to be swift at finding newly allocated objects that are still alive and moving them away from the nursery. Typically, a _young collection_ frees a given amount of memory much faster than an _old collection_ or a _garbage collection_ of a single-generational _heap_ (a heap without a nursery).

  #### Garbage Collection

  Garbage collection is the process of freeing space in the heap or the nursery for allocation of new objects.

  Every object tree must have one or more root objects. As long as the application can reach those roots, the whole tree is reachable. Special objects called garbage-collection roots are always reachable and so is any object that has a garbage-collection root at its own root.

  There are four kinds of GC roots in Java:
  * Local variables are kept alive by the stack of a thread. This is not a real object virtual reference and thus is not visible. For all intents and purposes, local variables are GC roots.
  * Active Java threads are always considered live objects and are therefore GC roots. This is especially important for thread local variables.
  * Static variables are referenced by their classes. This fact makes them de facto GC roots. Classes themselves can be garbage-collected, which would remove all referenced static variables. This is of special importance when we use application servers, OSGi containers or class loaders in general. We will discuss the related problems in the Problem Patterns section.
  *JNI References are Java objects that the native code has created as part of a JNI call. Objects thus created are treated specially because the JVM does not know if it is being referenced by the native code or not. Such objects represent a very special form of GC root, which we will examine in more detail in the Problem Patterns section below.

  Therefore, a simple Java application has the following GC roots:
  * Local variables in the main method
  * The main thread
  * Static variables of the main class

  Non-reachable objects become garbage.

  * **The Mark and Sweep Model**

    Live objects are tracked and everything else designated garbage. A mark and sweep garbage collection consists of two phases, the mark phase and the sweep phase.

    * It traverses all object references, starting with the GC roots, and marks every object found as alive.
    * All of the heap memory that is not occupied by marked objects is reclaimed. It is simply marked as free, essentially swept free of unused objects.

    During the mark phase all objects that are reachable from Java threads, native handles and other root sources are marked as alive, as well as the objects that are reachable from these objects and so forth. This process identifies and marks all objects that are still used, and the rest can be considered garbage.

    During the sweep phase the heap is traversed to find the gaps between the live objects. These gaps are recorded in a free list and are made available for new object allocation.

    The mostly concurrent mark phase is divided into four parts:

    * Initial marking, where the root set of live objects is identified. This is done while the Java threads are paused.
    * Concurrent marking, where the references from the root set are followed in order to find and mark the rest of the live objects in the heap. This is done while the Java threads are running.
    * Precleaning, where changes in the heap during the concurrent mark phase are identified and any additional live objects are found and marked. This is done while the Java threads are running.
    * Final marking, where changes during the precleaning phase are identified and any additional live objects are found and marked. This is done while the Java threads are paused.

    The mostly concurrent sweep phase consists of four parts:

    * Sweeping of one half of the heap. This is done while the Java threads are running and are allowed to allocate objects in the part of the heap that isn’t currently being swept.
    * A short pause to switch halves.
    * Sweeping of the other half of the heap. This is done while the Java threads are running and are allowed to allocate objects in the part of the heap that was swept first.
    * A short pause for synchronization and recording statistics.

    Garbage collection is intended to remove the cause for classic memory leaks: unreachable-but-not-deleted objects in memory. However, this works only for memory leaks in the original sense. It’s possible to have unused objects that are still reachable by an application because the developer simply forgot to dereference them. Such objects cannot be garbage-collected. Even worse, such a logical memory leak cannot be detected by any software. Even the best analysis software can only highlight suspicious objects. We will examine memory leak analysis in the Analyzing the Performance Impact of Memory Utilization and Garbage Collection section. When objects are no longer referenced directly or indirectly by a GC root, they will be removed. There are no classic memory leaks. Analysis cannot really identify memory leaks; it can only point out suspicious objects.

    In conclusion, only objects that are not referenced are to be garbage collected.

    For example, objects in the following code is never get collected and your memory will be full just to do nothing.

    ```Java
    List objs = new ArrayList();
    for (int i = 0; i  < Integer.MAX_VALUE; i++) objs.add(new Object());
    ```

    But if you don't reference those object ... you can loop as much as you like without memory problem.

    ```Java
    List objs = new ArrayList();
    for (int i = 0; i  < Integer.MAX_VALUE; i++) new Object();
    ```

    Another example:

    ```Java
    public static Object otherMethod(Object obj) {
        return new Object();
    }

    public static void main(String[] args) {
        Object myObj = new Object();
        myObj = otherMethod(myObj);
        // ... more code ...  
    }
    ```

    After you call otherMethod() the original Object created is made unreachable and that's "garbage" that gets garbage collected.

    There are many ways to make object unreferenced:

    * By nulling the reference

    ```Java
    Employee e=new Employee();  
    e=null;  
    ```

    * By assigning a reference to another

    ```Java
    Employee e1=new Employee();  
    Employee e2=new Employee();  
    e1=e2;//now the first object referred by e1 is available for garbage collection  
    ```

    * By annonymous object etc.

    ```Java
    new Employee();
    ```

    * By isolating a Reference

    ```Java
    Referen r2 = new Referen ();
    Referen r3= new Referen ();
    Referen r4= new Referen ();
    r2.r = r3;
    r3.r = r4;
    r4.r = r2;
    r2 = null;
    r3 = null;
    r4 = null;
    ```

* ### Python

  **One difference of memory management between Python and Java is that there is no manual way of doing garbage collection in Java, however, you can create an object and the Python Virtual Machine handles the memory needed and where it shall be placed in the memory layout in Python.**

  Memory management in Python involves a private heap containing all Python objects and data structures. The management of this private heap is ensured internally by the Python memory manager. The Python memory manager has different components which deal with various dynamic storage management aspects, like sharing, segmentation, preallocation or caching.

  The algorithm used for garbage collecting is called Reference counting. That is the Python VM keeps an internal journal of how many references refer to an object, and automatically garbage collects it when there are no more references refering to it.

  On top of the raw memory allocator, several object-specific allocators operate on the same heap and implement distinct memory management policies adapted to the peculiarities of every object type. For example, integer objects are managed differently within the heap than strings, tuples or dictionaries because integers imply different storage requirements and speed/space tradeoffs. The Python memory manager thus delegates some of the work to the object-specific allocators, but ensures that the latter operate within the bounds of the private heap.

  To avoid memory corruption, extension writers should never try to operate on Python objects with the functions exported by the C library: malloc(), calloc(), realloc() and free().

  ```Python
    char *buf = (char *) PyMem_Malloc(BUFSIZ); /* for I/O */

    if (buf == NULL)
        return PyErr_NoMemory();
    /* ...Do some I/O operation involving buf... */
    res = PyBytes_FromString(buf);
    PyMem_Free(buf); /* allocated with PyMem_Malloc */
    return res;
  ```

  Python uses two strategies for memory allocation reference counting and garbage collection.

  Reference counting works by counting the number of times an object is referenced by other objects in the system. When references to an object are removed, the reference count for an object is decremented. When the reference count becomes zero the object is deallocated.

  Reference counting is extremely efficient but it does have some caveats. One such caveat is that it cannot handle reference cycles. A reference cycle is when there is no way to reach an object but its reference count is still greater than zero. The easiest way to create a reference cycle is to create an object which refers to itself as in the example below:

  ```Python
  def make_cycle():
    l = [ ]
    l.append(l)

  make_cycle()
  ```

  Because make_cycle() creates an object l which refers to itself, the object l will not automatically be freed when the function returns. This will cause the memory that l is using to be held onto until the Python garbage collector is invoked.

  Python schedules garbage collection based upon a threshold of object allocations and object deallocations. When the number of allocations minus the number of deallocations are greater than the threshold number, the garbage collector is run. Python provides gc module.

  The garbage collection can be invoked manually in the following way:

   ```Python
    import gc
    collected = gc.collect()
    print "Garbage collector: collected %d objects." % (collected)
   ```


7. Interfaces/protocols/?: How do interfaces/protocols/etc work?
8. Functional features: What functional features are supported and how do they work? (lambdas, closures, etc)
9. Reflection: What reflection abilities are supported?
10. **Procedural programming support: Can functions be created outside of classes or must all functions be methods of a class?**
    * ### Java

    **In Java, you have to declare all the methods within the same class definition.**

    Java has its own object file format - the .class file. Class files contain a wealth of information about their contents that allows the environment to do things with classes at runtime that the native linkage mechanism couldn't even dream about. That information has to start somewhere, and that starting point is the class. The available information allows the compiled code to describe itself without the need for separate files containing a description in source code as you'd have in C, C++ or other languages. That gives you all of the type safety benefits languages using the native linkage lack, even at runtime, and is what enables you to fish an arbitrary class out of a file using reflection and use it with a guaranteed failure if something doesn't match up.

    There are four modifiers in Java:
    * Visible to the package, the _default_. No modifiers are needed.
    * Visible to the class only (_private_).
    * Visible to the world (_public_).
    * Visible to the package and all subclasses (_protected_).

    However, when you use those modifiers to create function, you still can't use the function in Java, you need to create object for those function. However you can use _static_ modifiers to create static function which can be used directly.

    There is no concept of Global Variables in Java. Although, you can achieve it using some thing like this:

    ```Java
        class Globals {
            public static String GLOBAL_VARIABLE_MESSAGE = "Hello World!";
        }
    ```

    And use it somewhere in the code using _Globals.GLOBAL_VARIABLE_MESSAGE_.


    * ### Python

    **In Python, you can define a function outside of a class and then use it in the class body as a method.**

    ```Python
    def func(self):
        print "func"

    class MyClass(object):
        myMethod = func
    ```

    You can also add a function to a class after it has been defined:

    ```Python
    class MyClass(object):
        pass
    def func(self):
        print "func"
    MyClass.myMethod = func
    ```


11. Singleton: How to implement a thread-safe singleton.
    In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one object. This is useful when exactly one object is needed to coordinate actions across the system. The concept is sometimes generalized to systems that operate more efficiently when only one object exists, or that restrict the instantiation to a certain number of objects. The term comes from the mathematical concept of a singleton.
    ### Java
    1) Simple implement in Java(not threasd safe)
    ```Java
    /// <summary>
    /// A simple singleton class implements.
    /// </summary>
    public sealed class Singleton
    {
        private static Singleton _instance = null;

        /// <summary>
        /// Prevents a default instance of the
        /// <see cref="Singleton"/> class from being created.
        /// </summary>
        private Singleton()
        {
        }

        /// <summary>
        /// Gets the instance.
        /// </summary>
        public static Singleton Instance
        {
            get { return _instance ?? (_instance = new Singleton()); }
        }
    }
    ```
    Can be used in the single thread environment.

    2) thread-safe version
    ```Java
    /// <summary>
    /// A thread-safe singleton class.
    /// </summary>
    public sealed class Singleton
    {
        private static Singleton _instance = null;
        private static readonly object SynObject = new object();

        Singleton()
        {
        }

        /// <summary>
        /// Gets the instance.
        /// </summary>
        public static Singleton Instance
        {
            get
            {
                // Syn operation.
                lock (SynObject)
                {
                    return _instance ?? (_instance = new Singleton());
                }
            }
        }
    }
    ```

    3) thread-safe double lock
    ```Java
    /// <summary>
    /// Double-Checked Locking implements a thread-safe singleton class
    /// </summary>
    public sealed class Singleton
    {
        private static Singleton _instance = null;
        // Creates an syn object.
        private static readonly object SynObject = new object();

        Singleton()
        {
        }

        public static Singleton Instance
        {
            get
            {
                // Double-Checked Locking
                if (null == _instance)
                {
                    lock (SynObject)
                    {
                        if (null == _instance)
                        {
                            _instance = new Singleton();
                        }
                    }
                }
                return _instance;
            }
        }
    }
    ```

    4) Lazy initialized
    ```Java
    /// <summary>
    /// .NET 4's Lazy<T> type
    /// </summary>
    public sealed class Singleton
    {
        private static readonly Lazy<Singleton> lazy =
            new Lazy<Singleton>(() => new Singleton());

        public static Singleton Instance { get { return lazy.Value; } }

        private Singleton()
        {
        }
    }
    ```

    ### Pyhton
    1) Simple implement in Python(not threasd safe)  
    ```python
    class Singleton(object):

        # 定义静态变量实例
        __instance = None

        def __init__(self):
            pass

        def __new__(cls, *args, **kwargs):
            if not cls.__instance:
                cls.__instance = super(Singleton, cls).__new__(cls, *args, **kwargs)
            return cls.__instance

    if __name__ == "__main__":
        instance1 = Singleton()
        instance2 = Singleton()

        print id(instance1)
        print id(instance2)
    ```

    2) Tread safe with double lock and lazy initialized
    ```python
    from MyThread import *
    import threading

    Lock = threading.Lock()


    class Singleton(object):

        # 定义静态变量实例
        __instance = None

        def __init__(self):
            pass

        def __new__(cls, *args, **kwargs):
            if not cls.__instance:
                try:
                    Lock.acquire()
                    # double check
                    if not cls.__instance:
                        cls.__instance = super(Singleton, cls).__new__(cls, *args, **kwargs)
                finally:
                    Lock.release()
            return cls.__instance


    def test_singleton_in_thread():
        print id(Singleton())

    if __name__ == "__main__":
        idx = 0
        while 1:
            MyThread(test_singleton_in_thread, []).start()
            idx += 1
            if idx > 0X100:
                break
    ```
    Based on these comparison between Java and Python, all of them can complete a thread-safe Singleton with lazy initialized.        

12. Unique features: Describe any unique features of the language.
    ### Java
    Java have these unique features

   1. Use of 16-bit Unicode for characters, including characters used for writing programs
   2. Run-time interpreter
   3. Support for dynamic and automatic compilation, loading and execution of classes found on the CLASSPATH
   4. Support for automatic garbage collection
   5. Support for Web "applets"
   6. Support for platform-independent GUI programming
   7. Support for event-driven programming
   8. Support for multithreading and synchronization
   9. Support for networking
   10. Support for security via a security manager
   11. Support for native language interface programming (keyword: native)
   12. A single-inheritance hierarchy with "Object" as the root superclass (keywords: extends and super)
   13. Everything must be in a class, including all method definitions.
   14. Interfaces (keywords: interface and implements)
   15. Code organization by packages (keywords: package and import)
   16. A "package" or "friendly" access protection category (but no corresponding keyword)
   17. All object creation at run-time via new
   18. A byte data type
   19. Fixed-size primitive types across all platforms
   20. Wrapper classes for primitive types
   21. The right-shift operator >>>, which uses zero extension, i.e., regarless of the sign, zeroes are inserted at the higher   
   22. order bits when the shift takes place.
   23. Automatic virtual instance methods
   24. Arrays and strings as "first-class" objects, and use of + for conversion to String as well as + and += for string concatenation
   25. Final methods that cannot be redefined and final classes that cannot be extended (inherited from)
   26. Automatic initialization of primitive class members to zero and of member object references to null.
   27. Field initializers and static initialization blocks
   28. Built-in support for comment documentation, so that a source file can contain its own documentation, which is stripped out and formatted into HTML by the javadoc utility
   29. Inner class objects that secretly keep a handle to the object of the outer class that was involved in the creation of the inner class, permitting the inner class object to access members of the outer class object without qualification
   30. Methods that throw or specify "checked" exceptions, i.e., exceptions that must be dealt with (or at least recognized and not dealt with) by the programmer
   31. Object variables and parameters are always references (or "handles")

   ### Python
   1. Intuitive looping through lists
   You can loop through every list-like datastructure like this:
   ```python
     for element in list:
     print(element)
   ```
   2. Arbitrary Integer size
   In Java:
   ```Java
   import java.math.BigInteger;
      public class test {
          public static void main(String[] args) {
              BigInteger a = new BigInteger("2");
              a = a.pow(100000);
              int sum = 0;
              for (int i=0; i < a.toString().length(); i++) {
                  sum += a.toString().charAt(i);
              }
              System.out.println(sum);
          }
      }
   ```
   Python: was much faster in both computation and programming time!
   ```python
      big = 2**100000
      sumOfDigits = 0
      for digit in str(big):
          sumOfDigits += int(digit)

      print(sumOfDigits)
   ```
   Python has no need for a special class as it has arbitrary length integers
   3. Swich values of variables
   You want to make sure, that variable a is smaller than b
   Java:
   ```Java
      tmp = a
      a = min(a, b)
      b = max(tmp, b)
   ```
   Python:
   ```python
   a, b = min(a, b), max(a,b)
   ```
   4. Return more than one variable
   python:
   ```python
      def function (x, y):
          return (x*x, y*y, x+y)

      a, b, c = function(4, 5)
      print("Part 1: %.2f" % a)
      print("Part 3: %.2f" % b)
   ```
   This is called "Argument Unpacking". In fact it does return only one variable (a tuple), but it creating the tuple is so easy that it does not feel like creating another variable.
   5. Short initialisation
   Java: Get a string representation of a list from the standard library
   ```Java
      import java.util.LinkedList;
      import java.util.List;
      public class test {
          public static void main(String[] args) {
              List<Integer> myList = new LinkedList<Integer>();
              myList.add(1);
              myList.add(3);
              myList.add(3);
              myList.add(7);
              System.out.println(myList);
          }
      }
   ```
   Python:
   ```python
      myList = [1, 3, 3, 7]
      print(myList)
   ```
   6. Chaining Comparisons
   Java:
   ```Java
   if (-5 <= x &amp;&amp; x <= 42)
   ```
   Python:
   ```python
   if -5 <= x <= 42:
   ```
   7. Enumeration
   You have a list and you would like to print it, prefixed with the index in the list
   Java:
   ```Java
      List myList = (List initialisation and assignment, multiple lines)
      int i = 0;
      for (int element : myList) {
          System.out.printf("%i: %i", i, element);
          i++;
      }
   ```
   Python:
   ```python
      myList = [1, 3, 3, 7]

      for nr, element in enumerate(myList):
          print("%i: %i" % (nr, element))
   ```
   8. Named String formatting
   ```python
   print("The %(foo)s is %(bar)i." % {'foo': 'answer', 'bar':42})
   ```
   9. any() and all()
   You have a very long list and you want to know, if a prime is in this list.
   Java:
   ```Java
    List myList = (List initialisation and assignment of many values)
    boolean isPrimePresent = false;
    for (int element : myList) {
        if (isPrime(element)) {
            isPrimePresent = true;
            break;
        }
    }

    if (!isPrimePresent) {
        System.out.println("The list did not containe a prime.");
    }
   ```
   Python:
   ```python
    myList = [4, 4, 9, 12]

    if not any(isPrime(x) for x in myList):
        print("The list did not contain a prime")
   ```
   10. Doctest
   You can write Documentation and Unit-Tests at the same time!
   Python:
   ```python
    def factorial(n):
        """Return the factorial of n, an exact integer >= 0.

        >>> [factorial(n) for n in range(6)]
        [1, 1, 2, 6, 24, 120]
        >>> factorial(30)
        265252859812191058636308480000000
        >>> factorial(-1)
        Traceback (most recent call last):
            ...
        ValueError: n must be >= 0

        Factorials of floats are OK, but the float must be an exact integer:
        >>> factorial(30.1)
        Traceback (most recent call last):
            ...
        ValueError: n must be exact integer
        >>> factorial(30.0)
        265252859812191058636308480000000

        It must also not be ridiculously large:
        >>> factorial(1e100)
        Traceback (most recent call last):
            ...
        OverflowError: n too large
        """

        import math
        if not n >= 0:
            raise ValueError("n must be >= 0")
        if math.floor(n) != n:
            raise ValueError("n must be exact integer")
        if n+1 == n:  # catch a value like 1e300
            raise OverflowError("n too large")
        result = 1
        factor = 2
        while factor <= n:
            result *= factor
            factor += 1
        return result


    if __name__ == "__main__":
        import doctest
        doctest.testmod()
   ```
   11. Sphinx
   Documentation can be generated from partially docstrings, partially rst files with Sphinx.
   12. for ... else
   You have a very long list and you want to know, if a prime is in this list.
   Java:
   ```Java
    List myList = (List initialisation and assignment of many values)
    boolean isPrimePresent = false;
    for (int element : myList) {
        if (isPrime(element)) {
            isPrimePresent = true;
            break;
        }
    }

    if (!isPrimePresent) {
        System.out.println("The list did not containe a prime.");
    }
   ```
   Python:
   ```python
    myList = [1, 3, 3, 7]

    for element in myList:
        if isPrime(element):
            break
    else:
        print("The list did not containe a prime.")
   ```
   13. Step through lists
   Print only every n-th element of an iterable.
   Python:
   ```python
    for element in myList[::n]:
        print elemenet
   ```
   14. Dynamically add properties to objects and classes
   Python:
   ```python
    class Node(object):
        value = 3

    a = Node()
    b = Node()

    print a.value

    """ colorize the node! """
    #print a.color ==> AttributeError

    # thats ok, although the object originally had no attribute "color"
    a.color = "white"
    print a.color

    # You can even add a property to the class
    Node.special = "here is it"
    print b.special
   ```
   15. Imaginary numbers
   Python directly supports usage of imaginary numbers:
   Python:
   ```python
   (2j + 1)**2
   ```
