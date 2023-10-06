# The Adapter design pattern is a structural design pattern that allows the interface of an existing class to be used as another interface. It is often used to make existing classes work with others without modifying their source code. Essentially, it acts as a bridge between two incompatible interfaces.

# The Adapter design pattern in Java is a structural design pattern that allows objects with incompatible interfaces to work together. It acts as a bridge between two incompatible interfaces, enabling them to collaborate seamlessly. This pattern is particularly useful when you want to reuse existing classes or libraries with different interfaces without modifying their source code.

```
public interface OldSystem {
    void request();
}

```

```

public class OldSystemImpl implements OldSystem {
    @Override
    public void request() {
        System.out.println("OldSystemImpl is processing the request.");
    }
}

```


```
public interface NewSystem {
    void newRequest();
}

```

```
public class OldSystemAdapter implements NewSystem {
    private OldSystem oldSystem;

    public OldSystemAdapter(OldSystem oldSystem) {
        this.oldSystem = oldSystem;
    }

    @Override
    public void newRequest() {
        oldSystem.request();
    }
}

```

```

public class Client {
    public static void main(String[] args) {
        OldSystem oldSystem = new OldSystemImpl(); // Existing OldSystem
        NewSystem adapter = new OldSystemAdapter(oldSystem);

        adapter.newRequest(); // Calls the oldSystem.request() through the adapter
    }
}

```