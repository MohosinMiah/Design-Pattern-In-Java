# The Factory Method design pattern is a creational design pattern that defines an interface for creating objects but allows subclasses to alter the type of objects that will be created. It provides a way to delegate the instantiation of objects to subclasses.

# It works look like create a helper method to create the instance of a class

```
// Document interface
interface Document {
    void open();
    void save();
    void close();
}

```

```
// Concrete documents
class TextDocument implements Document {
    @Override
    public void open() {
        System.out.println("Text document is opened.");
    }

    @Override
    public void save() {
        System.out.println("Text document is saved.");
    }

    @Override
    public void close() {
        System.out.println("Text document is closed.");
    }
}

```

```

class PDFDocument implements Document {
    @Override
    public void open() {
        System.out.println("PDF document is opened.");
    }

    @Override
    public void save() {
        System.out.println("PDF document is saved.");
    }

    @Override
    public void close() {
        System.out.println("PDF document is closed.");
    }
}

```

```

// Abstract creator
abstract class DocumentCreator {
    public abstract Document createDocument();
}

```

```
// Concrete creators
class TextDocumentCreator extends DocumentCreator {
    @Override
    public Document createDocument() {
        return new TextDocument();
    }
}

```

```
class PDFDocumentCreator extends DocumentCreator {
    @Override
    public Document createDocument() {
        return new PDFDocument();
    }
}

```

```

public class Client {
    public static void main(String[] args) {
        DocumentCreator textDocumentCreator = new TextDocumentCreator();
        DocumentCreator pdfDocumentCreator = new PDFDocumentCreator();

        Document textDocument = textDocumentCreator.createDocument();
        Document pdfDocument = pdfDocumentCreator.createDocument();

        textDocument.open();
        textDocument.save();
        textDocument.close();

        pdfDocument.open();
        pdfDocument.save();
        pdfDocument.close();
    }
}


```