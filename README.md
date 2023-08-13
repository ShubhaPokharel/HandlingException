# HandlingException

Handling Exceptions Summary


Exception is an object occurred at runtime to disturb the flow of creation. Whenever we have exceptions in our application the application will be terminated abnormally and the rest of the application will not be executed.There are two ways to handle exceptions
1. try-catch block and 
2. Using throws’ keyword. 

Try and catch is used to handle exceptions. In the try block, we have the code that we think that may raise an exception. In the catch block, we have the handling exception code( the code that will handle the exception). We can have multiple catch blocks if we have multiple exceptions. To handle all exceptions we can use the root class of Exception which is ‘Exception’. 

# Types of Exception:
1. Checked exceptions
2. Unchecked exceptions
3. Errors

# Checked exceptions:
Checked exceptions are exceptions caused due to the developers mistake. Checked Exceptions are as follows:
1. FileNotFoundException 
2. SQLException.
3. InterruptedException

FileNotFoundException is caused whenever the developer can’t find the file.For example:


SQLException is caused whenever the developer can’t access with the database. We must handle the checked exceptions.For example:


InterruptedException: ‘Thread.sleep()’ is used to stop the application. Thread is like a task and its task is to stop the application(sleep). ‘Thread.sleep();’ can throw InterruptedException. We must handle the exceptions since it is a checked exception.  For an example:


# Unchecked exceptions:
Unchecked exceptions are caused due to the end users input mistakes. Unchecked Exceptions are as follows:
1. ArithmeticException, 
2. StringIndexOutOfBoundsException, 
3. ArrayIndexOutOfBoundsException. 

ArithmeticException is caused when a number is being divided by 0. Anything divided by 0 is 0. Therefore, we are going to get ArithmeticException. We don’t have to handle unchecked exceptions, it is not mandatory.

StringIndexOutOfBoundsException is caused whenever we use charAt() method to get the specific string in an index. 
Let’s say for example we have the word ‘aruna’. Aruna has 5 letters but the index starts from 0. The end user is trying to get a letter from aruna but instead it typed 24. We only have 5 letters not 24, so we will get StringIndexOutOfBoundsException. 
String ind = 'aruna';
String letter = ind.charAt(24);
System.outpringln(letter);

ArrayIndexOutOfBoundsException is caused whenever the end user tries to find the index of a number but types a small or huge number. For example, if we have only 4 numbers(10,20,30,40). The index starts from 0 ,so we have 3 numbers. Instead the end user put 12. And there is no index of 12. Therefore, we will get ArrayIndexOutOfBoundsExceptions.


# Error
The last type of exception are errors. Errors are caused due to the lack of System resources. Error examples are as follows: 
StackOverflowError
OutOfMemoryError

# 'throws' keyword:

Try and catch is used to handle exceptions, but the throws keyword is used to give responsibility to others such as methods or caller methods. 
Lets take an example of the throws keyword:


Exmplanation: Lets say we have 3 methods. In the first method, an exception had raised but it is not handling it. Instead it it using the throws keyword and throwing the exception. The other method had the responsibility to handle the exception but it also isn’t handling the exception, it is throwing the exception. The 3rd method has to handle the exception and it is handling the exception. We can see from that example, that the method that raised the exception doesn’t have to handle it it throw the exception and the other method can handle the exception. But, what if none of the methods handle the exceptions?! The main method will have to handle the exception but if the main method isn’t handling the main method, JVM must handle the exception.
In short, We have to use the throws keyword whenever we are handling checked exceptions. So that way the method can navigate to another method. We don’t have to use the throws keyword whenever we are handling unchecked exception. It will automatically navigate from one method to another.

# Printing exceptions
There are 3 ways to pring the exceptions:
1. Print the reference variable:  Lets say an ArithmeticException has occurred. When we run the output we will get ‘java.lang.ArithmeticException /: by zero’. The output will look like ‘java.lang.ArithmeticException /: by zero’ whenever we print the reference variable.

   
2. Use ‘.getMessage()’ method:
To print out a small description, we can use ‘.getMessage()’. For example, /: by zero will get printed if we use .getMessage().


3. Use ‘.printStackTrace()’ method. If we want to print a long description like where the exception first occurred and what happened next we can use ‘.printStackTrace().’

   
# 5 keywords in Exception
There are 5 keyword in exception handling:
1. try,
2. catch,
3. finally,
4. throws
5. throw
  
#Note: We have already talked about try, catch and throws keyword. Let’s talk about the finally keyword.

#About 'finally' keyword:
There are 3 cases in try and catch block:
1. The first case is that the connection opens in the try block. The transaction is successful. Then, the application gets terminated normally and the connection closes.
   
2.  The second case is that the connection opens in the try block. The transaction is not successful, but the catch block is matched. Then, the application gets terminated normally and the connection closes
 
4. The 3rd case is that the connection opens in the try block. The transaction is not successful and the catch block is not matched. The application gets terminated abnormally and the connect does not close.


To overcome the 3rd case we can use the 'finally' block. The finally block will get executed in both normal and abnormal cases. To release the resources(scanner, file and connection) we can use the 'finally' keyword. For example:




Description: Lets say we have try, catch and finally block. But in those 3 blocks we are just printing out words. The catch block will not get executed because there is no exception in the try block. The try block and finally block will get executed.
