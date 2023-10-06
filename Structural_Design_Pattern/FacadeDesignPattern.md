# The Facade design pattern is a structural design pattern that provides a simplified, unified interface to a set of interfaces or subsystems in a complex system. It hides the complexity of the underlying system and provides a single entry point for clients to interact with the system. Facade simplifies the client's interaction with the system by providing a higher-level interface that abstracts away the low-level details.

# Facade works like a helper method that help to create complex object creation in a simple way to the client. 

```
// AudioSubsystem subsystems
class AudioSubsystem {
    public void start() {
        System.out.println("Audio subsystem started");
    }

    public void stop() {
        System.out.println("Audio subsystem stopped");
    }
}

```

```
// VideoSubsystem subsystems

class VideoSubsystem {
    public void start() {
        System.out.println("Video subsystem started");
    }

    public void stop() {
        System.out.println("Video subsystem stopped");
    }
}

```

```
// ScreenSubsystem subsystems
class ScreenSubsystem {
    public void turnOn() {
        System.out.println("Screen subsystem turned on");
    }

    public void turnOff() {
        System.out.println("Screen subsystem turned off");
    }
}

```

```
// Facade class
class MultimediaFacade {
    private AudioSubsystem audio;
    private VideoSubsystem video;
    private ScreenSubsystem screen;

    public MultimediaFacade() {
        audio = new AudioSubsystem();
        video = new VideoSubsystem();
        screen = new ScreenSubsystem();
    }

    public void startMultimedia() {
        audio.start();
        video.start();
        screen.turnOn();
    }

    public void stopMultimedia() {
        audio.stop();
        video.stop();
        screen.turnOff();
    }
}

```

```
// MultimediaFacade facade
public class Client {
    public static void main(String[] args) {
        MultimediaFacade multimediaFacade = new MultimediaFacade();

        // Starting and stopping multimedia using the facade
        multimediaFacade.startMultimedia();
        System.out.println("Doing some other tasks...");
        multimediaFacade.stopMultimedia();
    }
}

```