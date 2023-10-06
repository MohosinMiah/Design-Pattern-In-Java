# The Observer pattern is a behavioral design pattern that defines a one-to-many dependency between objects. When one object (the subject) changes its state, all its dependents (observers) are notified and updated automatically.

```

// Subject interface
interface Subject {
    void addObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers();
}

```

```
// Concrete subject
class WeatherStation implements Subject {
    private int temperature;
    private List<Observer> observers = new ArrayList<>();

    public void setTemperature(int temperature) {
        this.temperature = temperature;
        notifyObservers();
    }

    @Override
    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    @Override
    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer   observers) {
            observer.update(temperature);
        }
    }
}

```

```

// Observer interface
interface Observer {
    void update(int temperature);
}

```

```

// Concrete observer
class WeatherDisplay implements Observer {
    @Override
    public void update(int temperature) {
        System.out.println("Temperature is now " + temperature + " degrees Celsius.");
    }
}

```

```
public class Main {
    public static void main(String[] args) {
        WeatherStation weatherStation = new WeatherStation();
        WeatherDisplay weatherDisplay = new WeatherDisplay();

        weatherStation.addObserver(weatherDisplay);

        // Simulate a change in temperature
        weatherStation.setTemperature(25);
    }
}


```