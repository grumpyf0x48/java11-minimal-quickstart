# Java Minimal Quickstart

This is a Maven Archetype for starting a minimal Java project.

It includes the following:

- Fixes warnings that Maven generates by default
- Add Junit dependency
- Add default Application and test files
- java.version sets on the command line

# Usage

To create a new Java project using this archetype:

```console
$ mvn archetype:generate \
       --batch-mode \
       -DarchetypeGroupId=org.grumpyf0x48 \
       -DarchetypeArtifactId=java11-minimal-quickstart \
       -DarchetypeVersion=1.0.0 \
       -DgroupId=com.example \
       -DartifactId=new-java11-project \
       -Dversion=0.1-SNAPSHOT \
       -DjavaVersion=1.11
```

Warning: Property `javaVersion` is mandatory. It will set `java.version` in `pom.xml` of the generated project.

```console
$ tree new-java11-project
new-java11-project
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

```console
$ mvn package
```
