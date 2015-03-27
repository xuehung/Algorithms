## Overriding and Hidding Methods
[Ref](https://docs.oracle.com/javase/tutorial/java/IandI/override.html)
 - An instance method in a subclass with the same signature *overrides* the superclass's method.
 - If a subclass defines a static method with the same signature as a static method in the superclass, then the method in the subclass *hides* the one in the superclass.

```Java

public class Animal {
    public static void testClassMethod() {
        System.out.println("The static method in Animal");
    }
    public void testInstanceMethod() {
        System.out.println("The instance method in Animal");
    }
}

public class Cat extends Animal {
    public static void testClassMethod() {
        System.out.println("The static method in Cat");
    }
    public void testInstanceMethod() {
        System.out.println("The instance method in Cat");
    }

    public static void main(String[] args) {
        Cat myCat = new Cat();
        Animal myAnimal = myCat;
        Animal.testClassMethod();
        // The static method in Animal

        myAnimal.testInstanceMethod();
        // The instance method in Cat
    }
}
```

### Interface Methods
 - Instance methods are preferred over interface default methods.
 - Methods that are already overridden by other candidates are ignored. This circumstance can arise when supertypes share a common ancestor

### Summary
|| *Superclass Instance Method* | *Superclass Static Method* |
|-----| ------------- | ------------- |
| *Subclass Instance Method* | Overrides | compile-time error |
| *Subclass Static Method* | compile-time error | Hides |


---

### Default keyword
