# Java (from 61B)

```java
ArrayMap<String, Integer> am = new ArrayMap<String, Integer>();
...
...
ArrayMap.KeyIterator ami = am.new KeyIterator();
```
In the above, the ```KeyIterator``` class must be associated with a specific ArrayMap. This is because ```KeyIterator``` is a nest class. So in order to instantiate a nest class that is not static, must have instance name before new.


### Packages
A package is a *namespace* that organizes classes and interfaces. Prevents that case where certain classes might have the same method names.
Naming convention: package name starts with website address
```java
package org.junit.*
``` 
refers to junit.org 

In which folder naming convention to access the file is just the name of the package with dots replaced by "/" 

Declare that something is part of the package at the top of the class. Must be contained in the package folder. 

**.jar** files = bundle of **.class** files so other people can use the files. Can access from project sturcture --> artifacts --> .jar. Need to **Build Artifacts...** People can use in their library. Actually like a .zip file! DOES NOT MAKE THE CODE SAFE TO DISTRIBUTE. 

Code without a package declaration is part of the **default package**

Maps are dictionaries. Key values are unique.

**Modules**: a set of methods that work together as a whole to perfom some task or set of related tasks
**Encapsulation**: a module is encapsulated if its implementation is completely hidden -- it can only be accessed through a documented interface

### API & ADT
**API**: Application Programming Interface
* cosists of **syntactic** and **semantic** specification
* compiler verifies syntax is met
* Tests help verify that semantics are correct (what it should do)


**ADT**: Abstract Data Type
example: the API of an ADT is the list of constructors and methods, including an informal description of the effect of each

***Things to think about when designing an API***
* public method or variable: you are saying it should be available **forever**. Don't take it away. ever. it could screw other people over who are using it.
* it's an iterative process


