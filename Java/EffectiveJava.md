# Effective Java : Third Edition   

## Item 2: Consider a builder when faced with many constructor parameters

- tranditionally the programmers have used *telescoping constructor pattern*
	- it's hard to read, hard to write, possibility to make a mistake
- the second option is *java bean pattern*
	- create parameterless constructor
	- then call setter methods to set parameters
	- cons:
		- precludes possibility of making a class immutable
- the third option is *builer pattern*
	- safety of telescoping pattern + readability of java bean pattern
	- well suited to class hierarchies
	- disadvantages:
		- must first create its builder
		- it could be a problem in performance-critical situations
		- more verbose than the telescoping pattern
