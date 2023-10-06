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
// Define a Document interface and its concrete implementations 

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
// Define a Document interface and its concrete implementations 

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

// Abstract creator   Create an abstract DocumentCreator class with a factory method 
abstract class DocumentCreator {
    public abstract Document createDocument();
}

```

```
// Define concrete creator classes that implement the factory method 

class TextDocumentCreator extends DocumentCreator {
    @Override
    public Document createDocument() {
        return new TextDocument();
    }
}

```

```
// Define concrete creator classes that implement the factory method 

class PDFDocumentCreator extends DocumentCreator {
    @Override
    public Document createDocument() {
        return new PDFDocument();
    }
}

```

```
// Use the concrete creators to create documents in your client code 
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