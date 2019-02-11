https://www.hiredintech.com/classrooms/system-design/lesson/55

# Five Steps for the System Design
Step 1.  Constraints and use cases (Requirement & Use Case clarify)
	Clarify the system's constraints and to identify what use cases the system needs to satisfy.
	
Step 2: Abstract design, core system class and overview arch
	 try to address every constraint and use case.
	 
Step 3: Object Interaction Diagram for each user cases. Refine Design in #Step 2 

Step 4: Understanding bottlenecks Or Issues

Step 5: Scaling your abstract design/Close issues

## System design need think about following aspects
- Ease to use
- Flexibility for future changing or demands requirements
- Scalability
- Efficiency
- Different domain system many have different issues need care. For network server, we need think about balance/huge user/etc.


# SOLID principles
https://en.wikipedia.org/wiki/SOLID
- Single responsibility principle
-- a class should have only a single responsibility
- Open/closed principle
-- open for extension, but closed for modification.
- Liskov substitution principle
-- objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.
- Interface segregation principle
-- many client-specific interfaces are better than one general-purpose interface
- Dependency inversion principle
-- depend upon abstractions, [not] concretions
