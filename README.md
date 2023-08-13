# HandlingException

Handling Exceptions Summary


Exception is an object occurred at runtime to disturb the flow of creation. Whenever we have exceptions in our application the application will be terminated abnormally and the rest of the application will not be executed.There are two ways to handle exceptions
1. try-catch block and 
2. Using throws’ keyword. 

Try and catch is used to handle exceptions. In the try block, we have the code that we think that may raise an exception. In the catch block, we have the handling exception code( the code that will handle the exception). We can have multiple catch blocks if we have multiple exceptions. To handle all exceptions we can use the root class of Exception which is ‘Exception’. 

## Types of Exception:
1. Checked exceptions
2. Unchecked exceptions
3. Errors

## Checked exceptions:
Checked exceptions are exceptions caused due to the developers mistake. Checked Exceptions are as follows:
1. FileNotFoundException 
2. SQLException.
3. InterruptedException

FileNotFoundException is caused whenever the developer can’t find the file.For example:


SQLException is caused whenever the developer can’t access with the database. We must handle the checked exceptions.For example:


InterruptedException: ‘Thread.sleep()’ is used to stop the application. Thread is like a task and its task is to stop the application(sleep). ‘Thread.sleep();’ can throw InterruptedException. We must handle the exceptions since it is a checked exception.  For an example:


## Unchecked exceptions:
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


## Error
The last type of exception are errors. Errors are caused due to the lack of System resources. Error examples are as follows: 
StackOverflowError
OutOfMemoryError

## 'throws' keyword:

Try and catch is used to handle exceptions, but the throws keyword is used to give responsibility to others such as methods or caller methods. 
Lets take an example of the throws keyword:


Exmplanation: Lets say we have 3 methods. In the first method, an exception had raised but it is not handling it. Instead it it using the throws keyword and throwing the exception. The other method had the responsibility to handle the exception but it also isn’t handling the exception, it is throwing the exception. The 3rd method has to handle the exception and it is handling the exception. We can see from that example, that the method that raised the exception doesn’t have to handle it it throw the exception and the other method can handle the exception. But, what if none of the methods handle the exceptions?! The main method will have to handle the exception but if the main method isn’t handling the main method, JVM must handle the exception.
In short, We have to use the throws keyword whenever we are handling checked exceptions. So that way the method can navigate to another method. We don’t have to use the throws keyword whenever we are handling unchecked exception. It will automatically navigate from one method to another.

## Printing exceptions
There are 3 ways to pring the exceptions:
1. Print the reference variable:  Lets say an ArithmeticException has occurred. When we run the output we will get ‘java.lang.ArithmeticException /: by zero’. The output will look like ‘java.lang.ArithmeticException /: by zero’ whenever we print the reference variable.

   
2. Use ‘.getMessage()’ method:
To print out a small description, we can use ‘.getMessage()’. For example, /: by zero will get printed if we use .getMessage().


3. Use ‘.printStackTrace()’ method. If we want to print a long description like where the exception first occurred and what happened next we can use ‘.printStackTrace().’

   
## 5 keywords in Exception
There are 5 keyword in exception handling:
1. try,
2. catch,
3. finally,
4. throws
5. throw
  
###### Note: We have already talked about try, catch and throws keyword. Let’s talk about the finally keyword.


### About 'finally' keyword:
There are 3 cases in try and catch block:
1. The first case is that the connection opens in the try block. The transaction is successful. Then, the application gets terminated normally and the connection closes.
   
2.  The second case is that the connection opens in the try block. The transaction is not successful, but the catch block is matched. Then, the application gets terminated normally and the connection closes
 
4. The 3rd case is that the connection opens in the try block. The transaction is not successful and the catch block is not matched. The application gets terminated abnormally and the connect does not close.


To overcome the 3rd case we can use the 'finally' block. The finally block will get executed in both normal and abnormal cases. To release the resources(scanner, file and connection) we can use the 'finally' keyword. 

#### example 1:

class Test{

   public static void main(String[] args){

      try{
      
         System.out.println("try block");
         
      }
      catch(Exception e){

         System.out.println("catch block");
         
      }
      finally{

         System.out.println("finally block");
         
      }
      
   }
   
}


Description: ► Lets say we have try, catch and finally block. But in those 3 blocks we are just printing out words. The catch block will not get executed because there is no exception in the try block. The try block and finally block will get executed.

#### example 2:

class Test{

   public static void main(String[] args){

      try{

         System.out.println("conection open");
         System.out.println(10/0);
         
      }
      catch(Exception e){

         System.out.println("exception handling");
      }

      finally{

         System.out.println("connection closing");
         
      }
      
   }
   
}

Description: ► The code above the exception will be executed(line 134), and the code below the exception(line 135) will not be executed. So, "connection open" will be executed, since it is above the exception code. The finally block will also be executed because the application is normal. The catch block will also be executed since an exception was raised in the try block.

#### example 3:


class Test{

   public static void main(String[] args){

      try{

         System.out.println("conection open");
         System.out.println(10/0);
         
      }
      catch(NullPointerException e){

         System.out.println("exception handling");
      }

      finally{

         System.out.println("connection closing");
         
      }
      
   }
   
}

Description: ► Again we have tr, catch and finally  block. In the try block, 'ArithmeticException' was raised(line 165) but in the catch block(line 168), we wrote 'NullPointerException'. Those 2 exceptions dont match and because they dont match the catch block will not get executed. This is an abnoral case, where try block and finally block only will get executed.


#### example 4:

class Test{

   public static void main(String[] args){

      try{

         System.out.println("connection open");
         
      }

      finally{

         System.out.println("connection close");
      }
      
   }
   
}

Description: ►  Try and finally block is also valid. We can use try and catch block but we can also use try and finally block.


#### example 5:

class Test{

   public static void main(String[] args){

      try{

         System.out.println(10/0);
         
      }
      catch(ArithmeticException e){

         System.out.println("ratan".charAt(28));
      }

      finally{

         int[] a = {10,20,30.40};

         System.out.println(a[9]);
         
      }
      
   }
   
}


Description: ► This time all 3 exceptions has raised. ArithmeticException(line 218) was raised in the try block. StringIndexOutOfBoundsException(line 223) was raised in the catch block. ArrayIndexOutOfBoundsException(line 230) was raised in the finally block. JVM will raise only one exception and that exception is the exception in the finally block. 


#### example 5: 

class Test{

   public static void main(String[] args){

      try{

         System.out.println("try");

         System.out.println("block");

         System.exit(0);  // JVM shutdown
      }

      finally{

          System.out.println("finally");
      }
   }
}

Description: ► 

- 'System.exit(0)' will sht JVM down.
 
When JVM is shut down, finally block will not be executed. But, if 'System.exit(0)' is below exception code, finally block be be executed.

# Try and catch possobilities 

#### 1. try{

   }

   catch(){

   }

   _____________


#### 2. try{
  
   }

   catch(){

   }

   statements

   try{
  
   }

   catch(){

   }

   _____________

#### 3.  try{
  
   }

   catch(){

   }

   catch(){

   }

   _________


#### 4. try{

      try{

      }

      catch(){

      }
   
   }

   catch(){

   }

   ___________

#### 5. try{

   }

   catch(){

         try{

         }

         catch(){

         }
   
   }
   
   ________

#### 6. try{

      try{

      }

      catch(){

      }
   
   }

   catch(){

         try{

         }

         catch(){

         }
   
   }
   
_______


## Try with resources

Try block with reources is try with parentheses( try(){} ). We can declare the resources inside try block. Once try block is completed, then the resource is automatically released.

1. If the resource throws unchecked exception, catch block is not mandatory.

2. If the resource throws checked exception, catch block is required, because we need to handle checked exceptions.

Example:

import java.io.*;

class Test{

   public static void main(String[] args){

      try(FileInputStream fis = new FileInputStream("abc.txt") ){

         System.out.println("enter a number");
         
      }

      catch(FileNotFoundException e){

         e.printStackTrace();
         
      }
      
   }
   
}


The example above isnt correct.  We are not calling the close() method, but it is internally callig close() method. The close method can cause IOException. IOException is checked exception, so we need to handle it.


import java.io.*;

class Test{

   public static void main(String[] args){

      try(FileInputStream fis = new FileInputStream("abc.txt") ){

         System.out.println("enter a number");
         
      }

      catch(IOException e){

         e.printStackTrace();
         
      }
      
   }
   
}

##### The advantage of using try with resources is that whenever the try block is completed, then the resource is automatically released.

____________

