# WPILib in Zed

I really like the [Zed](zed.dev) code editor. VS Code with WPILib Java is slow on my Mac and regularly drops frames and runs out of memory. Using the Java language server extension, some configuration, and some custom tasks, it feels like a pretty good experience.

## Configure `settings.json`

- Move `settings.json` into `.zed` of your project root
- Change all `~/wpilib/...` paths to the actual path to your install. This is the default Mac install location
