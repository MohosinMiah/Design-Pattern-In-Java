# The Abstract Factory design pattern is a creational design pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes. It allows you to ensure that the created objects are compatible and follow a consistent theme or style.

# Example 1

```
// Abstract Factory interface
interface PizzaFactory {
    Pizza createPizza();
}

```

```
// Abstract Product  Pizza
interface Pizza {
    void prepare();
    void bake();
    void cut();
    void box();
}

```

```

// Concrete Product  MargheritaPizza
class MargheritaPizza implements Pizza {
    @Override
    public void prepare() {
        System.out.println("Preparing Margherita Pizza");
    }

    @Override
    public void bake() {
        System.out.println("Baking Margherita Pizza");
    }

    @Override
    public void cut() {
        System.out.println("Cutting Margherita Pizza");
    }

    @Override
    public void box() {
        System.out.println("Boxing Margherita Pizza");
    }
}

```

```

// Concrete Product  PepperoniPizza
class PepperoniPizza implements Pizza {
    @Override
    public void prepare() {
        System.out.println("Preparing Pepperoni Pizza");
    }

    @Override
    public void bake() {
        System.out.println("Baking Pepperoni Pizza");
    }

    @Override
    public void cut() {
        System.out.println("Cutting Pepperoni Pizza");
    }

    @Override
    public void box() {
        System.out.println("Boxing Pepperoni Pizza");
    }
}

```

```

// Concrete Factory  MargheritaPizzaFactory
class MargheritaPizzaFactory implements PizzaFactory {
    @Override
    public Pizza createPizza() {
        return new MargheritaPizza();
    }
}

```

```

// Concrete Factory  PepperoniPizzaFactory
class PepperoniPizzaFactory implements PizzaFactory {
    @Override
    public Pizza createPizza() {
        return new PepperoniPizza();
    }
}

```

```
// Use the PizzaFactory to create and process different types of pizzas 
public class PizzaShop {
    public static void main(String[] args) {
        PizzaFactory margheritaFactory = new MargheritaPizzaFactory();
        Pizza margheritaPizza = margheritaFactory.createPizza();

        PizzaFactory pepperoniFactory = new PepperoniPizzaFactory();
        Pizza pepperoniPizza = pepperoniFactory.createPizza();

        System.out.println("Margherita Pizza ");
        margheritaPizza.prepare();
        margheritaPizza.bake();
        margheritaPizza.cut();
        margheritaPizza.box();

        System.out.println("\nPepperoni Pizza ");
        pepperoniPizza.prepare();
        pepperoniPizza.bake();
        pepperoniPizza.cut();
        pepperoniPizza.box();
    }
}


```