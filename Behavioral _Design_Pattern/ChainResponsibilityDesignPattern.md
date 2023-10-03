# The Chain of Responsibility design pattern is a behavioral design pattern that allows you to pass requests along a chain of handlers. Each handler decides either to process the request or pass it to the next handler in the chain. 

```

public interface Handler {
    void setNextHandler(Handler nextHandler);
    void handleRequest(Request request);
}

```

```

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

public enum RequestType {
    TYPE1, TYPE2, TYPE3
}

```

```

public class Client {
    public static void main(String[] args) {
        Handler handler1 = new ConcreteHandler1();
        Handler handler2 = new ConcreteHandler2();

        handler1.setNextHandler(handler2);

        Request request1 = new Request(RequestType.TYPE1);
        handler1.handleRequest(request1);

        Request request2 = new Request(RequestType.TYPE2);
        handler1.handleRequest(request2);

        Request request3 = new Request(RequestType.TYPE3);
        handler1.handleRequest(request3);
    }
}

```