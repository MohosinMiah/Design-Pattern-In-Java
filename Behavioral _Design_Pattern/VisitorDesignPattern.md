# The Visitor design pattern is a behavioral design pattern that allows you to add new behaviors to existing classes without altering their code.

```
// Define the Shape interface 

public interface Shape {
    void accept(Visitor visitor);
}

```

```
// Create concrete shape classes that implement the Shape interface 

public class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double getRadius() {
        return radius;
    }

    @Override
    public void accept(Visitor visitor) {
        visitor.visit(this);
    }
}

public class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    public double getWidth() {
        return width;
    }

    public double getHeight() {
        return height;
    }

    @Override
    public void accept(Visitor visitor) {
        visitor.visit(this);
    }
}

```

```
// Define the Visitor interface 

public interface Visitor {
    void visit(Circle circle);
    void visit(Rectangle rectangle);
}

```

```
// Create concrete visitor classes that implement the Visitor interface for calculating area and perimeter 

public class AreaCalculator implements Visitor {
    private double totalArea = 0;

    @Override
    public void visit(Circle circle) {
        totalArea += Math.PI * circle.getRadius() * circle.getRadius();
    }

    @Override
    public void visit(Rectangle rectangle) {
        totalArea += rectangle.getWidth() * rectangle.getHeight();
    }

    public double getTotalArea() {
        return totalArea;
    }
}

``` 

```
// Create concrete visitor classes that implement the Visitor interface for calculating area and perimeter 

public class PerimeterCalculator implements Visitor {
    private double totalPerimeter = 0;

    @Override
    public void visit(Circle circle) {
        totalPerimeter += 2 * Math.PI * circle.getRadius();
    }

    @Override
    public void visit(Rectangle rectangle) {
        totalPerimeter += 2 * (rectangle.getWidth() + rectangle.getHeight());
    }

    public double getTotalPerimeter() {
        return totalPerimeter;
    }
}

```

```
// Create a client to demonstrate the Visitor pattern 

public class Client {
    public static void main(String[] args) {
        Circle circle = new Circle(5);
        Rectangle rectangle = new Rectangle(4, 6);

        AreaCalculator areaCalculator = new AreaCalculator();
        PerimeterCalculator perimeterCalculator = new PerimeterCalculator();

        circle.accept(areaCalculator);
        rectangle.accept(areaCalculator);

        circle.accept(perimeterCalculator);
        rectangle.accept(perimeterCalculator);

        System.out.println("Total Area  " + areaCalculator.getTotalArea()); // Output  Total Area  74.53981633974483
        System.out.println("Total Perimeter  " + perimeterCalculator.getTotalPerimeter()); // Output  Total Perimeter  32.84955592153876
    }
}

```