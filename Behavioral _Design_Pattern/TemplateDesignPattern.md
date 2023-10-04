# Template Method Design Pattern Example in Java

The Template Method design pattern is a behavioral design pattern that defines the structure of an algorithm in the base class but lets subclasses override specific steps of the algorithm without changing its structure.

```
public abstract class Beverage {
    // Template method
    public final void prepareBeverage() {
        boilWater();
        brew();
        pourInCup();
        addCondiments();
    }

    // These methods are abstract and will be implemented by concrete subclasses
    protected abstract void brew();
    protected abstract void addCondiments();

    // These methods are common to all beverages and are implemented in the base class
    private void boilWater() {
        System.out.println("Boiling water");
    }

    private void pourInCup() {
        System.out.println("Pouring into cup");
    }
}
```

```
public class Coffee extends Beverage {
    @Override
    protected void brew() {
        System.out.println("Dripping Coffee through filter");
    }

    @Override
    protected void addCondiments() {
        System.out.println("Adding Sugar and Milk");
    }
}

public class Tea extends Beverage {
    @Override
    protected void brew() {
        System.out.println("Steeping the tea");
    }

    @Override
    protected void addCondiments() {
        System.out.println("Adding Lemon");
    }
}
```


```
public class BeverageTest {
    public static void main(String[] args) {
        Beverage coffee = new Coffee();
        Beverage tea = new Tea();

        System.out.println("Making coffee:");
        coffee.prepareBeverage();

        System.out.println("\nMaking tea:");
        tea.prepareBeverage();
    }
}
```