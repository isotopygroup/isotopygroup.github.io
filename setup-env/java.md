# Java

## Installing JDK

There are three different methods which can be used.
The most recent LTS version (11) will be installed with `apt`, while the most recent version (14) will be installed through IntelliJ.

### Manual Install

To manually install download `tar.gz` file from [OpenJDK](https://openjdk.java.net) and extract to desired directory.
This method will allow the JDK to be used in an IDE (e.g. IntelliJ).
However `java` and `javac` would only work from within the directory without modifying the path variable.

### Apt Install

```bash
sudo apt update
sudo apt install openjdk-11-jdk
```

Install location seems to be `/usr/lib/jvm/`.

### IntelliJ Install

Can install from IntelliJ settings.
Default install location is `~/.jdks`.
