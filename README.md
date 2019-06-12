>The site just my Java Study recording. If any people have advice please let me know. Great thanks

I will update it everyday for Java skill improvement.
Reference Book: Thinking Java & Core java Made simple in books24x7

[Basic java Core]() | [Java 多线程]()
---- | --- 
## Varargs parameter
The three dots can only be used in a method argument, and are called 'varargs'. It means you can pass in an array of parameters without explicitly creating the array.
```
private void method(String... args) {}
```

## Java Object Initialization/Finalizer
1) JVM will create a default constructor if code doesn't define one
2) Static initial block will be called before constructor. One class can have multiple initial blocks
3) Java static variables will be ininitialized to default value.
4) Garbage collection cannot make sure finalize called on time. 
5) Java 7 introduced try-with-resources & AutoCloseable interface to free the resource automatically.
## Java Object common Methond
1) Clone need avoid final member. because final have issue to reassign
2) Clone need avoid call supper clone, or else will share some data user don't want share.
3) Clone can be better with copy constructor like C++. 
4) == Reflexive/Symmetric/Transitive/Consistent, equals(null) always return false.

### Visibility
|Modifier   | Package     | Subclass    | Everyone Else |
| ------    | ----------- | ----------- | ----------- |
| public    | accessible  |accessible   | accessible  |
| protected | accessible  | accessible  | not accessible|
| no modifier | accessible | not accessible | not accessible |
| private   | not accessible | not accessible | not accessible |

## Java Interface
1) Interface include nested interfaces, classes, enumerations, annotations
2) Every declaration is public
3) Method is abstract
4) Const field is implicitly static and final
5) Nested interfaces/classes/emumeration is public and static
6) Marker interface (Clonable & Serializable)

## Final variable
It is not necessary to initialize the value of final variable at the time of declaration. It can be initialized at the time of declaration, With the help of block OR initialize it by using constructor.

##Java basic study
BOOK Thinking Java
Advanced Java http://enos.itcollege.ee/~jpoial/allalaadimised/reading/Advanced-java.pdf

##Java Interview questions
https://www.edureka.co/blog/interview-questions/java-interview-questions/

#Course Links
https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/

https://courses.edx.org Introduction to Theoretical Computer Science 

# JUnit inside
https://www.ibm.com/developerworks/cn/java/j-lo-junit-src/index.html

# Java FW
## Akka
https://www.youtube.com/watch?v=lPTqcecwkJg

#
InterviewCake
https://www.hiredintech.com/classrooms/system-design/lesson/60
https://www.educative.io/collection/5642554087309312/5679846214598656
https://www.reddit.com/r/cscareerquestions/comments/1jov24/heres_how_to_prepare_for_tech_interviews/

