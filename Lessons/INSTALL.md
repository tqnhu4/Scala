Installing Scala is a straightforward process, but it requires having the Java Development Kit (JDK) already set up on your system, as Scala runs on the Java Virtual Machine (JVM).

-----

## 💻 Step 1: Install Java Development Kit (JDK)

First, ensure you have a compatible **JDK** installed. Scala 2.13 and newer typically work best with **JDK 8 or later** (JDK 11 or 17 are good choices).

1.  **Check if Java is installed:**
    Open your terminal or command prompt and type:

    ```bash
    java -version
    javac -version
    ```

    If you see version information, Java is likely installed. If not, proceed to step 2.

2.  **Download and Install JDK:**

      * Go to the official Oracle JDK download page or OpenJDK distributions like Adoptium (Eclipse Temurin).
      * Download the appropriate installer for your operating system (Windows, macOS, Linux).
      * Follow the installation instructions for your specific OS. On Windows, this usually involves running an executable. On macOS, it might be a `.dmg` file. On Linux, you might use your package manager (e.g., `sudo apt install openjdk-17-jdk` for Ubuntu).

3.  **Set JAVA\_HOME (if needed):**
    After installation, you might need to set the `JAVA_HOME` environment variable, though many installers do this automatically.

      * **Windows:** Search for "Environment Variables," click "Environment Variables," and then "New" under "System variables." Set `Variable name` to `JAVA_HOME` and `Variable value` to your JDK installation path (e.g., `C:\Program Files\Java\jdk-17`). Also, ensure `%JAVA_HOME%\bin` is in your `Path` variable.
      * **macOS/Linux:** Add the following to your `~/.bash_profile`, `~/.zshrc`, or `~/.bashrc` file (adjust the path to your JDK version):
        ```bash
        export JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk-17.0.2.jdk/Contents/Home" # Example path for macOS
        export PATH=$JAVA_HOME/bin:$PATH
        ```
        Then, run `source ~/.bash_profile` (or your respective file) to apply changes.

4.  **Verify JDK Installation:**
    Restart your terminal or command prompt and run `java -version` and `javac -version` again. You should now see the version numbers.

-----

## 🛠️ Step 2: Install Scala

Once JDK is ready, you can install Scala. There are a few common ways:

### Option A: Using Coursier (Recommended for most users)

Coursier is a dependency manager and launcher that makes it easy to install Scala tools.

1.  **Install Coursier:**

      * **macOS (with Homebrew):**
        ```bash
        brew install coursier/formulas/coursier
        ```
      * **Linux/WSL:**
        ```bash
        curl -fL https://get.coursier.app/cs | bash
        ```
      * **Windows:**
        ```powershell
        Invoke-WebRequest -Uri https://get.coursier.app/cs.ps1 -OutFile coursier.ps1
        .\coursier.ps1
        ```
        Follow the prompts; this will add `cs` to your Path.

2.  **Install Scala and SBT with Coursier:**
    Once Coursier is installed, you can use it to install the Scala command-line tools and **SBT (Scala Build Tool)**.

    ```bash
    cs install scala scalac sbt
    ```

    This command downloads and installs the latest stable versions of Scala's compiler (`scalac`), the Scala REPL (`scala`), and SBT.

### Option B: Manual Installation (Less common, but provides more control)

If you prefer to manually download and set up Scala:

1.  **Download Scala:**

      * Go to the official Scala download page: [https://www.scala-lang.org/download/](https://www.scala-lang.org/download/)
      * Download the **ZIP or TGZ archive** for your operating system.

2.  **Extract the Archive:**

      * Extract the downloaded archive to a directory of your choice (e.g., `C:\scala` on Windows, `/opt/scala` or `/usr/local/scala` on Linux/macOS).

3.  **Set SCALA\_HOME and Update PATH:**

      * **Windows:** Add a new system variable `SCALA_HOME` pointing to your Scala installation directory (e.g., `C:\scala-2.13.12`). Then, add `%SCALA_HOME%\bin` to your system `Path` variable.
      * **macOS/Linux:** Add the following to your `~/.bash_profile`, `~/.zshrc`, or `~/.bashrc` file (adjust the path and version):
        ```bash
        export SCALA_HOME="/usr/local/scala-2.13.12" # Example path
        export PATH=$SCALA_HOME/bin:$PATH
        ```
        Then, run `source ~/.bash_profile` (or your respective file).

### Option C: Using a Package Manager (Platform-specific)

  * **macOS (with Homebrew):**
    ```bash
    brew install scala
    brew install sbt # Also install SBT
    ```
  * **Linux (e.g., Ubuntu/Debian):**
    You can often install via `apt` (though versions might not be the latest):
    ```bash
    sudo apt update
    sudo apt install scala
    sudo apt install sbt # Also install SBT
    ```
    For the latest versions, using Coursier is generally preferred on Linux.

-----

## ✅ Step 3: Verify Scala Installation

After installation (regardless of the method), open a **new** terminal or command prompt and run:

```bash
scala -version
scalac -version
sbt sbtVersion
```

You should see output similar to this, indicating that Scala, the Scala compiler, and SBT are correctly installed and accessible:

```
Scala code runner version 2.13.12 -- Copyright 2002-2023, LAMP/EPFL
Scala compiler version 2.13.12 -- Copyright 2002-2023, LAMP/EPFL
[info] 1.9.8
```

Now you're ready to start coding in Scala\! You can open the Scala REPL by typing `scala` in your terminal, or create an SBT project to build more complex applications.