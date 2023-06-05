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


## Item 5: Prefer dependency injection to hardwiring resources   

When creating a new instance of a class, instead of hardcoding the dependencies into the constructor,   
pass the dependencies into the constructor. This allows the class to be more flexible, reusable, and testable.

*Benefits of dependency injection*

- Flexibility: Dependency injection allows the class to be configured with different dependencies at runtime. 
This makes the class more flexible and adaptable to different environments.

- Reusability: Dependency injection makes it easier to reuse classes. This is because the dependencies are injected into the class, rather than being hardcoded into the class. This makes the class more independent of its dependencies, and makes it easier to use the class in different contexts.

- Testability: Dependency injection makes it easier to test classes. This is because the dependencies can be mocked or stubbed out in unit tests. This allows the class to be tested in isolation, and without the need for its dependencies.

*When to use dependency injection*

Dependency injection should be used when a class depends on one or more underlying resources whose behavior affects that of the class. For example, a class that depends on a database should use dependency injection to inject the database connection into the constructor. This allows the class to be configured with different databases at runtime, and makes the class more reusable and testable.

Here is an example of how to use dependency injection:
```
public class SpellChecker {

    private final Lexicon dictionary;

    public SpellChecker(Lexicon dictionary) {
        this.dictionary = dictionary;
    }

    public boolean isValid(String word) {
        return dictionary.isValid(word);
    }

}
```
In this example, the `SpellChecker` class depends on a `Lexicon` object. The `Lexicon` object provides the dictionary that the `SpellChecker` class uses to check the validity of words.

The `SpellChecker` class can be configured with different `Lexicon` objects at runtime by passing the `Lexicon` object into the constructor. This allows the `SpellChecker` class to be used with different dictionaries, and makes the class more reusable and testable.

## Item 9: Prefer try-with-resources to try-finally

- the resulting code is shorter and clearer, and the exceptions that it generates are more useful
```
try (MyResource resource = new MyResource()) {
    // Use the resource here.
} catch (Exception e) {
    // Handle the exception here.
}
```
- When i write a class that represents a resource, the class should implement `AutoCloseable` interface
- This will ensure that the resource is closed properly, even if an exception is thrown.
- The try-with-resources statement will automatically call the close() method on the resource, even if an exception is thrown. This helps to prevent resource leaks and makes your code more reliable.


## Item 12: Always override toString

- providing a good `toString` implementation makes your class much more pleasant to use and makes systems using the class easier to debug
- when you decide to specify the format, you should clearly document your intentions
- override Object's toString implementation in every instantiable class you write, unless a superclass has already done so


## Item 14: Minimize the accessibility of classes and members   

- *information hiding* or *encapsulation* is a fundamental tenet of software design
- information hiding is *decouples* the components
- allowing them to be developed, tested, optimized, used, understood and modified in isolation
- make each class or member as inaccessible as possible
- instance fields of public classes should rarely be public
- classes with public mutable fields are not generally thread-safe



	
