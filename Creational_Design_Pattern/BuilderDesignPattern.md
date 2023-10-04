# The Builder design pattern is a creational design pattern used to construct complex objects step by step. It separates the construction of a complex object from its representation, allowing the same construction process to create different representations. The pattern is particularly useful when you have a complex object with many optional parameters.



```
// Define the Pizza class:

public class Pizza {
    private String dough;
    private String sauce;
    private String cheese;
    private boolean pepperoni;
    private boolean mushrooms;
    private boolean onions;

    private Pizza(Builder builder) {
        this.dough = builder.dough;
        this.sauce = builder.sauce;
        this.cheese = builder.cheese;
        this.pepperoni = builder.pepperoni;
        this.mushrooms = builder.mushrooms;
        this.onions = builder.onions;
    }

    public static class Builder {
        private String dough;
        private String sauce;
        private String cheese;
        private boolean pepperoni;
        private boolean mushrooms;
        private boolean onions;

        public Builder(String dough, String sauce) {
            this.dough = dough;
            this.sauce = sauce;
        }

        public Builder cheese(String cheese) {
            this.cheese = cheese;
            return this;
        }

        public Builder pepperoni(boolean pepperoni) {
            this.pepperoni = pepperoni;
            return this;
        }

        public Builder mushrooms(boolean mushrooms) {
            this.mushrooms = mushrooms;
            return this;
        }

        public Builder onions(boolean onions) {
            this.onions = onions;
            return this;
        }

        public Pizza build() {
            return new Pizza(this);
        }
    }

    @Override
    public String toString() {
        return "Pizza with " + dough + " dough, " + sauce + " sauce, " + cheese + " cheese, " +
                (pepperoni ? "with pepperoni, " : "") +
                (mushrooms ? "with mushrooms, " : "") +
                (onions ? "with onions, " : "") +
                "baked to perfection!";
    }
}


```

```
// Create a client program to build different types of pizzas:

public class PizzaBuilderExample {
    public static void main(String[] args) {
        Pizza pizza1 = new Pizza.Builder("Thin Crust", "Tomato")
                .cheese("Mozzarella")
                .pepperoni(true)
                .mushrooms(true)
                .build();

        Pizza pizza2 = new Pizza.Builder("Thick Crust", "BBQ")
                .cheese("Cheddar")
                .onions(true)
                .build();

        System.out.println(pizza1);
        System.out.println(pizza2);
    }
}

```