# Java Minimal Quickstart

This is a Maven Archetype for starting a minimal Java project.

It includes the following:

- Fixes warnings that Maven generates by default
- Add default application and test files
- Add Junit dependency
- java.version sets on the command line via the property `javaVersion`

## Usage

To create a new Java project using this archetype:

### Build the archetype locally

```console
$ git clone git@github.com:grumpyf0x48/java-minimal-quickstart.git
$ cd java-minimal-quickstart
$ mvn install
```

### Generate a project using the archetype

For example, to create a Java 11 project with the following coordinates: `com.example`, `java11-project`, `0.1-SNAPSHOT`:

```console
$ mvn archetype:generate \
       --batch-mode \
       -DarchetypeGroupId=org.grumpyf0x48 \
       -DarchetypeArtifactId=java-minimal-quickstart \
       -DarchetypeVersion=1.0.0 \
       -DgroupId=com.example \
       -DartifactId=java11-project \
       -Dversion=0.1-SNAPSHOT \
       -DjavaVersion=1.11
```

**Warning**: Property `javaVersion` is mandatory. It will set `java.version` in `pom.xml` of the generated project.

Then, the project looks like:

```console
$ tree java11-project
java11-project
├── pom.xml
└── src
    ├── main
    │   └── java
    │       └── com
    │           └── example
    │               └── Application.java
    └── test
        └── java
            └── com
                └── example
                    └── ApplicationTest.java

9 directories, 3 files
```
