# Coding Guidance
**Modularize** your application as much as you can. Use common components, for functions like 
navigation, security, date and time, auditing, logging

**Document** your components and methods as much as you can.

**Write and utilize reusable code** - Avoid using redundant or duplicate code, which can be hard to
 maintain

**Minimize Your Code** - need to think about the best approach you can apply to achieve intended 
functionality.

**Don't Ignore the Exceptions**-In case of exceptions, give a friendly message to the user, but log the 
actual error with all possible details about the error, including the time it occurred, method and class 
name etc. 

**Measure Performance**- At a time of design & writing the code, start analyzing on how the 
performance of this function is, and where is the bottleneck.

**Do write unit test** - Write and perform rigorous unit testing.

**Object-Oriented Design** - Follow guidance available

**Naming Conventions**- Follow standards naming conventions applicable for the language

# Unit Testing Checklist
- [ ] Does each requirement that applies to the class have its own test case?
- [ ] Does each element from the design that applies to the class have its own test case? 
- [ ] Have all defined-used data-flow paths been tested with at least one test case?
- [ ] Has the code been checked for data-flow patterns that are unlikely to be correct, such as defined-defined, defined-exited, and defined-killed?
- [ ] Has a list of common errors been used to write test cases to detect errors that can occur?
- [ ] Have all simple boundaries been tested: maximum, minimum, and off-by-one boundaries?
