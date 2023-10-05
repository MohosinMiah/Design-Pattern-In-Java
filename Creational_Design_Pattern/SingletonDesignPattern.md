# The Singleton design pattern in Java ensures that a class has only one instance and provides a global point of access to that instance. It's used to control the instantiation of a class and restrict it to one single instance throughout the application.

```
public class Singleton {

    private static volatile Singleton instance;

    private Singleton() {
    }

    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}


```