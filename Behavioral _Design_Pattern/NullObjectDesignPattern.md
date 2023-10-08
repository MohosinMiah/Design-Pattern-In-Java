# 
The Null Object design pattern is a behavioral design pattern that provides an object as a surrogate for the lack of an actual object of a given type. It allows you to avoid explicit null checks and handle the absence of an object gracefully. In essence, it ensures that a valid object is always returned, even when no real object is available, thus preventing null reference exceptions.

```
// Define an interface or an abstract class that represents the behavior you want to provide:

public interface Customer {
    String getName();
    void doSomething();
}

```

```
// Concrete implementation
public class RealCustomer implements Customer {
    private String name;

    public RealCustomer(String name) {
        this.name = name;
    }

    @Override
    public String getName() {
        return name;
    }

    @Override
    public void doSomething() {
        System.out.println("Real Customer is doing something.");
    }
}

```

```
// Create a null object class that also implements the same interface 
public class NullCustomer implements Customer {
    @Override
    public String getName() {
        return "No Customer Available";
    }

    @Override
    public void doSomething() {
        // Do nothing
    }
}

```

```
// Use the null object in cases where an object might be null

public class Client {
    public static void main(String[] args) {
        Customer customer1 = getCustomerByName("Alice");
        Customer customer2 = getCustomerByName("Bob");
        Customer customer3 = getCustomerByName("Unknown");

        customer1.doSomething(); // Real Customer is doing something.
        customer2.doSomething(); // Real Customer is doing something.
        customer3.doSomething(); // No action is performed, as it's a Null Customer.

        System.out.println(customer1.getName()); // Alice
        System.out.println(customer2.getName()); // Bob
        System.out.println(customer3.getName()); // No Customer Available
    }

    public static Customer getCustomerByName(String name) {
        if (name.equals("Alice")) {
            return new RealCustomer(name);
        }
        if (name.equals("Bob")) {
            return new RealCustomer(name);
        }
        return new NullCustomer();
    }
}

```