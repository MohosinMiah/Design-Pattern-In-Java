# The Decorator design pattern is a structural design pattern that allows you to add behavior or responsibilities to objects dynamically at runtime. It is achieved by creating a set of decorator classes that are used to wrap concrete components. Decorators enhance the functionality of objects without altering their structure.

```
// Define a common interface for text formatting

public interface Text {
    String format();
}

```

```
// Create a concrete text class that implements the Text interface

public class PlainText implements Text {
    private String content;

    public PlainText(String content) {
        this.content = content;
    }

    @Override
    public String format() {
        return content;
    }
}

```

```
//  Create decorator classes that also implement the Text interface to add formatting

public abstract class TextDecorator implements Text {
    protected Text decoratedText;

    public TextDecorator(Text decoratedText) {
        this.decoratedText = decoratedText;
    }

    @Override
    public String format() {
        return decoratedText.format();
    }
}

```

```
public class BoldTextDecorator extends TextDecorator {
    public BoldTextDecorator(Text decoratedText) {
        super(decoratedText);
    }

    @Override
    public String format() {
        return "<b>" + super.format() + "</b>";
    }
}

```

```
public class ItalicTextDecorator extends TextDecorator {
    public ItalicTextDecorator(Text decoratedText) {
        super(decoratedText);
    }

    @Override
    public String format() {
        return "<i>" + super.format() + "</i>";
    }
}

```

```
//  Decorator pattern to format text
public class Client {
    public static void main(String[] args) {
        Text plainText = new PlainText("Hello, Decorator Pattern!");

        Text boldText = new BoldTextDecorator(plainText);
        Text italicText = new ItalicTextDecorator(plainText);
        Text boldItalicText = new BoldTextDecorator(new ItalicTextDecorator(plainText));

        System.out.println("Plain Text: " + plainText.format());
        System.out.println("Bold Text: " + boldText.format());
        System.out.println("Italic Text: " + italicText.format());
        System.out.println("Bold Italic Text: " + boldItalicText.format());
    }
}

```