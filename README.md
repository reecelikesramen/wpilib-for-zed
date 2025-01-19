# WPILib in Zed

I really like the [Zed](zed.dev) code editor. VS Code with WPILib Java is slow on my Mac and regularly drops frames and runs out of memory. Using the Java language server extension, some configuration, and some custom tasks, it feels like a pretty good experience.

## Configure Settings

- Move `settings.json` into `.zed` of your project root.
- Change all `~/wpilib/...` paths to the actual path to your install. This is the default Mac install location.

## Tasks

- Move `tasks.json` into `.zed` of your project root.
- No other configuration is necessary.

## AdvantageKit Support

Team 2220 uses AdvantageKit this year for logging and I have added some custom tasks to make it easier to simulate and replay.

- Move `./advantagekit/tasks.json` into `.zed` of your project root.
- Set the `SIM_MODE` constant to be driven by `AKIT_SIM_MODE` environment variable. Here's what I use:
  ```java
  /* This gets the value of environment variable AKIT_SIM_MODE otherwise sets SIM_MODE to Mode.SIM */
  public static final Mode SIM_MODE =
      Optional.ofNullable(System.getenv("AKIT_SIM_MODE")).map(Mode::valueOf).orElse(Mode.SIM);
  ```
- Optionally, in `build.gradle`, set the GUI enabled state of the simulator to be driven by `AKIT_SIM_MODE` environment variable. Here's what I used:
  ```groovy
  // Simulation configuration (e.g. environment variables).
  wpi.sim.addGui().defaultEnabled = providers.environmentVariable('AKIT_SIM_MODE').map(env -> env.equals("SIM")).orElse(true)
  wpi.sim.addDriverstation()
  ```
