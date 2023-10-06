# The Simple Factory design pattern is a creational design pattern that provides an interface for creating objects but hides the details of their instantiation. It typically involves a factory class with a method for creating objects based on certain conditions or parameters.

```
interface Product {
    void getDescription();
}
```

```
class ConcreteProductA implements Product {
    @Override
    public void getDescription() {
        System.out.println("This is product A.");
    }
}

```

```
class ConcreteProductB implements Product {
    @Override
    public void getDescription() {
        System.out.println("This is product B.");
    }
}

```

```
class ProductFactory {
    public static Product createProduct(String type) {
        if (type.equalsIgnoreCase("A")) {
            return new ConcreteProductA();
        } else if (type.equalsIgnoreCase("B")) {
            return new ConcreteProductB();
        } else {
            throw new IllegalArgumentException("Invalid product type.");
        }
    }
}

```

```

public class Client {
    public static void main(String[] args) {
        Product productA = ProductFactory.createProduct("A");
        Product productB = ProductFactory.createProduct("B");

        productA.getDescription(); // Output  This is product A.
        productB.getDescription(); // Output  This is product B.
    }
}


```