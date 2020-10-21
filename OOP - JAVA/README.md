## What is Object Oriented Programming? 
- It uses objects in programming, The main aim of OOP is to bind together the data and the functions that operate on them so that no other part of the code can access this data except that function.
- Concepts including:  Polymorphism , Inheritance , Encapsulation , Abstraction, Class, Object, Instance

##  4 pillars of OOP:
- Abstraction : 
    - In Java, abstraction is achieved using Abstract classes and interfaces.
	- abstraction hiding the implementation details from the user, only the functionality will be provided to the user.
	- Abstract Class: A class which contains the abstract keyword in its declaration
	    - Abstract classes may or may not contain abstract methods, i.e., methods without body
		- if a class has at least one abstract method, then the class must be declared abstract.
		- If a class is declared abstract, it cannot be instantiated.
		- To use an abstract class, you have to inherit it from another class, If you inherit an abstract class, you have to provide implementations to all the abstract methods in it.

- Encapsulation:
	- It is a mechanism of wrapping the data (variables) and code acting on the data (methods) together as a single unit
    - In encapsulation, the variables of a class will be hidden from other classes, and can be accessed only through the methods of their current class. Therefore, it is also known as data hiding.
	- To achieve encapsulation in Java: 
	    - Declare the variables of a class as private.
		- Provide public setter and getter methods to modify and view the variables values.
	- Benefits of Encapsulation
		- The fields of a class can be made read-only or write-only.
		- A class can have total control over what is stored in its fields.

- Polymorphism:
	- It is the ability of an object to take on many forms. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object
	- two types of polymorphism: 
		- Compile time polymorphism (static binding):
			- This type of polymorphism is achieved by function overloading or operator overloading.

					**Overloading**:  when two methods have the same name but differ in the type or number of arguments. 
						public double computeArea(Circle c) { … }
						public double computeArea(Square s) { … } 
					
				□ Functions can be overloaded by change in number of arguments or/and change in type of arguments.
				
		- Runtime polymorphism (dynamic binding)
			-   It is a process in which a function call to the overridden method is resolved at Runtime. 
			- This type of polymorphism is achieved by Method Overriding.
				
					Overriding: when a method shares the same name and function signature as another method in its super class. 
- Inheritance: 
	-  It is the mechanism in java by which one class is allow to inherit the features(fields and methods) of another class.
		-   Super Class: The class whose features are inherited (or a base class or a parent class).
		-   Sub Class: The class that inherits the other class (or a derived class, extended class, or child class). It can has its own fields and methods in addition to the superclass fields and methods
		-   Single Inheritance : In single inheritance, subclasses inherit the features of one superclass
		-   Multilevel Inheritance : In Multilevel Inheritance, a derived class will be inheriting a base class and as well as the derived class also act as the base class to other class
		-   Hierarchical Inheritance : one class serves as a superclass (base class) for more than one sub class

	-   Some drawbacks of classical inheritance: 
        -   Main disadvantage of using inheritance is that the two classes (parent and child class) gets tightly coupled.

## OOP in JAVA: 
- Object Vs Class?
	- Class is a blueprint from which you can create the instance, An object is the instance of the class,
	- Class doesn't allocated memory when it is created. Object allocates memory when it is created. 
	- Class is declared using class keyword, Object is created through new keyword 
    - Class is declared once. Object is created many times as per requirement.
    
- Interface:
	- Interfaces specify what a class must do. It is the blueprint of the class.
	- Methods declared in an interface are by default abstract (only method signature, no body).  
	- If a class implements an interface and does not provide method bodies for the interface, then the class must be declared abstract.
	- Why do we use interface ?
		-   It is allows total abstraction.
		-   it also can achieve multiple inheritance .
		-   It is also used to achieve loose coupling.

- Difference between abstract and interface: 
	- Type of methods: Interface can have only abstract methods. Abstract class can have abstract and non-abstract methods
	- Final Variables: Variables declared in a Java interface are by default final. An abstract class may contain non-final variables.
	- Type of variables: Abstract class can have final, non-final, static and non-static variables. Interface has only static and final variables.
	- Implementation: Abstract class can provide the implementation of interface. Interface can’t provide the implementation of abstract class.
	- Inheritance vs Abstraction: interface can be implemented using keyword “implements” and abstract class can be extended using keyword “extends”.
	- Accessibility of Data Members: Members of a Java interface are public by default. A Java abstract class can have class members like private, protected, etc.

- Difference between 'public' , 'protected', 'private' keywords?
	- Private:
		-   A private member variable or function cannot be accessed, or even viewed from outside the class. Only the class and friend functions can access private members.
	- Protected:
		-   The methods or data members declared as protected are accessible within same package or sub classes in different package.
		-   Private +  one additional benefit that they can be accessed in child classes which are called derived classes.
	- Public: it can be accessed everywhere

-  public static void main 
	- Public: It is an Access modifier, which specifies from where and who can access the method. Making the main() method public makes it globally available
	- Static: It is a keyword which is when associated with a method, makes it a class related method. The main() method is static so that JVM can invoke it without instantiating the class.
	- void: It is a keyword and used to specify that a method doesn’t return anything. 
	- main: It is the name of Java main method. It is the identifier that the JVM looks for as the starting point of the java program.
	- String[] args: It stores Java command line arguments and is an array of type java.lang.String class.

- Keywords static and final for in java?
	- static means  the variable belongs to the class as a whole. When a member is declared static, it can be accessed before any objects of its class are created, and without reference to any object.
		-  variable is declared as static, then a single copy of variable is created and shared among all objects at class level. Static variables are global variables
		-  method is declared with static keyword, it is known as static method. The most common example of a static method is main( ) method. As discussed above, Any static member can be accessed before any objects of its class are created
		
	- Final: is used to control whether a variable, method, or class is "changeable.'
		-   The final statement has a different meaning depending on its context:
			- When applied to a variable (primitive): The value of the variable cannot change
			- When applied to a variable (reference): The reference variable cannot point to any other object on the heap. 
			- When applied to a method in superclass, it cannot be overridden, it cannot be modified by its sub class.
			- When applied to a class: The class cannot be sub classed.
				- Is possible extend a final class: No








 