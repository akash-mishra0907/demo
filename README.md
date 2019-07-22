# demo

Exam 1 - Results
Attempt 3
Question 1: Correct
Consider below code:

//Test.java
package com.udayan.oca;
 
class SpecialString {
     String str;
     SpecialString(String str) {
         this.str = str;
     }
}
 
public class Test {
     public static void main(String[] args) {
         System.out.println(new String("Java"));
         System.out.println(new StringBuilder("Java"));
         System.out.println(new SpecialString("Java"));
     }
}
What will be the result of compiling and executing Test class?









Explanation
String and StringBuilder classes override toString() method, which prints the text stored in these classes. SpecialString class doesn't override toString() method and hence when instance of SpecialString is printed on to the console, you get: <fully qualified name of SpecialString class>@<hexadecimal representation of hashcode>.
Question 2: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.io.FileNotFoundException;
import java.io.IOException;
 
abstract class Super {
     public abstract void m1() throws IOException;
}
 
class Sub extends Super {
     @Override
     public void m1() throws IOException {
         throw new FileNotFoundException();
     }
}
 
public class Test {
     public static void main(String[] args) {
         Super s = new Sub();
         try {
             s.m1();
         } catch (FileNotFoundException e) {
             System.out.print("M");
         } finally {
             System.out.print("N");
         }
     }
}








Explanation
Even though an instance of FileNotFoundException is thrown by method m1() at runtime, but method m1() declares to throw IOException. Reference variable s is of Super type and hence for compiler, call to s.m1(); is to method m1() of Super, which throws IOException. And as IOException is checked exception hence calling code should handle it.As calling code doesn't handle IOException or its super type, so s.m1(); gives compilation error.
Question 3: Correct
Given code:

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String [] arr = {"A", "B", "C", "D", "E"};
         for(/*INSERT*/) {
             System.out.print(arr[n]);
         }
     }
}
Which option, if used to replace /*INSERT*/, on execution will print ACE on to the console?









Explanation
You have to print element at index 0, 2 and 4, which means index must start with 0 and step expression should increment the index by 2. Hence, int n = 0; n < arr.length; n += 2 is the correct answer.
Question 4: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.util.function.Predicate;
 
public class Test {
     public static void main(String[] args) {
         String [] arr = {"A", "ab", "bab", "Aa", "bb", "baba", "aba", "Abab"};
 
         Predicate<String> p = s -> s.toUpperCase().substring(0,1).equals("A");
 
         processStringArray(arr, p);
     }
 
     private static void processStringArray(String [] arr, 
                                                Predicate<String> predicate) {
         for(String str : arr) {
             if(predicate.test(str)) {
                 System.out.println(str);
             }
         }
     }
}










Explanation
Let us suppose test string is "aba". Lambda expression s.toUpperCase().substring(0,1).equals("A"); means: "aba".toUpperCase().substring(0,1).equals("A"); => "ABA".substring(0,1).equals("A"); => "A".equals("A"); => true. This lambda expression returns true for any string starting with a (in lower or upper case). Based on the lambda expression, 5 array elements passes the Predicate's test and are printed on to the console.
Question 5: Correct
Consider below code:

//Guest.java
class Message {
     static void main(String [] args) {
         System.out.println("Welcome! " + args[1]);
     }
}
 
public class Guest {
     public static void main(String [] args) {
         Message.main(args);
     }
}
And the commands:
javac Guest.java
java Guest James Gosling

What is the result?











Explanation
Class Guest has special main method but main method defined in Message class is not public and hence it can't be called by JVM. But there is no issue with the syntax hence no compilation error. java Guest James Gosling passes new String [] {"James", "Gosling"} to args of Guest.main method. Guest.main method invokes Message.main method with the same argument: new String [] {"James", "Gosling"}. args[1] is "Gosling" hence "Welcome! Gosling" gets printed on to the console.
Question 6: Correct
Which of the following statement is correct about below code?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         do {
             System.out.println(100);
         } while (false);
         System.out.println("Bye");
     }
}








Explanation
As do-while loop executes at least once, hence none of the code is unreachable in this case. Java runtime prints 100 to the console, then it checks boolean expression, which is false. Hence control goes out of do-while block. Java runtime executes 2nd System.out.println statement to print "Bye" on to the console.
Question 7: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.Period;
 
public class Test {
     public static void main(String [] args) {
         Period period = Period.of(0, 0, 0);
         System.out.println(period);
     }
}
What will be the result of compiling and executing Test class?









Explanation
Period.of(0, 0, 0); is equivalent to Period.ZERO. ZERO period is displayed as P0D, other than that, Period components (year, month, day) with 0 values are ignored. toString()'s result starts with P, and for non-zero year, Y is appended; for non-zero month, M is appended; and for non-zero day, D is appended. P,Y,M and D are in upper case. NOTE: Period.parse(CharSequence) method accepts the String parameter in "PnYnMnD" format, over here P,Y,M and D can be in any case.
Question 8: Correct
Which of the following is a checked Exception?









Explanation
ClassCastException extends RuntimeException (unchecked exception), FileNotFoundException extends IOException, IOException extends Exception (checked exception), ExceptionInInitializerError is from Error family and is thrown by an static initializer block, RuntimeException and all its sub classes are unchecked exceptions.
Question 9: Correct
Consider the code of Test.java file:

package com.udayan.oca;
 
class Student {
     String name;
     int age;
 
     void Student() {
         Student("James", 25);
     }
 
     void Student(String name, int age) {
         this.name = name;
         this.age = age;
     }
}
 
public class Test {
     public static void main(String[] args) {
         Student s = new Student();
         System.out.println(s.name + ":" + s.age);
     }
}
What will be the result of compiling and executing Test class?









Explanation
Methods can have same name as the class. Student() and Student(String, int) are methods and not constructors of the class, note the void return type of these methods. As no constructors are provided in the Student class, java compiler adds default no-arg constructor. That is why the statement Student s = new Student(); doesn't give any compilation error. Default values are assigned to instance variables, hence null is assigned to name and 0 is assigned to age. In the output, null:0 is displayed.
Question 10: Correct
What will be the result of compiling and executing Test class?

//Test.java
package com.udayan.oca.test;
 
abstract class Animal {
     private String name;
 
     Animal(String name) {
        this.name = name;
     }
 
     public String getName() {
         return name;
     }
}
 
class Dog extends Animal {
     private String breed;
     Dog(String breed) {
         this.breed = breed;
     }
 
     Dog(String name, String breed) {
         super(name);
         this.breed = breed;
     }
 
     public String getBreed() {
         return breed;
     }
}
 
public class Test {
     public static void main(String[] args) {
         Dog dog1 = new Dog("Beagle");
         Dog dog2 = new Dog("Bubbly", "Poodle");
         System.out.println(dog1.getName() + ":" + dog1.getBreed() + ":" + 
                             dog2.getName() + ":" + dog2.getBreed());
     }
}












Explanation
abstract class can have constructors and it also possible to have abstract class without any abstract method. So, there is no issue with Animal class. Java compiler adds super(); as the first statement inside constructor, if call to another constructor using this(...) or super(...) is not available. Inside Animal class Constructor, compiler adds super(); => Animal(String name) { super(); this.name = name; }, super() in this case invokes the no-arg constructor of Object class and hence no compilation error here. Compiler changes Dog(String) constructor to: Dog(String breed) { super(); this.breed = breed; }. No-arg constructor is not available in Animal class and as another constructor is provided, java compiler doesn't add default constructor. Hence Dog(String) constructor gives compilation error. There is no issue with Dog(String, String) constructor.
Question 11: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDateTime;
 
public class Test {
     public static void main(String [] args) {
         LocalDateTime obj = LocalDateTime.now();
         System.out.println(obj.getSecond());
     }
}
Which of the following statement is correct?









Explanation
LocalDateTime stores both date and time parts. LocalDateTime.now(); retrieves the current date and time from the system clock. obj.getSecond() can return any value between 0 and 59.
Question 12: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         double price = 90000;
         String model;
         if(price > 100000) {
             model = "Tesla Model X";
         } else if(price <= 100000) {
             model = "Tesla Model S";
         }
           System.out.println(model);
     }
}








Explanation
In this case "if - else if" block is used and not "if - else" block. 90000 is assigned to variable 'price' but you can assign parameter value or call some method returning double value, such as: 'double price = currentTemp();'. In these cases compiler will not know the exact value until runtime, hence Java Compiler is not sure which boolean expression will be evaluated to true and so variable model may not be initialized. Usage of LOCAL variable, 'model' without initialization gives compilation error. Hence, System.out.println(model); gives compilation error.
Question 13: Correct
Below is the code of Test.java file:

package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String [] args) {
         List<Integer> list = new ArrayList<Integer>();
         list.add(new Integer(2));
         list.add(new Integer(1));
         list.add(new Integer(0));
 
         list.remove(list.indexOf(0));
 
         System.out.println(list);
     }
}
What will be the result of compiling and executing Test class?









Explanation
remove method of List interface is overloaded: remove(int) and remove(Object). indexOf method accepts argument of Object type, in this case list.indexOf(0) => 0 is auto-boxed to Integer object so no issues with indexOf code. list.indexOf(0) returns 2 (index at which 0 is stored in the list). So list.remove(list.indexOf(0)); is converted to list.remove(2); remove(int) version is matched, it's a direct match so compiler doesn't do auto-boxing in this case. list.remove(2) removes the element at index 2, which is 0. Hence in the output, you get [2, 1].
Question 14: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         Double [] arr = new Double[2];
         System.out.println(arr[0] + arr[1]);
     }
}








Explanation
Array elements are initialized to their default values. arr is referring to an array of Double type, which is reference type and hence both the array elements are initialized to null. To calculate arr[0] + arr[1], java runtime converts the expression to arr[0].doubleValue() + arr[1].doubleValue(). As arr[0] and arr[1] are null hence calling doubleValue() method throws NullPointerException.
Question 15: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         StringBuilder sb = new StringBuilder("Java");
         String s1 = sb.toString();
         String s2 = sb.toString();
 
         System.out.println(s1 == s2);
     }
}








Explanation
toString() method defined in StringBuilder class doesn't use String literal rather uses the constructor of String class to create the instance of String class. So both s1 and s2 refer to different String instances even though their contents are same. s1 == s2 returns false.
Question 16: Correct
Consider code below:

package com.udayan.oca;
 
class PenDrive {
     int capacity;
     PenDrive(int capacity) {
         this.capacity = capacity;
     }
}
 
class OTG extends PenDrive {
     String type;
     OTG(int capacity, String type) {
         //TODO
     }
}
 
public class Test {
     public static void main(String[] args) {
         OTG obj = new OTG(64, "TYPE-C");
         System.out.println(obj.capacity + ":" + obj.type);
     }
}
 
Currently above code is giving compilation error. 

Which of the option can successfully replace //TODO statement such that on executing Test class, output is 64:TYPE-C?






Explanation
Java compiler adds super(); as the first statement inside constructor, if call to another constructor using this(...) or super(...) is not available. Compiler adds super(); as the first line in OTG's constructor: OTG(int capacity, String type) { super(); } but PenDrive class doesn't have a no-arg constructor and that is why OTG's constructor gives compilation error. To correct the compilation error, parent class constructor should be invoked by using super(capacity); This would resolve compilation error. super(capacity); will only assign value to capacity property, to assign value to type another statement is needed. this.type = type; must be the 2nd statement. Remember: Constructor call using this(...) or super(...) must be the first statement inside the constructor.
Question 17: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     char c;
     double d;
     float f;
     public static void main(String[] args) {
         Test obj = new Test();
         System.out.println(">" + obj.c);
         System.out.println(">" + obj.d);
         System.out.println(">" + obj.f);
     }
}




Explanation
primitive type instance variables are initialized to respective zeros (byte: 0, short: 0, int: 0, long: 0L, float: 0.0f, double: 0.0, boolean: false, char: \u0000). When printed on the console; byte, short, int & long prints 0, float & double print 0.0, boolean prints false and char prints nothing or non-printable character (white space). Reference type instance variables are initialized to null.
Question 18: Correct
For the class Test, which options, if used to replace /*INSERT*/, will print "Lucky no. 7" on to the console? Select 3 options.

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         /*INSERT*/
         switch(var) {
             case 7:
                 System.out.println("Lucky no. 7");
                 break;
             default:
                 System.out.println("DEFAULT");
         }
     }
}










Explanation
switch can accept primitive types: byte, short, int, char; wrapper types: Byte, Short, Integer, Character; String and enums. In this case, all are valid values but only 3 executes "case 7:". case is comparing integer value 7. NOTE: character seven, '7' is different from integer value seven, 7. So "char var = '7';" and "Character var = '7';" will print DEFAULT on to the console.
Question 19: Correct
What will be the result of compiling and executing Test class?

//Test.java
package com.udayan.oca;
 
class Student {
     String name;
     int marks;
 
     Student(String name, int marks) {
         this.name = name;
         this.marks = marks;
     }
}
 
public class Test {
     public static void main(String[] args) {
         Student student = new Student("James", 25);
         int marks = 25;
         review(student, marks);
         System.out.println(marks + "-" + student.marks);
     }
 
     private static void review(Student stud, int marks) {
         marks = marks + 10;
         stud.marks+=marks;
     }
}








Explanation
This question checks your knowledge of pass-by-value and pass-by-reference schemes. In below statements: student<main> means student inside main method. On execution of main method: student<main> --> {"James", 25}, marks<main> = 25. On execution of review method: stud<review> --> {"James", 25} (same object referred by student<main>), marks<review> = 25 (this marks is different from the marks defined in main method). marks<review> = 35 and stud.marks = 60. So at the end of review method: stud<review> --> {"James", 60}, marks<review> = 35. Control goes back to main method: student<main> --> {"James", 60}, marks<main> = 25. Changes done to reference variable are visible in main method but changes done to primitive variable are not reflected in main method.
Question 20: Skipped
For the class Test, which options, if used to replace /*INSERT*/, will print "Hurrah! I passed..." on to the console?

public class Test {
     /*INSERT*/ {
         System.out.println("Hurrah! I passed...");
     }
}












Explanation
As System.out.println needs to be executed on executing the Test class, this means special main method should replace /*INSERT*/. Special main method's name should be "main" (all characters in lower case), should be static, should have public access specifier and it accepts argument of String [] type. String [] argument can use any identifier name, even though in most of the cases you will see "args" is used. Position of static and public can be changed but return type must come just before the method name.
Question 21: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<String> list1 = new ArrayList<>();
         list1.add("A");
         list1.add("D");
 
         List<String> list2 = new ArrayList<>();
         list2.add("B");
         list2.add("C");
 
         list1.addAll(1, list2);
 
         System.out.println(list1);
     }
}
What will be the result of compiling and executing Test class?









Explanation
list1 --> [A, D], list2 --> [B, C], list1.addAll(1, list2); is almost equal to list1.add(1, [B, C]); => Inserts B at index 1, C takes index 2 and D is moved to index 3. list1 --> [A, B, C, D]
Question 22: Correct
Consider the following class:

package com.udayan.oca;
 
public class Employee {
     public int passportNo; //line 2
}
Which of the following is the correct way to make the variable 'passportNo' read only for any other class?









Explanation
passportNo' should be read-only for any other class.This means make 'passportNo' private and provide public getter method. Don't provide public setter as then 'passportNo' will be read-write property. If passportNo is declared with default scope, then other classes in the same package will be able to access passportNo for read-write operation.
Question 23: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
class Message {
     String msg = "Happy New Year!";
 
     public void print() {
         System.out.println(msg);
     }
}
 
public class Test {
     public static void change(Message m) {
         m = new Message();
         m.msg = "Happy Holidays!";
     }
 
     public static void main(String[] args) {
         Message obj = new Message();
         obj.print();
         change(obj);
         obj.print();
     }
}








Explanation
It is pass-by-reference scheme.Initially, msg = "Happy New Year!"Call to method change(Message) doesn't modify the msg property of passed object rather it creates another Message object and modifies the msg property of new object to "Happy Holidays!"So, the instance of Message referred by obj remains unchanged.Hence in the output, you get:Happy New Year! Happy New Year!
Question 24: Skipped
Consider below code: 

public class Test {
     static {
         System.out.println(1/0);
     }
 
     public static void main(String[] args) {
         System.out.println("HELLO");
     }
}
On execution, does Test class print "HELLO" on to the console?





Explanation
To invoke the special main method, JVM loads the class in the memory. At that time, static initializer block is invoked. 1/0 throws a RuntimeException and as a result static initializer block throws an instance of java.lang.ExceptionInInitializerError.
Question 25: Correct
Which of the following is not a valid array declaration?









Explanation
1st array dimension must be specified at the time of declaration. new int[][8]; gives compilation error as 1st dimension is not specified.
Question 26: Correct
Consider code of Test.java file:

package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<Character> list = new ArrayList<>();
         list.add(0, 'V');
         list.add('T');
         list.add(1, 'E');
         list.add(3, 'O');
 
         if(list.contains('O')) {
             list.remove('O');
         }
 
         for(char ch : list) {
             System.out.print(ch);
         }
     }
}
What will be the result of compiling and executing Test class?













Explanation
list.add(0, 'V'); => char 'V' is converted to Character object and stored as the first element in the list. list --> [V]. list.add('T'); => char 'T' is auto-boxed to Character object and stored at the end of the list. list --> [V,T]. list.add(1, 'E'); => char 'E' is auto-boxed to Character object and inserted at index 1 of the list, this shifts T to the right. list --> [V,E,T]. list.add(3, 'O'); => char 'O' is auto-boxed to Character object and added at index 3 of the list. list --> [V,E,T,O].list.contains('O') => char 'O' is auto-boxed to Character object and as Character class overrides equals(String) method this expression returns true. Control goes inside if-block and executes: list.remove('O');. remove method is overloaded: remove(int) and remove(Object). char can be easily assigned to int so compiler tags remove(int) method. list.remove(<ASCCI value of 'O'>); ASCCI value of 'A' is 65 (this everybody knows) so ASCII value of 'O' will be more than 65. list.remove('O') throws runtime exception, as it tries to remove an item from the index greater than 65 but allowed index is 0 to 3 only.
Question 27: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         short [] args = new short[]{50, 50};
         args[0] = 5;
         args[1] = 10;
         System.out.println("[" + args[0] + ", " + args[1] + "]");
     }
}








Explanation
main method's parameter variable name is "args" and it is a local to main method. So, same name "args" can't be used directly within the curly brackets of main method. short [] args = new short[]{50, 50}; gives compilation error for using same name for local variable.
Question 28: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String [] args) {
         int a = 100;
         System.out.println(-a++);
     }
}










Explanation
First add parenthesis (round brackets) to the given expression: -a++. There are 2 operators involved. unary minus and Postfix operator. Let's start with expression and value of a.-a++; [a = 100]. -(a++); [a = 100] Postfix operator has got higher precedence than unary operator. -(100); [a = 101] Use the value of a (100) in the expression and after that increase the value of a to 101. -100; [a = 101] -100 is printed on to the console.
Question 29: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     private static void m(int x) {
         System.out.println("int version");
     }
 
     private static void m(char x) {
         System.out.println("char version");
     }
 
     public static void main(String [] args) {
         int i = '5';
         m(i);
         m('5');
     }
}










Explanation
Method m is overloaded. Which overloaded method to invoke is decided at compile time. m(i) is tagged to m(int) as i is of int type and m('5') is tagged to m(char) as '5' is char literal.
Question 30: Correct
For the class Test, which options, if used to replace /*INSERT*/, will print [5, 10] on to the console? Select 3 options.

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         /*INSERT*/
         arr[0] = 5;
         arr[1] = 10;
         System.out.println("[" + arr[0] + ", " + arr[1] + "]");
     }
}











Explanation
You can declare one-dimensional array by using either "short arr []" or "short [] arr". You can create an array object on the same line or next line. "short arr [] = new short[2];" and "short [] arr; arr = new short[2];" both are correct. Array size cannot be specified at the time of declaration, so short [2] arr; gives compilation error. short [] arr = {}; => arr refers to a short array object of 0 size. so arr[0] = 5; and arr[1] = 10; will throw ArrayIndexOutOfBoundsException at runtime. short [] arr = new short[]{0, 0}; => arr refers to a short array object of size 2 and both array elements have value 100. arr[0] = 5; replaces 1st element value with 5 and arr[1] = 10; replaces 2nd element value with 10. So this is also a correct option. short [] arr = new short[2]{100, 100}; => Array's size can't be specified, if you use {} to assign values to array elements.
Question 31: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String [] fruits = {"apple", "banana", "mango", "orange"};
         for(String fruit : fruits) {
             System.out.print(fruit + " ");
             if(fruit.equals("mango")) {
                 continue;
             }
             System.out.println("salad!");
             break;
         }        
     }
}










Explanation
break; and continue; are used inside for-loop, hence no compilation error. In first iteration "apple " is printed on to the console. Cursor remains on the same line as print method is used and not println. boolean expression of if-block returns false, control goes just after if-block and appends "salad!" on to the console. break; statement takes the control out of for loop, main method ends and program terminates successfully. So in the console, you get "apple salad!"
Question 32: Skipped
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         m1(); //Line 3
     }
 
     private static void m1() throws Exception { //Line 6
         System.out.println("NOT THROWING ANY EXCEPTION"); //Line 7
     }
}








Explanation
If a method declares to throw Exception or its sub-type other than RuntimeException types, then calling method should follow handle or declare rule. In this case, as method m1() declares to throw Exception, so main method should either declare the same exception or its super type in its throws clause OR m1(); should be surrounded by try-catch block. Line 3 in this case causes compilation error.
Question 33: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         System.out.println("Output is: " + 10 != 5);
     }
}








Explanation
Binary plus (+) has got higher precedence than != operator. Let us group the expression. "Output is: " + 10 != 5 = ("Output is: " + 10) != 5 [!= is binary operator, so we have to evaluate the left side first. + operator behaves as concatenation operator.] = "Output is: 10" != 5 Left side of above expression is String, and right side is int. But String can't be compared to int hence compilation error.
Question 34: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String fruit = "mango";
         switch (fruit) {
             default:
                 System.out.println("ANY FRUIT WILL DO");
             case "Apple":
                 System.out.println("APPLE");
             case "Mango":
                 System.out.println("MANGO");
             case "Banana":
                 System.out.println("BANANA");
                 break;
         }
     }
}








Explanation
"mango" is different from "Mango", so there is no matching case available. default block is executed, "ANY FRUIT WILL DO" is printed on to the screen. No break statement inside default, hence control enters in fall-through and executes remaining blocks until the break; is found or switch block ends. So in this case, it prints APPLE, MANGO, BANANA one after another and break; statement takes control out of switch block. main method ends and program terminates successfully.
Question 35: Skipped
Which of the following correctly defines class Printer?





Explanation
If package is used then it should be the first statement, but javadoc and developer comments are not considered as java statements so a class can have developer and javadoc comments before the package statement. If import and package both are available, then correct order is package, import, class declaration.
Question 36: Incorrect
Consider codes below:

//A.java
package com.udayan.oca;
 
public class A {
     public void print() {
         System.out.println("A");
     }
}
 
//B.java
package com.udayan.oca;
 
public class B extends A {
     public void print() {
         System.out.println("B");
     }
}
 
//Test.java
package com.udayan.oca.test;
 
import com.udayan.oca.*;
 
public class Test {
     public static void main(String[] args) {
         A obj1 = new A();
         B obj2 = (B)obj1;
         obj2.print();
     }
}
What will be the result of compiling and executing Test class?









Explanation
Class A and B are declared public and inside same package com.udayan.oca. Method print() of class A has correctly been overridden by B. print() method is public so no issues in accessing it anywhere. Let's check the code inside main method. A obj1 = new A(); => obj1 refers to an instance of class A. B obj2 = (B)obj1; => obj1 is of type A and it is assigned to obj2 (B type), hence explicit casting is necessary. obj1 refers to an instance of class A, so at runtime obj2 will also refer to an instance of class A. sub type can't refer to an object of super type so at runtime B obj2 = (B)obj1; will throw ClassCastException.
Question 37: Skipped
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String str1 = new String("Core");
         String str2 = new String("CoRe");
         System.out.println(str1 = str2);
     }
}








Explanation
System.out.println(str1 = str2) has assignment(=) operator and not equality(==) operator.After the assignment, str1 refers to "CoRe" and System.out.println prints "CoRe" to the console.
Question 38: Skipped
Consider below code:

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
 
public class Test {
     public static void main(String [] args) {
          LocalDate date = LocalDate.of(2020, 9, 31);
          System.out.println(date);
     }
}
What will be the result of compiling and executing Test class?









Explanation
LocalDate.of(...) method first validates year, then month and finally day of the month. September can't have 31 days so LocalDate.of(...) method throws an instance of java.time.DateTimeException class.
Question 39: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         double [] arr = new int[2]; //Line 3
         System.out.println(arr[0]); //Line 4
     }
}








Explanation
int variable can easily be assigned to double type but double [] and int [] are not compatible. In fact, both are siblings and can't be assigned to each other, so Line 3 causes compilation failure.
Question 40: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.time.LocalTime;
 
public class Test {
     public static void main(String[] args) {
         LocalTime time = LocalTime.of(16, 40);
         String amPm = time.getHour() >= 12 ? (time.getHour() == 12) ? "PM" : "AM";
         System.out.println(amPm);
     }
}








Explanation
This question is on ternary operator (?:). If an expression has multiple ternary operators then number of ? and : should match. Given expression contains 2 ? and 1 : and hence Compilation Error.
Question 41: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         byte var = 100;
         switch(var) {
             case 100:
                 System.out.println("var is 100");
                 break;
             case 200:
                 System.out.println("var is 200");
                 break;
             default:
                 System.out.println("In default");
         }
     }
}








Explanation
case values must evaluate to the same type / compatible type as the switch expression can use. switch expression can accept following: char or Character byte or Byte short or Short int or Integer An enum only from Java 6 A String expression only from Java 7 In this case, switch expression [switch (var)] is of byte type.byte range is from -128 to 127. But in case expression [case 200], 200 is outside byte range and hence compilation error.
Question 42: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         String s = new String("Hello");
         List<String> list = new ArrayList<>();
         list.add(s);
         list.add(new String("Hello"));
         list.add(s);
         s.replace("l", "L");
 
         System.out.println(list);
     }
}
What will be the result of compiling and executing Test class?









Explanation
ArrayList's 1st and 3rd items are referring to same String instance referred by s [s --> "Hello"] and 2nd item is referring to another instance of String.String is immutable, which means s.replace("l", "L"); creates another String instance "HeLLo" but s still refers to "Hello" [s --> "Hello"]. [Hello, Hello, Hello] is printed in the output.
Question 43: Skipped
How many objects of Pen class are eligible for Garbage Collection at Line 4?

package com.udayan.oca;
 
class Pen {
     
}
 
public class TestPen {
     public static void main(String[] args) {
         new Pen(); //Line 1
         Pen p = new Pen(); // Line 2
         change(p); //Line 3
         System.out.println("About to end."); //Line 4
     }
 
     public static void change(Pen pen) { //Line 5
         pen = new Pen(); //Line 6
     }
}








Explanation
Object created at Line 1 becomes eligible for Garbage collection after Line 1 only, as there are no references to it. So We have one object marked for GC. Object created at Line 6 becomes unreachable after change(Pen) method pops out of the STACK, and this happens after Line 3. So at Line 4, we have two Pen objects eligible for Garbage collection: Created at Line 1 and Created at Line 6.
Question 44: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
 
class MyLocalDate extends LocalDate {
     @Override
     public String toString() {
         return super.getDayOfMonth() + "-" + super.getMonthValue() + 
            "-" +  super.getYear();
     }
}
 
public class Test {
     public static void main(String [] args) {
         MyLocalDate date = LocalDate.parse("1980-03-16");
         System.out.println(date);
     }
}
What will be the result of compiling and executing Test class?











Explanation
LocalDate is a final class so cannot be extended.
Question 45: Correct
Given the code of Test.java file:

package com.udayan.oca;
 
class Point {
     int x;
     int y;
     void assign(int x, int y) {
         x = this.x;
         this.y = y;
     }
 
     public String toString() {
         return "Point(" + x + ", " + y + ")";
     }
}
 
public class Test {
     public static void main(String[] args) {
         Point p1 = new Point();
         p1.x = 10;
         p1.y = 20;
         Point p2 = new Point();
         p2.assign(p1.x, p1.y);
         System.out.println(p1.toString() + ";" + p2.toString());
     }
}
What will be the result of compiling and executing Test class?











Explanation
HINT: First check if members are accessible or not. All the codes are in same file Test.java, and Point class & variable x, y are declared with default modifier hence these can be accessed within the same package. Class Test belongs to same package so no issues in accessing Point class and instance variables of Point class. Make use of pen and paper to draw the memory diagrams (heap and stack). It will be pretty quick to reach the result.Point p1 = new Point(); means p1.x = 0 and p1.y = 0 as instance variable are initialized to respective zeros. p1.x = 10; means replace 0 with 10 in p1.x, p1.y = 20; means replace 0 with 20 in p1.y, Point p2 = new Point(); means p2.x = 0 and p2.y = 0 as instance variable are initialized to respective zeros. p2.assign(p1.x, p1.y); invokes the assign method, parameter variable x = 10 and y = 20. As assign is invoked on p2 reference variable hence this and p2 refers to same Point object. x = this.x; means assign 0 to parameter variable x, no changes in this.y, which means p2.x is unchanged. this.y = y; means assign 20 to this.y, which means p2.y is now 20So after assign method is invoked and control goes back to main method: p1.x = 10, p1.y = 20, p2.x = 0 and p2.y = 20. Output is: Point(10, 20);Point(0, 20)
Question 46: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         int [] arr = {2, 1, 0};
         for(int i : arr) {
             System.out.println(arr[i]);
         }
     }
}








Explanation
Inside enhanced for loop, System.out.println(arr[i]); is used instead of System.out.println(i); When loop executes 1st time, i stores the first array element, which is 2 but System.out.println statement prints arr[2] which is 0. Loop executes in this manner and prints 0 1 2 on to the console.
Question 47: Correct
What will be the result of compiling and executing the Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         int grade = 60;
         if(grade = 60)
             System.out.println("You passed...");
         else
             System.out.println("You failed...");
     }
}








Explanation
Following are allowed in boolean expression of if statement:1. Any expression whose result is either true or false. e.g. age > 20 2. A boolean variable. e.g. flag 3. A boolean literal: true or false 4. A boolean assignment. e.g. flag = true boolean expression in this case is: (grade = 60), which is an int assignment and not boolean assignment. Hence Compilation error.
Question 48: Incorrect
Consider below code fragment:

interface Printable {
     public void setMargin();
     public void setOrientation();
}
 
abstract class Paper implements Printable { //Line 7
     public void setMargin() {}
     //Line 9
}
 
class NewsPaper extends Paper { //Line 12
     public void setMargin() {}
     //Line 14
}
Above code is currently giving compilation error. Which 2 modifications, done independently, enable the code to compile?









Explanation
First you should find out the reason for compilation error. Methods declared in Printable interface are implicitly abstract, no issues with Printable interface. class Paper is declared abstract and it implements Printable interface, it overrides setMargin() method but setOrientation() method is still abstract. No issues with class Paper as it is an abstract class and can have 0 or more abstract methods. class NewsPaper is concrete class and it extends Paper class (which is abstract). So class Paper must override setOrientation() method OR it must be declared abstract. Replacing Line 9 with 'public abstract void setOrientation();' is not necessary and it will not resolve the compilation error in NewsPaper class. Replacing Line 7 with 'class Paper implements Printable {' will cause compilation failure of Paper class as it inherits abstract method 'setOrientation'.
Question 49: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<Integer> list = new ArrayList<>();
         list.add(100);
         list.add(200);
         list.add(100);
         list.add(200);
         list.remove(100);
 
         System.out.println(list);
     }
}












Explanation
List cannot accept primitives, it can accept objects only. So, when 100 and 200 are added to the list, then auto-boxing feature converts these to wrapper objects of Integer type. So, 4 items gets added to the list. One can expect the same behavior with remove method as well that 100 will be auto-boxed to Integer object. But remove method is overloaded in List interface: remove(int) => Removes the element from the specified position in this list and remove(Object) => Removes the first occurrence of the specified element from the list. As remove(int) version is available, which perfectly matches with the call remove(100); hence compiler does not do auto-boxing in this case. But at runtime remove(100) tries to remove the element at 100th index and this throws IndexOutOfBoundsException.
Question 50: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.time.LocalDate;
import java.time.Month;
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<LocalDate> dates = new ArrayList<>();
         dates.add(LocalDate.parse("2018-07-11"));
         dates.add(LocalDate.parse("1919-02-25"));
         dates.add(LocalDate.of(2020, 4, 8));
         dates.add(LocalDate.of(1980, Month.DECEMBER, 31));
 
         dates.removeIf(x -> x.getYear() < 2000);
 
         System.out.println(dates);
     }
}








Explanation
LocalDate objects can be created by using static method parse and of. removeIf(Predicate) method was added as a default method in Collection interface in JDK 8 and it removes all the elements of this collection that satisfy the given predicate. Predicate's test method returns true for all the LocalDate objects with year less than 2000. So all the LocalDate objects with year value less than 2000 are removed from the list. Remaining LocalDate objects are printed in their insertion order.
Question 51: Correct
Which of these access modifiers can be used for a top level interface?









Explanation
A top level interface can be declared with either public or default modifiers. public interface is accessible across all packages but interface declared with default modifier and be accessed in the defining package only.
Question 52: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<String> dryFruits = new ArrayList<>();
         dryFruits.add("Walnut");
         dryFruits.add("Apricot");
         dryFruits.add("Almond");
         dryFruits.add("Date");
 
         Iterator<String> iterator = dryFruits.iterator();
         while(iterator.hasNext()) {
             String dryFruit = iterator.next();
             if(dryFruit.startsWith("A")) {
                 dryFruits.remove(dryFruit);
             }
         }
        
         System.out.println(dryFruits);
    }
}
What will be the result of compiling and executing Test class?









Explanation
ConcurrentModificationException exception may be thrown for following condition: 1. Collection is being iterated using Iterator/ListIterator or by using for-each loop. And 2. Execution of Iterator.next(), Iterator.remove(), ListIterator.previous(), ListIterator.set(E) & ListIterator.add(E) methods. These methods may throw java.util.ConcurrentModificationException in case Collection had been modified by means other than the iterator itself, such as Collection.add(E) or Collection.remove(Object) or List.remove(int) etc. For the given code, 'dryFruits' list is being iterated using the Iterator<String>. hasNext() method of Iterator has following implementation: public boolean hasNext() { return cursor != size; } Where cursor is the index of next element to return and initially it is 0. 1st Iteration: cursor = 0, size = 4, hasNext() returns true. iterator.next() increments the cursor by 1 and returns "Walnut". 2nd Iteration: cursor = 1, size = 4, hasNext() returns true. iterator.next() increments the cursor by 1 and returns "Apricot". As "Apricot" starts with "A", hence dryFruits.remove(dryFruit) removes "Apricot" from the list and hence reducing the list's size by 1, size becomes 3. 3rd Iteration: cursor = 2, size = 3, hasNext() returns true. iterator.next() method throws java.util.ConcurrentModificationException. If you want to remove the items from ArrayList, while using Iterator or ListIterator, then use Iterator.remove() or ListIterator.remove() method and NOT List.remove(...) method. Using List.remove(...) method while iterating the list (using the Iterator/ListIterator or for-each) may throw java.util.ConcurrentModificationException.
Question 53: Correct
Consider codes below:

//A.java
package com.udayan.oca;
 
public class A {
     public int i1 = 1;
     protected int i2 = 2;
}
 
//B.java
package com.udayan.oca.test;
 
import com.udayan.oca.A;
 
public class B extends A {
     public void print() {
         A obj = new A();
         System.out.println(obj.i1); //Line 8
         System.out.println(obj.i2); //Line 9
         System.out.println(this.i2); //Line 10
         System.out.println(super.i2); //Line 11
     }
 
     public static void main(String [] args) {
         new B().print();
     }
}
One of the statements inside print() method is causing compilation failure. Which of the below solutions will help to resolve compilation error?









Explanation
class A is declared public and defined in com.udayan.oca package, there is no problem in accessing class A outside com.udayan.oca package. class B is defined in com.udayan.oca.test package, to extend from class A either use import statement "import com.udayan.oca.A;" or fully qualified name of the class com.udayan.oca.A. No issues with this class definition as well.Variable i1 is declared public in class A, so Line 8 doesn't cause any compilation error. Variable i2 is declared protected so it can only be accessed in subclass using using inheritance but not using object reference variable. obj.i2 causes compilation failure. class B inherits variable i2 from class A, so inside class B it can be accessed by using either this or super. Line 10 and Line 11 don't cause any compilation error.
Question 54: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
 
public class Test {
    public static void main(String [] args) {
        LocalDate newYear = LocalDate.of(2018, 1, 1);
        LocalDate christmas = LocalDate.of(2018, 12, 25);
        boolean flag1 = newYear.isAfter(christmas);
        boolean flag2 = newYear.isBefore(christmas);
        System.out.println(flag1 + ":" + flag2);
    }
}
What will be the result of compiling and executing Test class?









Explanation
isAfter and isBefore method can be interpreted as: Does 1st Jan 2018 come after 25th Dec 2018? No, false. Does 1st Jan 2018 come before 25th Dec 2018? Yes, true.
Question 55: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         int x = 1;
         while(checkAndIncrement(x)) {
             System.out.println(x);
         }
     }
 
     private static boolean checkAndIncrement(int x) {
         if(x < 5) {
             x++;
             return true;
         } else {
             return false;
         }
     }
}








Explanation
This is an example of pass-by-value scheme. x of checkAndIncrement method contains the copy of variable x defined in main method. So, changes done to x in checkAndIncrement method are not reflected in the variable x of main. x of main remains 1 as code inside main is not changing its value. Every time checkAndIncrement method is invoked with argument value 1, so true is returned always and hence while loop executed indefinitely.
Question 56: Skipped
A bank's swift code is generally of 11 characters and used in international money transfers. 
An example of swift code: ICICINBBRT4
ICIC: First 4 letters for bank code
IN: Next 2 letters for Country code
BB: Next 2 letters for Location code
RT4: Next 3 letters for Branch code

Which of the following code correctly extracts country code from the swift code referred by String reference variable swiftCode?









Explanation
substring(int beginIndex, int endIndex) is used to extract the substring. The substring begins at "beginIndex" and extends till "endIndex - 1". Country code information is stored at index 4 and 5, so the correct substring method to extract country code is: swiftCode.substring(4, 6);
Question 57: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
 
class Counter {
     int count;
     Counter(int count) {
         this.count = count;
     }
 
     public String toString() {
         return "Counter-" + count;
     }
}
 
public class Test {
     public static void main(String[] args) {
         ArrayList<Counter> original = new ArrayList<>();
         original.add(new Counter(10));
 
         ArrayList<Counter> cloned = (ArrayList<Counter>) original.clone();
         cloned.get(0).count = 5;
 
         System.out.println(original);
     }
}
What will be the result of compiling and executing Test class?









Explanation
Let' suppose: new ArrayList<>() is stored at [15EE00]. new Counter(10) is stored at [25AF06]. original contains memory address of above counter object. [15EE00] --> {25AF06}. Now original.clone() will create a new array list object, suppose at [45BA12] and then it will copy the contents of the ArrayList object stored at [15EE00]. So, cloned contains memory address of the same counter object. [45BA12] --> {25AF06} In this case, original != cloned, but original.get(0) == cloned.get(0). This means both the array lists are created at different memory location but refer to same Counter object. cloned.get(0) returns counter object stored at [25AF06] and .count = 5 means [25AF06] refers to [Counter object (5)]. System.out.println(original); Prints the element of ArrayList original, which is: {25AF06} and toString() method prints: Counter-5 as Counter object referred by [25AF06] is [Counter object (5)].
Question 58: Correct
____________ uses access modifiers to protect variables and hide them within a class.

Which of the following options accurately fill in the blanks above?









Explanation
Encapsulation is all about having private instance variable and providing public getter and setter methods.
Question 59: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
import java.time.LocalTime;
 
public class Test {
     public static void main(String [] args) {
         LocalDate date = LocalDate.parse("1947-08-14");
         LocalTime time = LocalTime.MAX;
         System.out.println(date.atTime(time));
     }
}
What will be the result of compiling and executing Test class?









Explanation
LocalTime.MIN --> {00:00}, LocalTime.MAX --> {23:59:59.999999999}, LocalTime.MIDNIGHT --> {00:00}, LocalTime.NOON --> {12:00}. date.atTime(LocalTime) method creates a LocalDateTime instance by combining date and time parts. toString() method of LocalDateTime class prints the date and time parts separated by T in upper case.
Question 60: Skipped
Consider 3 files:

//Order.java
package orders;
 
public class Order {
    
}
 
//Item.java
package orders.items;
 
public class Item {
    
}
 
//Shop.java
package shopping;
 
/*INSERT*/
 
public class Shop {
     Order order = null;
     Item item = null;
}
For the class Shop, which options, if used to replace /*INSERT*/, will resolve all the compilation errors? Select 2 options.








Explanation
If you check the directory structure, you will find that directory "orders" contains "items", but orders and orders.items are different packages.import orders.*; will only import all the classes in orders package but not in orders.items package. You need to import Order and Item classes. To import Order class, use either import orders.Order; OR import orders.*; and to import Item class, use either import orders.items.Item; OR import orders.items.*;
Question 61: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
class Student {
     private String name;
     private int age;
 
     Student(String name, int age) {
         this.name = name;
         this.age = age;
     }
 
     public String toString() {
         return "Student[" + name + ", " + age + "]";
     }
}
 
public class Test {
     public static void main(String[] args) {
         List<Student> students = new ArrayList<>();
         students.add(new Student("James", 25));
         students.add(new Student("James", 27));
         students.add(new Student("James", 25));
         students.add(new Student("James", 25));
 
         students.remove(new Student("James", 25));
 
         for(Student stud : students) {
             System.out.println(stud);
         }
     }
}
What will be the result of compiling and executing Test class?









Explanation
Before you answer this, you must know that there are 5 different Student object created in the memory (4 at the time of adding to the list and 1 at the time of removing from the list). This means these 5 Student objects will be stored at different memory addresses.remove(Object) method removes the first occurrence of matching object and equals(Object) method decides whether 2 objects are equal or not. equals(Object) method defined in Object class uses == operator to check the equality and in this case as 5 Student objects are stored at different memory location, hence not equal. Nothing is removed from the students list, all the 4 Student objects are printed in the insertion order.
Question 62: Incorrect
Consider below code:

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.function.Predicate;
 
class Employee {
     private String name;
     private int age;
     private double salary;
 
     public Employee(String name, int age, double salary) {
         this.name = name;
         this.age = age;
         this.salary = salary;
     }
 
     public String getName() {
         return name;
     }
 
    public int getAge() {
         return age;
     }
 
    public double getSalary() {
         return salary;
     }
 
    public String toString() {
         return name;
     }
}
 
public class Test {
     public static void main(String [] args) {
         List<Employee> list = new ArrayList<>();
         list.add(new Employee("James", 25, 15000));
         list.add(new Employee("Lucy", 23, 12000));
         list.add(new Employee("Bill", 27, 10000));
         list.add(new Employee("Jack", 19, 5000));
         list.add(new Employee("Liya", 20, 8000));
 
         process(list, /*INSERT*/);
 
         System.out.println(list);
     }
 
     private static void process(List<Employee> list, Predicate<Employee> predicate) {
         Iterator<Employee> iterator = list.iterator();
         while(iterator.hasNext()) {
             if(predicate.test(iterator.next()))
             iterator.remove();
         }
      }
}
Which of the following lambda expressions, if used to replace /*INSERT*/, prints [Jack, Liya] on to the console?











Explanation
Jack's salary is 5000 and Liya's salary is 8000. If Employee's salary is >= 10000 then that Employee object is removed from the list. Allowed lambda expression is: (Employee e) -> { return e.getSalary() >= 10000; }, Can be simplified to: (e) -> { return e.getSalary() >= 10000; } => type can be removed from left side of the expression. Further simplified to: e -> { return e.getSalary() >= 10000; } => if there is only one parameter in left part, then round brackets (parenthesis) can be removed. Further simplified to: e -> e.getSalary() >= 10000 => if there is only one statement in the right side then semicolon inside the body, curly brackets and return statement can be removed. But all 3 [return, {}, ;] must be removed together. NOTE: there should not be any space between - and > of arrow operator.
Question 63: Correct
For the given code snippet:

List<String> list = new /*INSERT*/(); 

Which of the following options, if used to replace /*INSERT*/, compiles successfully?









Explanation
List is an interface so its instance can't be created using new keyword. List<String> and List<> will cause compilation failure. ArrayList implements List interface, so it can be it can be used to replace /*INSERT*/. List<String> list = new ArrayList<String>(); compiles successfully. Starting with JDK 7, Java allows to not specify type while initializing the ArrayList. Type is inferred from the left side of the statement. So List<String> list = new ArrayList<>(); is a valid syntax starting with JDK 7.
Question 64: Skipped
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String str = "java";
         StringBuilder sb = new StringBuilder("java");
 
         System.out.println(str.equals(sb) + ":" + sb.equals(str));
     }
}










Explanation
equals method declared in Object class has the declaration: public boolean equals(Object). Generally, equals method is used to compare different instances of same class but if you pass any other object, there is no compilation error. Parameter type is Object so it can accept any Java object. str.equals(sb) => String class overrides equals(Object) method but as "sb" is of StringBuilder type so this returns false. StringBuilder class doesn't override equals(Object) method. So Object version is invoked which uses == operator, hence sb.equals(str) returns false as well. false:false is printed on to the console.
Question 65: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
import java.time.Period;
import java.time.format.DateTimeFormatter;
 
public class Test {
     public static void main(String [] args) {
         LocalDate date = LocalDate.of(2012, 1, 11);
         Period period = Period.ofMonths(2);
         DateTimeFormatter formatter = DateTimeFormatter.ofPattern("MM-dd-yy");
         System.out.print(formatter.format(date.minus(period)));
     }
}
What will be the result of compiling and executing Test class?











Explanation
date --> {2012-01-11}, period --> {P2M}, date.minus(period) --> {2011-11-11} [subtract 2 months period from {2012-01-11}, month is changed to 11 and year is changed to 2011]. formatter -> {MM-dd-yy}, when date {2011-11-11} is formatter in this format 11-11-11 is printed on to the console.
Question 66: Skipped
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         try {
             main(args);
         } catch (Exception ex) {
             System.out.println("CATCH-");
         }
             System.out.println("OUT");
     }
}








Explanation
main(args) method is invoked recursively without specifying any exit condition, so this code ultimately throws java.lang.StackOverflowError. StackOverflowError is a subclass of Error type and not Exception type, hence it is not handled. Stack trace is printed to the console and program ends abruptly.Java doesn't allow to catch specific checked exceptions if these are not thrown by the statements inside try block. catch(java.io.FileNotFoundException ex) {} will cause compilation error in this case as main(args); will never throw FileNotFoundException. But Java allows to catch Exception type, hence catch (Exception ex) {} doesn't cause any compilation error.




Exam 2 - Results
Attempt 1
Question 1: Correct
Which of the following correctly defines class Printer?





Explanation
If package is used then it should be the first statement, but javadoc and developer comments are not considered as java statements so a class can have developer and javadoc comments before the package statement. If import and package both are available, then correct order is package, import, class declaration. Multiple package statements are not allowed.
Question 2: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         System.out.println(new Boolean("ture"));
     }
}








Explanation
Boolean class code uses equalsIgnoreCase method to validate the passed String, so if passed String is "true" ('t', 'r', 'u' and 'e' can be in any case), then boolean value stored in Boolean object is true otherwise false. In this question passed String is "ture" and not "true" and that is why false is printed on to the console.
Question 3: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         int score = 60;
         switch (score) {
             default:
                 System.out.println("Not a valid score");
             case score < 70:
                 System.out.println("Failed");
                 break;
             case score >= 70:
                 System.out.println("Passed");
                 break;
         }
     }
}    









Explanation
case values must evaluate to the same type / compatible type as the switch expression can use. switch expression can accept following: char or Character, byte or Byte, short or Short, int or Integer, An enum only from Java 6, A String expression only from Java 7. In this case, switch expression [switch (score)] is of int type. But case expressions, score < 70 and score >= 70 are of boolean type and hence compilation error.
Question 4: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String s1 = "OcA";
         String s2 = "oCa";
         System.out.println(s1.equals(s2));
     }
}








Explanation
equals(String str) method of String class matches two String objects and it takes character's case into account while matching. Alphabet A in upper case and alphabet a in lower case are not equal according to this method. As String objects referred by s1 and s2 have different cases, hence output is false.
Question 5: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         int [] arr = {3, 2, 1};
         for(int i : arr) {
             System.out.println(arr[i]);
         }
     }
}










Explanation
Inside enhanced for loop, System.out.println(arr[i]); is used instead of System.out.println(i); When loop executes 1st time, i stores the first array element, which is 3 but System.out.println statement prints arr[3] and this causes java runtime to throw the instance of ArrayIndexOutOfBoundsException.
Question 6: Incorrect
Consider below code:

package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<StringBuilder> days = new ArrayList<>();
         days.add(new StringBuilder("Sunday"));
         days.add(new StringBuilder("Monday"));
         days.add(new StringBuilder("Tuesday"));
 
         if(days.contains(new StringBuilder("Sunday"))) {
             days.add(new StringBuilder("Wednesday"));
         }
 
         System.out.println(days.size());
     }
}
What will be the result of compiling and executing Test class?









Explanation
StringBuilder class doesn't override equals(Object) method and hence days.contains(new StringBuilder("Sunday")) returns false. Code inside if-block is not executed and days.size() returns 3.
Question 7: Correct
Consider below code:

//Test.java
public class Test {
     private static boolean flag = !true;
 
     public static void main(String [] args) {
         System.out.println(!flag ? args[0] : args[1]);
     }
}
What will be the result of compiling and executing Test class using below commands?

javac Test.java
java Test AM PM









Explanation
There is no compilation error. When Test class is loaded by JVM to invoked main(String []) method, static variable declaration and initialization statement is executed and false is assigned to flag as !true is false. As java Test AM PM command is used, so args[0] --> "AM" and args[1] --> "PM". In ternary operator, boolean expression is evaluated first, !flag evaluates to true and therefore agrs[0] is returned. AM is printed on to the console.
Question 8: Correct
Consider code of Test.java file:

package com.udayan.oca;
 
public class Test {
     public static void main(String [] args) {
         int [] arr = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
         String str = process(arr, 3, 8); //Line 5
         System.out.println(str);
     }
 
     /*INSERT*/
}
Line 5 is giving compilation error as process method is not found. 

Which of the following method definitions, if used to replace /*INSERT*/, will resolve the compilation error?





Explanation
It is clear from Line 5 that, method name should be process, it should be static method, it should accept 3 parameters (int[], int, int) and its return type must be String.
Question 9: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<String> list = new ArrayList<>();
         list.add("X");
         list.add("Y");
         list.add("X");
         list.add("Y");
         list.add("Z");
         list.remove(new String("Y"));
         System.out.println(list);
     }
}












Explanation
After all the add statements are executed, list contains: [X, Y, X, Y, Z]. list.remove(new String("Y")); removes the first occurrence of "Y" from the list, which means the 2nd element of the list. After removal list contains: [X, X, Y, Z]. NOTE: String class and all the wrapper classes override equals(Object) method, hence at the time of removal when another instance is passes [new String("Y")], there is no issue in removing the matching item.
Question 10: Incorrect
Consider the following interface declaration:

public interface I1 {
    void m1() throws java.io.IOException;
}
Which of the following incorrectly implements interface I1?





Explanation
NOTE: Question is asking for "incorrect" implementation and not "correct" implementation.According to overriding rules, if super class / interface method declares to throw a checked exception, then overriding method of sub class / implementer class has following options:1. May not declare to throw any checked exception, 2. May declare to throw the same checked exception thrown by super class / interface method, 3. May declare to throw the sub class of the exception thrown by super class / interface method, 4. Cannot declare to throw the super class of the exception thrown by super class / interface method
Question 11: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.time.LocalDate;
import java.time.Month;
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<LocalDate> dates = new ArrayList<>();
         dates.add(LocalDate.parse("2018-7-11"));
         dates.add(LocalDate.parse("1919-10-25"));
         dates.add(LocalDate.of(2020, 4, 8));
         dates.add(LocalDate.of(1980, Month.DECEMBER, 31));
 
         dates.removeIf(x -> x.getYear() < 2000);
 
         System.out.println(dates);
     }
}








Explanation
LocalDate.parse(CharSequence) method accepts String in "9999-99-99" format only. Single digit month and day value are padded with 0 to convert it to 2 digits. To represent 9th June 2018, format String must be "2018-06-09". If correct format string is not passed then an instance of java.time.format.DateTimeParseException is thrown. In this question, LocalDate.parse("2018-7-11") throws an exception at runtime.
Question 12: Correct
Which of the following are Java Exception classes? Select 3 options.











Explanation
ClassCastException, NumberFormatException and IllegalArgumentException are Runtime exceptions. There are no exception classes in java with the names: NullException and ArrayIndexException.
Question 13: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
import java.time.Period;
import java.time.format.DateTimeFormatter;
 
public class Test {
     public static void main(String [] args) {
         LocalDate date = LocalDate.of(2012, 1, 11);
         Period period = Period.ofMonths(2);
         DateTimeFormatter formatter = DateTimeFormatter.ofPattern("mm-dd-yy");
         System.out.print(formatter.format(date.minus(period)));
     }
}
What will be the result of compiling and executing Test class?











Explanation
While working with dates, programmers get confused with M & m and D & d. Easy way to remember is that Bigger(Upper case) letters represent something bigger. M represents month & m represents minute, D represents day of the year & d represents day of the month. LocalDate's object doesn't have time component, mm represents minute and not months so at runtime format method throws exception.
Question 14: Incorrect
What is the output if below program is run with the command line:

java Test

public class Test {
     public static void main(String[] args) {
         System.out.println(args.length);
     }
}










Explanation
We have not passed any command-line arguments, hence args refers to an array object of Size 0. args.length prints 0. args is not null and hence no NullPointerException. Also we are not accessing array element so no question of ArrayIndexOutOfBoundsException as well.
Question 15: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String str1 = " ";
         boolean b1 = str1.isEmpty();
         System.out.println(b1);
         str1.trim();
         b1 = str1.isEmpty();
         System.out.println(b1);
     }
}








Explanation
str1 refers to single space character and isEmpty() method of String returns true if no characters are there in the String. As str1 contains single space, hence b1 is false. false is first printed on to the console. str1.trim(); => creates an empty string "" but str1 still refers to single space string " ". b1 = str1.isEmpty(); assigns false to b1 and last System.out.println statement prints false on to the console. So output is:false false
Question 16: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.function.Predicate;
 
class Employee {
     private String name;
     private int age;
     private double salary;
 
     public Employee(String name, int age, double salary) {
         this.name = name;
         this.age = age;
         this.salary = salary;
     }
 
    public String getName() {
         return name;
     }
 
    public int getAge() {
         return age;
     }
 
    public double getSalary() {
         return salary;
     }
 
     public String toString() {
         return name;
     }
}
 
public class Test {
     public static void main(String [] args) {
         List<Employee> list = new ArrayList<>();
         list.add(new Employee("James", 25, 15000));
         list.add(new Employee("Lucy", 23, 12000));
         list.add(new Employee("Bill", 27, 10000));
         list.add(new Employee("Jack", 19, 5000));
         list.add(new Employee("Liya", 20, 8000));
 
         process(list, e -> e.getAge() > 20);
     }
 
     private static void process(List<Employee> list, Predicate<Employee> predicate) {
         Iterator<Employee> iterator = list.iterator();
         while(iterator.hasNext()) {
             Employee e = iterator.next();
             if(predicate.test(e))
                 System.out.print(e + " ");
         }
     }
}
What will be the result of compiling and executing Test class?









Explanation
process(List, Predicate) method prints all the records passing the Predicate's test and test is to process the records having age greater than 20. There are 3 records with age > 20 and these are printed in the insertion order. NOTE: toString() method just returns the name.
Question 17: Correct
Consider below code:

//Guest.java
class Message {
     public static void main(String [] args) {
         System.out.println("Welcome! " + args[1]);
     }
}
 
public class Guest {
     public static void main(String [] args) {
         Message.main(args);
     }
}
And the commands:

javac Guest.java

java Guest James Gosling

What is the result?









Explanation
Both the classes contain special main method. No compilation error with the code: file is correctly names as Guest.java (name of public class). java Guest James Gosling passes new String [] {"James", "Gosling"} to args of Guest.main method. Apart from being special main method, Message.main is static method so Guest.main method invokes Message.main method with the same argument: new String [] {"James", "Gosling"}. args[1] is "Gosling" hence "Welcome! Gosling" gets printed on to the console.
Question 18: Skipped
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.Period;
 
public class Test {
     public static void main(String [] args) {
         Period period = Period.of(2, 1, 0).ofYears(10).ofMonths(5).ofDays(2);
         System.out.println(period);
     }
}
What will be the result of compiling and executing Test class?









Explanation
of and ofXXX methods are static methods and not instance methods. Period.of(2, 1, 0) => returns an instance of Period type. static methods can be invoked using class_name or using reference variable. In this case ofYears(10) is invoked on period instance but compiler uses Period's instance to resolve the type, which is period. A new Period instance {P10Y} is created, after that another Period instance {P5M} is created and finally Period instance {P2D} is created. This instance is assigned to period reference variable and hence P2D is printed on to the console.
Question 19: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<Integer> list = new ArrayList<>();
         list.add(100);
         list.add(200);
         list.add(100);
         list.add(200);
         list.remove(new Integer(100));
 
         System.out.println(list);
     }
}












Explanation
List cannot accept primitives, it can accept objects only. So, when 100 and 200 are added to the list, then auto-boxing feature converts these to wrapper objects of Integer type. So, 4 items gets added to the list: [100, 200, 100, 200]. list.remove(new Integer(100)); removes the first occurrence of 100 from the list, which means the 1st element of the list. After removal list contains: [200, 100, 200]. NOTE: String class and all the wrapper classes override equals(Object) method, hence at the time of removal when another instance is passes[new Integer(100)], there is no issue in removing the matching item.
Question 20: Correct
Which is not a valid statement based on given code?

class A{}
class B extends A{}








Explanation
B b = new A(); -> child class reference cannot refer to parent class object. This will give compilation error.A a = new B(); -> parent class reference can refer to child class object. This is Polymorphism.B a = new B(); -> No issues at all.A a = new A(); -> No issues at all.
Question 21: Incorrect
For the given code fragment:

abstract class Player {
     protected void play() {
 
     }
 
     abstract void run();
}
 
class FootballPlayer extends Player {
     void play() {
 
     }
 
     protected void run() {
 
     }
}
Which 2 modifications, done independently, enable the code to compile?











Explanation
Player class has no compilation error, so no need to change anything in Player class. run() method of Player class is declared with default access modifier, so overriding method in FootballPlayer class must be declared with default, protected or public modifier. run() method of FootballPlayer class is already declared with protected access modifier so there is no issue with this method. play() method of Player class is declared with protected access modifier, so overriding method in FootballPlayer class must be declared with protected or public access modifier. Currently play() method of FootballPlayer class is declared with default access modifier, and hence compilation error. Provide protected or public for play() method of FootballPlayer class.
Question 22: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         StringBuilder sb = new StringBuilder("Java");
         String s1 = sb.toString();
         String s2 = "Java";
 
         System.out.println(s1 == s2);
     }
}








Explanation
toString() method defined in StringBuilder class doesn't use String literal rather uses the constructor of String class to create the instance of String class. So both s1 and s2 refer to different String instances even though their contents are same. s1 == s2 returns false.
Question 23: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         int x = 5;
         while (x < 10) 
             System.out.println(x);
             x++;
     }
}








Explanation
while loop doesn't have curly bracket over here, so only System.out.println(x) belongs to while loop. Above syntax can be written as follows: int x = 5; while (x < 10) { System.out.println(x); } x++; As x++; is outside loop, hence value of x is always 5 within loop, 5 < 10 is true for all the iterations and hence infinite loop.
Question 24: Incorrect
Consider given code:

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String [][] fruits = {{"apple", "mango"}, {"orange", "grape"}};
         /*INSERT*/
     }
}
For the class Test, which options, if used to replace /*INSERT*/, will print "apple mango orange grape " on to the console?





Explanation
Easy question on iterating through 2-dimensional array. Starting index should be 0 and not 1. Enhanced for loop syntax is correct.As for loops contain 1 statement, hence curly brackets can be ignored.
Question 25: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         Boolean b1 = new Boolean("tRuE");
         Boolean b2 = new Boolean("fAlSe");
         Boolean b3 = new Boolean("abc");
         Boolean b4 = null;
         System.out.println(b1 + ":" + b2 + ":" + b3 + ":" + b4);
     }
}










Explanation
Boolean class code uses equalsIgnoreCase method to validate the passed String, so if passed String is "true" ('t', 'r', 'u' and 'e' can be in any case), then boolean value stored in Boolean object is true otherwise false. b1 stores true, b2 stores false, b3 stores false and as b4 is of reference type, hence it can store null as well. Output is: true:false:false:null
Question 26: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
 
public class Test {
     public static void main(String [] args) {
         LocalDate newYear = LocalDate.of(2018, 1, 1);
         LocalDate eventDate = LocalDate.of(2018, 1, 1);
         boolean flag1 = newYear.isAfter(eventDate);
         boolean flag2 = newYear.isBefore(eventDate);
         System.out.println(flag1 + ":" + flag2);
     }
}
What will be the result of compiling and executing Test class?









Explanation
isAfter and isBefore method can be interpreted as: Does 1st Jan 2018 come after 1st Jan 2018? No, false. Does 1st Jan 2018 come before 1st Jan 2018? No, false.
Question 27: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
class Vehicle {
     public int getRegistrationNumber() {
         return 1;
     }
}
 
class Car {
     public int getRegistrationNumber() {
         return 2;
     }
}
 
public class Test {
     public static void main(String[] args) {
         Vehicle obj = new Car();
         System.out.println(obj.getRegistrationNumber());
     }
}








Explanation
class Car doesn't extend from Vehicle class, this means Vehicle is not super type of Car. Hence, Vehicle obj = new Car(); gives compilation error.
Question 28: Correct
What will be the result of compiling and executing Test class?

//Test.java
package com.udayan.oca;
 
class Point {
     static int x;
     int y;
}
 
public class Test {
     public static void main(String[] args) {
         Point p1 = new Point();
         Point p2 = new Point();
         p1.x = 17;
         p1.y = 35;
         p2.x = 19;
         p2.y = 40;
 
         System.out.println(p1.x + ":" + p1.y + ":" + p2.x + ":" + p2.y);
     }
}












Explanation
Variables x and y are declared with default scope, so can be accessed in same package.There is only one copy of static variable for all the instances of the class. Variable x is shared by p1 and p2 both. p1.x = 17; sets the value of variable x to 17, p2.x = 19; overrides the value of variable x to 19. So in System.out.println statement both p1.x and p2.x prints 19. p1.x and p2.x don't give any compilation error but as this syntax creates confusion, so it is not a good practice to access the static variables or static methods using reference variable, instead class name should be used. Point.x is the preferred syntax. Each object has its own copy of instance variables, so p1.y is 35 and p2.y is 40.
Question 29: Incorrect
Consider below code: 

package com.udayan.oca;
 
import java.util.function.Predicate;
 
public class Test {
     public static void main(String[] args) {
         String [] arr = {"A", "ab", "bab", "Aa", "bb", "baba", "aba", "Abab"};
 
         processStringArray(arr, /*INSERT*/);
     }
 
     private static void processStringArray(String [] arr, 
                                                Predicate<String> predicate) {
         for(String str : arr) {
             if(predicate.test(str)) {
                 System.out.println(str);
             }
         }
     }
}
Which of the following options can replace /*INSERT*/ such that on executing Test class all the array elements are displayed in the output? Select ALL that apply.









Explanation
p -> true means test method returns true for the passed String. p -> !false means test method returns true for the passed String. p -> p.length() >= 1 means test method returns true if passed String's length is greater than or equal to 1 and this is true for all the array elements. p -> p.length() < 10 means test method returns true if passed String's length is less than 10 and this is true for all the array elements.
Question 30: Correct
Which of these keywords can be used to prevent inheritance of a class?









Explanation
Class declared as final can't be inherited. Examples are: String, Integer, System etc.
Question 31: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<String> list = new ArrayList<>();
         list.add(0, "Array");
         list.add(0, "List");
 
         System.out.println(list);
     }
}
What will be the result of compiling and executing Test class?











Explanation
list.add(0, "Array"); means list --> [Array], list.add(0, "List"); means insert "List" to 0th index and shift "Array" to right. So after this operation, list --> [List, Array]. In the console, [List, Array] is printed.
Question 32: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String [] args) {
         int a = 2;
         boolean res = false;
         res = a++ == 2 || --a == 2 && --a == 2;
         System.out.println(a);
     }
}








Explanation
a++ == 2 || --a == 2 && --a == 2; [Given expression]. (a++) == 2 || --a == 2 && --a == 2; [Postfix has got higher precedence than other operators]. (a++) == 2 || (--a) == 2 && (--a) == 2; [After postfix, precedence is given to prefix]. ((a++) == 2) || ((--a) == 2) && ((--a) == 2); [== has higher precedence over && and ||]. ((a++) == 2) || (((--a) == 2) && ((--a) == 2)); [&& has higher precedence over ||]. Let's start solving it: ((a++) == 2) || (((--a) == 2) && ((--a) == 2)); [a=2, res=false]. (2 == 2) || (((--a) == 2) && ((--a) == 2)); [a=3, res=false]. true || (((--a) == 2) && ((--a) == 2)); [a=3, res=false]. || is a short-circuit operator, hence no need to evaluate expression on the right. res is true and a is 3.
Question 33: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         System.out.println("Output is: " + (10 != 5));
     }
}








Explanation
"Output is: " + (10 != 5) [Nothing to evaluate at left side, so let's evaluate the right side of +, 10 != 5 is true.] = "Output is: " + true [+ operator behaves as concatenation operator] = "Output is: true"
Question 34: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
 
public class Test {
     public static void main(String [] args) {
         LocalDate d1 = LocalDate.parse("1999-09-09");
         LocalDate d2 = LocalDate.parse("1999-09-09");
         LocalDate d3 = LocalDate.of(1999, 9, 9);
         LocalDate d4 = LocalDate.of(1999, 9, 9);
         System.out.println((d1 == d2) + ":" + (d2 == d3) + ":" + (d3 == d4));
     }
}
What will be the result of compiling and executing Test class?









Explanation
"parse" and "of" methods create new instances, so in this case you get 4 different instance of LocalDate stored at 4 different memory addresses.
Question 35: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
class Message {
     String msg = "Happy New Year!";
 
     public void print() {
         System.out.println(msg);
     }
}
 
public class Test {
     public static void change(Message m) {
         m.msg = "Happy Holidays!";
     }
 
     public static void main(String[] args) {
         Message obj = new Message();
         obj.print();
         change(obj);
         obj.print();
     }
}








Explanation
It is pass-by-reference scheme.Initially, msg = "Happy New Year!"Call to method change(Message) modifies msg property of passed object to "Happy Holidays!"Hence in the output, you get:Happy New Year!Happy Holidays!
Question 36: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
 
     private static void add(double d1, double d2) {
         System.out.println("double version: " + (d1 + d2));
     }
 
     private static void add(Double d1, Double d2) {
         System.out.println("Double version: " + (d1 + d2));
     }
 
     public static void main(String[] args) {
         add(10.0, new Integer(10));
     }
 
}








Explanation
int can be converted to double but Integer type can't be converted to Double type as Integer and Double are siblings (both extends from Number class) so can't be casted to each other. add(10.0, new Integer(10)); => 1st parameter is tagged to double primitive type and 2nd parameter is converted to int, is tagged to double primitive type as well. So, add(double, double); method is invoked.
Question 37: Incorrect
What will be the result of compiling and executing Test class?

//Test.java
package com.udayan.oca;
 
class Parent {
     int i = 10;
     Parent(int i) {
         super();
         this.i = i;
     }
}
 
class Child extends Parent {
     int j = 20;
 
     Child(int j) {
         super(0);
         this.j = j;
     }
 
     Child(int i, int j) {
         super(i);
         this(j);
     }
 
}
 
public class Test {
     public static void main(String[] args) {
         Child child = new Child(1000, 2000);
         System.out.println(child.i + ":" + child.j);
     }
}












Explanation
super(); inside Parent(int) constructor invokes the no-arg constructor of Object class and hence no compilation error for Parent(int) constructor. super(0); inside Child(int) constructor invokes Parent(int) constructor, which is available and hence no issues. Child(int, int) constructor has both super(i) and this(j) statements. A constructor should have super(...) or this(...) but not both. Hence Child(int, int) causes compilation failure. As all the classes are defined in Test.java file under com.udayan.oca.test package, hence child.i and child.j don't give compilation error. i and j are declared with package scope.
Question 38: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String [] arr = new String[7];
         System.out.println(arr);
     }
}








Explanation
Variable arr refers to an array object of String of 7 elements. Variable arr contains the memory address of String array object. arr is of reference type, hence it prints some String Containing @ symbol.
Question 39: Incorrect
Below is the code of Test.java file:

package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String [] args) {
         List<Integer> list = new ArrayList<Integer>();
 
         list.add(27);
         list.add(27);
 
         list.add(new Integer(27));
         list.add(new Integer(27));
 
         System.out.println(list.get(0) == list.get(1));
         System.out.println(list.get(2) == list.get(3));
     }
}
What will be the result of compiling and executing Test class?









Explanation
This is bit tricky. Just remember this:Two instances of following wrapper objects, created through auto-boxing will always be same, if their primitive values are same:Boolean, Byte, Character from \u0000 to \u007f (7f equals to 127), Short and Integer from -128 to 127. For 1st statement, list.add(27); => Auto-boxing creates an integer object for 27. For 2nd statement, list.add(27); => Java compiler finds that there is already an Integer object in the memory with value 27, so it uses the same object. That is why System.out.println(list.get(0) == list.get(1)); returns true. new Integer(27) creates a new Object in the memory, so System.out.println(list.get(2) == list.get(3)); returns false.
Question 40: Correct
Which of the following array declarations and initializations is NOT legal?









Explanation
You can't specify size at the time of initializing with data, hence new int[3]{10, 20, 30}; gives compilation error.
Question 41: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
 
public class Test {
     public static void main(String [] args) {
         LocalDate date = LocalDate.parse("2018-1-01");
         System.out.println(date);
     }
}
What will be the result of compiling and executing Test class?









Explanation
LocalDate.parse(CharSequence) method accepts String in "9999-99-99" format only. Single digit month and day value are padded with 0 to convert it to 2 digits. To represent 9th June 2018, format String must be "2018-06-09". If correct format string is not passed then an instance of java.time.format.DateTimeParseException is thrown.
Question 42: Correct
Choose the options that meets the following specification: 

Create a well encapsulated class Clock with one instance variable model. 

The value of model should be accessible and modifiable outside Clock.





Explanation
Encapsulation is all about having private instance variable and providing public getter and setter methods.
Question 43: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
public class Test {
     public static void main(String[] args) {
         List<String> list = new ArrayList<>();
         list.add("ONE");
         list.add("TWO");
         list.add("THREE");
         list.add("THREE");
 
         if(list.remove(2)) {
             list.remove("THREE");
         }
 
         System.out.println(list);
    }
}
What will be the result of compiling and executing Test class?











Explanation
list.remove(Object) method returns boolean result but list.remove(int index) returns the removed item from the list, which in this case is of String type and not Boolean type and hence if(list.remove(2)) causes compilation error.
Question 44: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
 
class Student {
     private String name;
     private int age;
 
     Student(String name, int age) {
         this.name = name;
         this.age = age;
     }
 
     public String toString() {
         return "Student[" + name + ", " + age + "]";
     }
 
     public boolean equals(Object obj) {
         if(obj instanceof Student) {
             Student stud = (Student)obj;
             if(this.name.equals(stud.name) && this.age == stud.age) {
                 return true;
             }
         }
         return false;
     }
}
 
public class Test {
     public static void main(String[] args) {
         List<Student> students = new ArrayList<>();
         students.add(new Student("James", 25));
         students.add(new Student("James", 27));
         students.add(new Student("James", 25));
         students.add(new Student("James", 25));
 
         students.remove(new Student("James", 25));
 
         for(Student stud : students) {
             System.out.println(stud);
         }
    }
}
What will be the result of compiling and executing Test class?









Explanation
Before you answer this, you must know that there are 5 different Student object created in the memory (4 at the time of adding to the list and 1 at the time of removing from the list). This means these 5 Student objects will be stored at different memory addresses.remove(Object) method removes the first occurrence of matching object and equals(Object) method decides whether 2 objects are equal or not. equals(Object) method has been overridden by the Student class and equates the object based on their name and age.3 matching Student objects are found in the list and 1st list element is removed from the list. Remaining 3 list elements are printed in the insertion order.
Question 45: Correct
How can you force JVM to run Garbage Collector?









Explanation
Both Runtime.getRuntime().gc(); and System.gc(); do the same thing, these make a request to JVM to run Garbage Collector. JVM makes the best effort to run Garbage Collector but nothing is guaranteed. Setting the reference variable to null will make the object eligible for Garbage Collection, if there are no other references to this object. But this doesn't force JVM to run the Garbage Collector. Garbage Collection cannot be forced.
Question 46: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
 
     private static void add(double d1, double d2) {
         System.out.println("double version: " + (d1 + d2));
     }
 
     private static void add(Double d1, Double d2) {
        System.out.println("Double version: " + (d1 + d2));
     }
 
     public static void main(String[] args) {
         add(10.0, null);
     }
 
}








Explanation
add(10.0, null); => Compiler can't convert null to double primitive type, so 2nd argument is tagged to Double reference type. So to match the method call, 10.0 is converted to Double object by auto-boxing and add(10.0, null); is tagged to add(Double, Double); method. But at the time of execution, d2 is null so System.out.println("Double version: " + (d1 + d2)); throws NullPointerException.
Question 47: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
 
public class Test {
     public static void main(String [] args) {
         LocalDate date = LocalDate.parse("1980-03-16");
         System.out.println(date.minusYears(-5));
     }
}
What will be the result of compiling and executing Test class?









Explanation
minusYears, minusMonths, minusWeeks, minusDays methods accept long parameter so you can pass either positive or negative value. If positive value is passed, then that specified value is subtracted and if negative value is passed, then that specified value is added. I think you still remember: minus minus is plus. Similarly plusYears, plusMonths, plusWeeks, plusDays methods work in the same manner. IF positive value is passed, then that specified value is added and if negative value is passed, then that specified value is subtracted.
Question 48: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public String name;
     public void Test() {
         name = "James";
     }
 
     public static void main(String [] args) {
         Test obj = new Test();
         System.out.println(obj.name);
     }
}










Explanation
public void Test() is method and not constructor, as return type is void.method can have same name as the class name, so no issues with Test() method declaration.As there are no constructors available for this class, java compiler adds following constructor.public Test() {}Test obj = new Test(); invokes the default constructor but it doesn't change the value of name property (by default null is assigned to name property)System.out.println(obj.name); prints null.
Question 49: Correct
Consider below code:

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
 
public class Test {
     public static void main(String[] args) {
         ArrayList<Integer> original = new ArrayList<>();
         original.add(new Integer(10));
 
         ArrayList<Integer> cloned = (ArrayList<Integer>) original.clone();
         Integer i1 = cloned.get(0);
         ++i1;
 
         System.out.println(cloned);
     }
}
What will be the result of compiling and executing Test class?









Explanation
Let' suppose: new ArrayList<>() is stored at [15EE00]. new Integer(10) is stored at [25AF06]. original contains memory address of above Integer object. [15EE00] --> {25AF06} Now original.clone() will create a new array list object, suppose at [45BA12] and then it will copy the contents of the ArrayList object stored at [15EE00]. So, cloned contains memory address of the same Integer object. [45BA12] --> {25AF06} In this case, original != cloned, but original.get(0) == cloned.get(0). This means both the array lists are created at different memory location but refer to same Counter object. Integer i1 = cloned.get(0) means, i1 also stores [25AF06]. ++i1; means i1 now refers to another Integer object at different memory location, say [38AB00] and [38AB00] refer to [Integer(11)]. i1 is not assigned back to the list so cloned list stays intact and still contains {25AF06} and in the output you get [10].
Question 50: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String [][] arr = {{"1", "2", "3"}, {"4", "5"}, {"6", "7"}};
         for(int i = 0; i < arr.length; i++) {
             for(int j = 0; j < arr[i].length; j++) {
                 System.out.print(arr[i][j] + " ");
                 if(arr[i][j].equals("2")) {
                     break;
                 }
             }
         }
     }
}








Explanation
arr.length is 3, so outer loop executes 3 times. In 1st execution, i=0. For 1st execution of inner loop, i=0, j=0 and arr[0].length = 3. Inner loop runs for two iterations and breaks after printing "1 2 ". break; statement takes the control out of inner loop. Control goes to step expression (i++) of outer loop, i becomes 1. Inner loop prints "4 5 " on to the console. Outer loop executes one more time and inner loop prints "6 7 " on to the console. Hence output is "1 2 4 5 6 7 ".
Question 51: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
import java.util.function.Predicate;
 
public class Test {
     public static void main(String[] args) {
         String [] arr = {"*", "**", "***", "****", "*****"};
         Predicate pr1 = s -> s.length() < 4;
         print(arr, pr1);
     }
 
     private static void print(String [] arr, Predicate<String> predicate) {
         for(String str : arr) {
             if(predicate.test(str)) {
                 System.out.println(str);
             }
         }
     }
}








Explanation
Though Predicate is a generic interface but raw type is also allowed. Type of the variable in lambda expression is inferred by the generic type of Predicate<T> interface. In this case, Predicate pr1 = s -> s.length() < 4; Predicate is considered of Object type so variable "s" is of Object type and Object class doesn't have length() method. So, s.length() causes compilation error.
Question 52: Incorrect
What will be the result of executing Test class using below command?

java Test good morning everyone

private class Test
{ 
       public static void main(String args[])
       { 
           System.out.println(args[1]);
       }
}








Explanation
Top level class can have two access modifiers: public and default. Over here Test class has private modifier and hence compilation error.
Question 53: Incorrect
Consider codes below:

//A.java
package com.udayan.oca;
 
public class A {
     public int i1;
     protected int i2;
     int i3;
     private int i4;
}
 
//TestA.java
package com.udayan.oca.test;
 
import com.udayan.oca.A; //Line 3
 
public class TestA {
     public static void main(String[] args) {
         A obj = new A(); //Line 7
         System.out.println(obj.i1); //Line 8
         System.out.println(obj.i2); //Line 9
         System.out.println(obj.i3); //Line 10
         System.out.println(obj.i4); //Line 11
     }
}
Which of the following 3 statements are true?













Explanation
class A is declared public and defined in com.udayan.oca package, there is no problem in accessing class A outside com.udayan.oca package. class TestA is defined in com.udayan.oca.test package, to use class A either use import statement "import com.udayan.oca.A;" or fully qualified name of the class com.udayan.oca.A. No issues at Line 3 and LIne 7. As TestA is in different package so it can only access public members of class A using object reference. Line 8 compiles successfully. protected, default and private members are not accessible outside com.udayan.oca package using object reference. NOTE: protected members can be accessed outside but only through inheritance and not object reference.
Question 54: Incorrect
Consider below code: 

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         long l = 100_00l;
         int i = 100;
         float f = 2.02f; 
         double d = 10_0.35d;
         f = l;
         d = l;
         f = d;
         d = f;
         f = i;
         i = f;
         i = (int)d;
     }
}
How many statement(s) cause(s) compilation failure?













Explanation
For readability purpose underscore (_) is used to separate numeric values. This is very useful in representing big numbers such as credit card numbers (1234_7654_9876_0987). long data can be suffixed by l, float by f and double by d. So first 4 variable declaration and assignment statements don't cause any compilation error. long can be easily assigned to float and double type variables, hence no issues with f = l; and d = l;double can't be assigned to float without explicit casting, so f = d; causes compilation error. float can easily be assigned to double and int can easily be assigned to float, so d = f; and f = i; compiles successfully. float can't be assigned to int without explicit casting, so i = f; causes compilation error. double can't be assigned to int without explicit casting, statement i = (int)d; is casting double to int, so no issues.In total, 2 statements are causing compilation error: f = d; and i = f;
Question 55: Correct
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         String fruit = "mango";
         switch (fruit) {
             case "Apple":
                 System.out.println("APPLE");
             case "Mango":
                 System.out.println("MANGO");
             case "Banana":
                 System.out.println("BANANA");
                 break;
             default:
                 System.out.println("ANY FRUIT WILL DO");
         }
     }
}










Explanation
"mango" is different from "Mango", so there is no matching case available. default block is executed and as it is the last block inside switch hence after printing "ANY FRUIT WILL DO" control goes out of switch block, main method ends and program terminates successfully.
Question 56: Incorrect
What will be the result of compiling and executing Test class?

package com.udayan.oca;
 
public class Test {
     private static void m1() throws Exception {
         throw new Exception();
     }
 
     public static void main(String[] args) {
         try {
             m1();
         } finally {
             System.out.println("A");
         }
     }
}








Explanation
Method m1() throws Exception (checked) and it declares to throw it, so no issues with method m1(). But main() method neither provides catch handler nor throws clause and hence main method gives Compilation error. Handle or Declare rule should be followed for checked exception if you are not re-throwing it.
Question 57: Correct
For the class Test, which options, if used to replace /*INSERT*/, will print TEN on to the console? Select 4 options.

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         /*INSERT*/
         switch(var) {
             case 10:
                 System.out.println("TEN");
                 break;
             default:
                 System.out.println("DEFAULT");
         }
     }
}












Explanation
switch can accept primitive types: byte, short, int, char; wrapper types: Byte, Short, Integer, Character; String and enums. In this case long and double are invalid values to be passed in switch expression. char uses 16 bits (2 Bytes) and its range is 0 to 65535 (no signed bit reserved) so it can easily store value 10.
Question 58: Incorrect
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.time.LocalDate;
import java.time.Period;
 
public class Test {
     public static void main(String [] args) {
         LocalDate date = LocalDate.parse("2000-01-01");
         Period period = Period.ofYears(-3000);
         System.out.println(date.plus(period));
     }
}
What will be the result of compiling and executing Test class?











Explanation
The minimum supported LocalDate is: {-999999999-01-01} and maximum supported LocalDate is: {+999999999-12-31}. If period of -3000 years is added to 1st Jan 2000, then result is 1st Jan -1000.
Question 59: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
import java.util.ArrayList;
import java.util.List;
import java.util.ListIterator;
 
public class Test {
     public static void main(String[] args) {
         List<String> dryFruits = new ArrayList<>();
         dryFruits.add("Walnut");
         dryFruits.add("Apricot");
         dryFruits.add("Almond");
         dryFruits.add("Date");
 
         ListIterator<String> iterator = dryFruits.listIterator();
         while(iterator.hasNext()) {
             if(iterator.next().startsWith("A")) {
                 iterator.remove();
              }
         }
 
         System.out.println(dryFruits);
     }
}
What will be the result of compiling and executing Test class?









Explanation
If you want to remove the items from ArrayList, while using Iterator or ListIterator, then use Iterator.remove() or ListIterator.remove() method and NOT List.remove() method. In this case ListIterator.remove() method is used. startsWith("A") returns true for "Apricot" and "Almond" so these elements are removed from the list. In the output, [Walnut, Date] is displayed.
Question 60: Correct
Following statement in a Java program compiles successfully:

student.report(course); 

What can you say for sure?









Explanation
It is good practice to have first character of class name in upper case, but it is not mandatory. student can be either class name or reference variable name. Syntax to invoke static method is: Class_Name.method_name(<arguments>); OR reference_variable_name.method_name(<arguments>); Syntax to invoke instance method is: reference_variable_name.method_name(<arguments>); If student represents class_name or refernce_variable_name, then report might be the static method of the class. If student represents reference_variable_name, then report is the instance method of the class. In both the cases, report must be the method name. Type of argument cannot be found out by looking at above syntax.
Question 61: Correct
Which of the following keywords is used to manually throw an exception?









Explanation
catch is for catching the exception and not throwing it.thrown is not a java keyword.throws is used to declare the exceptions a method can throw.To manually throw an exception, throw keyword is used. e.g., throw new Exception();
Question 62: Incorrect
Consider the code snippet:

import java.util.ArrayList;
import java.util.List;
 
public class Test {
     List list1 = new ArrayList<String>(); //Line 5
     List<String> list2 = new ArrayList(); //Line 6
     List<> list3 = new ArrayList<String>(); //Line 7
     List<String> list4 = new ArrayList<String>(); //Line 8
     List<String> list5 = new ArrayList<>(); //Line 9
}
Which of the following statements compile without any warning?











Explanation
Line 8's syntax was added in JDK 5 and it compiles without any warnings. Line 9's syntax was added in JDK 7, in which type parameter can be ignored from right side of the statement, it is inferred from left side, so Line 9 also compiles without any warning. Type parameter can't be removed from declaration part, hence Line 7 gives compilation error. Both Line 5 and Line 6 are mixing Generic type with Raw type and hence warning is given by the compiler.
Question 63: Correct
What will be the result of compiling and executing the following program?

package com.udayan.oca;
 
import java.io.FileNotFoundException;
import java.io.IOException;
 
abstract class Super {
     public abstract void m1() throws IOException;
}
 
class Sub extends Super {
     @Override
     public void m1() throws IOException {
         throw new FileNotFoundException();
     }
}
 
public class Test {
     public static void main(String[] args) {
         Super s = new Sub();
         try {
             s.m1();
         } catch (IOException e) {
             System.out.print("A");
         } catch(FileNotFoundException e) {
             System.out.print("B");
         } finally {
             System.out.print("C");
         }
     }
}








Explanation
FileNotFoundException extends IOException and hence catch block of FileNotFoundException should appear before the catch block of IOException. Therefore, class Test gives compilation error.
Question 64: Incorrect
Consider the code of Test.java file:

package com.udayan.oca;
 
class Student {
     String name;
     int age;
 
     Student() {
         Student("James", 25);
     }
 
     Student(String name, int age) {
         this.name = name;
         this.age = age;
     }
}
 
public class Test {
     public static void main(String[] args) {
         Student s = new Student();
         System.out.println(s.name + ":" + s.age);
     }
}
What will be the result of compiling and executing Test class?









Explanation
A constructor can call another constructor by using this(...) and not the constructor name. Hence Student("James", 25); gives compilation error.
Question 65: Correct
Consider below code: 

//Test.java
package com.udayan.oca;
 
class Parent {
     public String toString() {
         return "Inner ";
     }
}
 
class Child extends Parent {
     public String toString() {
         return super.toString().concat("Peace!");
     }
}
 
public class Test {
     public static void main(String[] args) {
         System.out.println(new Child());
     }
}
What will be the result of compiling and executing Test class?









Explanation
System.out.println(new Child()); invokes the toString() method on Child's instance. Parent class's method can be invoked by super keyword. super.toString() method returns "Inner " and "Inner ".concat("Peace!") returns "Inner Peace!".
Question 66: Correct
What will be the result of compiling and executing the Test class?

package com.udayan.oca;
 
public class Test {
     public static void main(String[] args) {
         int grade = 75;
         if(grade > 60)
             System.out.println("Congratulations");
             System.out.println("You passed");
         else
             System.out.println("You failed");
     }
}








Explanation
As there is no brackets after if, hence only one statement is part of if block and other is outside. Above code can be written as below: if(grade > 60) { System.out.println("Congratulations"); } System.out.println("You passed"); else System.out.println("You failed"); There should not be anything between if-else block but in this case, System.out.println("You passed"); is between if-else and thus Compilation error.
