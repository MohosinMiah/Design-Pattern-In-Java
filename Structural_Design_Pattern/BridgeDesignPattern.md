# The Bridge design pattern is a structural design pattern that is used to separate an abstraction (high-level interface or component) from its implementation (low-level details or concrete implementation). It allows these two parts to vary independently, which promotes flexibility, maintainability, and extensibility in your code.

```
// Define the abstraction (high-level interface):

public interface RemoteControl {
    void powerOn();
    void powerOff();
    void volumeUp();
    void volumeDown();
}

```

```
// Create concrete implementations of the abstraction:

public class TVRemoteControl implements RemoteControl {
    private Device device;

    public TVRemoteControl(Device device) {
        this.device = device;
    }

    @Override
    public void powerOn() {
        device.powerOn();
    }

    @Override
    public void powerOff() {
        device.powerOff();
    }

    @Override
    public void volumeUp() {
        device.volumeUp();
    }

    @Override
    public void volumeDown() {
        device.volumeDown();
    }
}

```

```
// Create concrete implementations of the abstraction:

public class RadioRemoteControl implements RemoteControl {
    private Device device;

    public RadioRemoteControl(Device device) {
        this.device = device;
    }

    @Override
    public void powerOn() {
        device.powerOn();
    }

    @Override
    public void powerOff() {
        device.powerOff();
    }

    @Override
    public void volumeUp() {
        device.volumeUp();
    }

    @Override
    public void volumeDown() {
        device.volumeDown();
    }
}

```

```
// Define the implementation interface:

public interface Device {
    void powerOn();
    void powerOff();
    void volumeUp();
    void volumeDown();
}

```

```
// Create concrete implementations of the implementation:

public class Television implements Device {
    private boolean isOn = false;
    private int volume = 50;

    @Override
    public void powerOn() {
        System.out.println("TV is powered on");
        isOn = true;
    }

    @Override
    public void powerOff() {
        System.out.println("TV is powered off");
        isOn = false;
    }

    @Override
    public void volumeUp() {
        if (isOn && volume < 100) {
            volume += 10;
            System.out.println("TV volume increased to " + volume);
        }
    }

    @Override
    public void volumeDown() {
        if (isOn && volume > 0) {
            volume -= 10;
            System.out.println("TV volume decreased to " + volume);
        }
    }
}

```

```
// Create concrete implementations of the implementation:

public class Radio implements Device {
    private boolean isOn = false;
    private int volume = 30;

    @Override
    public void powerOn() {
        System.out.println("Radio is powered on");
        isOn = true;
    }

    @Override
    public void powerOff() {
        System.out.println("Radio is powered off");
        isOn = false;
    }

    @Override
    public void volumeUp() {
        if (isOn && volume < 50) {
            volume += 5;
            System.out.println("Radio volume increased to " + volume);
        }
    }

    @Override
    public void volumeDown() {
        if (isOn && volume > 0) {
            volume -= 5;
            System.out.println("Radio volume decreased to " + volume);
        }
    }
}

```

```
// public class Client {
    public static void main(String[] args) {
        Device tv = new Television();
        Device radio = new Radio();

        RemoteControl tvRemote = new TVRemoteControl(tv);
        RemoteControl radioRemote = new RadioRemoteControl(radio);

        tvRemote.powerOn();
        tvRemote.volumeUp();
        tvRemote.powerOff();

        radioRemote.powerOn();
        radioRemote.volumeUp();
        radioRemote.powerOff();
    }
}

```