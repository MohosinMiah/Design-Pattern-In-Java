# The State pattern allows an object to alter its behavior when its internal state changes.

```
public interface State {
    void turnOn();
    void turnOff();
}

public class OnState implements State {
    @Override
    public void turnOn() {
        System.out.println("The light is already on.");
    }

    @Override
    public void turnOff() {
        System.out.println("Turning off the light.");
    }
}

public class OffState implements State {
    @Override
    public void turnOn() {
        System.out.println("Turning on the light.");
    }

    @Override
    public void turnOff() {
        System.out.println("The light is already off.");
    }
}

public class LightSwitch {
    private State state;

    public LightSwitch() {
        state = new OffState();
    }

    public void setState(State state) {
        this.state = state;
    }

    public void turnOn() {
        state.turnOn();
    }

    public void turnOff() {
        state.turnOff();
    }
}

public class Main {
    public static void main(String[] args) {
        LightSwitch lightSwitch = new LightSwitch();

        lightSwitch.turnOn();
        lightSwitch.turnOff();

        lightSwitch.setState(new OnState());
        lightSwitch.turnOn();
        lightSwitch.turnOff();
    }
}

```