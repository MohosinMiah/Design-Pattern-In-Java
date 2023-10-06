# The Chain of Responsibility design pattern is a behavioral design pattern that allows you to pass requests along a chain of handlers. Each handler decides either to process the request or pass it to the next handler in the chain. 

```
// Define the Handler interface 

public interface Handler {
    void setNextHandler(Handler nextHandler);
    void handleRequest(Request request);
}

```

```
// Create concrete handler classes that implement the Handler interface 

public class ConcreteHandler1 implements Handler {
    private Handler nextHandler;

    @Override
    public void setNextHandler(Handler nextHandler) {
        this.nextHandler = nextHandler;
    }

    @Override
    public void handleRequest(Request request) {
        if (request.getType().equals(RequestType.TYPE1)) {
            System.out.println("Request handled by ConcreteHandler1");
        } else if (nextHandler != null) {
            nextHandler.handleRequest(request);
        }
    }
}

// Create concrete handler classes that implement the Handler interface 

public class ConcreteHandler2 implements Handler {
    private Handler nextHandler;

    @Override
    public void setNextHandler(Handler nextHandler) {
        this.nextHandler = nextHandler;
    }

    @Override
    public void handleRequest(Request request) {
        if (request.getType().equals(RequestType.TYPE2)) {
            System.out.println("Request handled by ConcreteHandler2");
        } else if (nextHandler != null) {
            nextHandler.handleRequest(request);
        }
    }
}

```

```
// Create a Request class 

public class Request {
    private RequestType type;

    public Request(RequestType type) {
        this.type = type;
    }

    public RequestType getType() {
        return type;
    }
}

```

```
// Define an enum for request types 

public enum RequestType {
    TYPE1, TYPE2, TYPE3
}

```

```
// Create a client class to demonstrate the Chain of Responsibility 

public class Client {
    public static void main(String[] args) {
        
        Handler handler1 = new ConcreteHandler1();
        Handler handler2 = new ConcreteHandler2();
        Handler handler3 = new ConcreteHandler3();

        // Set the next handler for each handler in the chain
        handler1.setNextHandler(handler2);
        handler2.setNextHandler(handler3);

        Request request1 = new Request(RequestType.TYPE1);
        handler1.handleRequest(request1);

        Request request2 = new Request(RequestType.TYPE2);
        handler1.handleRequest(request2);

        Request request3 = new Request(RequestType.TYPE3);
        handler1.handleRequest(request3);
    }
}

```