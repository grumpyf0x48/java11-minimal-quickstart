# Java Minimal Quickstart

[![Java CI](https://github.com/grumpyf0x48/java-minimal-quickstart/actions/workflows/build.yaml/badge.svg)](https://github.com/grumpyf0x48/java-minimal-quickstart/actions/workflows/build.yaml)

This is a Maven Archetype for starting a minimal Java project with Maven.

It adds the following to what was defined in [java9-minimal-quickstart](https://github.com/spilth/java9-minimal-quickstart):

- Add the possibility to set `java.version` on the command line via `javaVersion` property
- Add default `Application.java` and test file `ApplicationTest.java`
- Add Junit 5 dependency
- Add `jacoco-maven-plugin` plugin for code coverage
- Add `maven-enforcer-plugin` and `versions-maven-plugin` plugins for obsolete dependencies handling

## Usage

To create a new Java project using this archetype, you need either:

* [Build the archetype](#build-the-archetype-locally) locally
* [Update Maven configuration](#update-maven-configuration) in `~/.m2/settings.xml` to add the archetype maven repository

Then you can [generate a project](#generate-a-project-using-the-archetype) with the archetype.

### Build the archetype locally

```console
git clone git@github.com:grumpyf0x48/java-minimal-quickstart.git && \
    cd java-minimal-quickstart && \
    ./mvnw install
```

### Update Maven configuration

To include the archetype maven repository, add the following content in `~/.m2/settings.xml`:

```console
$ more ~/.m2/settings.xml

...

  <profiles>
    <profile>
      <id>java-minimal-quickstart</id>
      <repositories>
        <repository>
          <id>java-minimal-quickstart</id>
          <url>https://maven.pkg.github.com/grumpyf0x48/java-minimal-quickstart</url>
          <releases>
            <enabled>true</enabled>
          </releases>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>

  <servers>
    <server>
      <id>java-minimal-quickstart</id>
      <username>${env.GITHUB_ACTOR}</username>
      <password>${env.GITHUB_TOKEN}</password>
    </server>
  </servers>

...

```

Having defined the following environment variables:

* `GITHUB_ACTOR` set to your GitHub username
* `GITHUB_TOKEN` set to a personal access token with 'read:packages' scope

### Generate a project using the archetype

For example, to create a Java **11** project with the following coordinates: `com.example`, `java11-project`, `0.0.1-SNAPSHOT`:

```console
mvn --batch-mode \
    -Pjava-minimal-quickstart \
    -DarchetypeGroupId=org.grumpyf0x48 \
    -DarchetypeArtifactId=java-minimal-quickstart \
    -DarchetypeVersion=0.1-SNAPSHOT \
    -DgroupId=com.example \
    -DartifactId=java11-project \
    -Dversion=0.0.1-SNAPSHOT \
    -Dname="Project Name" \
    -Ddescription="Project Description" \
    -DjavaVersion=11 \
     archetype:generate
```

Property `javaVersion` will set `java.version` in `pom.xml` of the generated project.

Its default value is: **17**.

Properties `version`, `name` and `description` are optional and will be set with default values if not set in the previous command.

Then, the generated project will look like:

```console
$ tree java11-project
java11-project
├── pom.xml
└── src
    ├── main
    │        └── java
    │            └── com
    │                └── example
    │                    └── Application.java
    └── test
        └── java
            └── com
                └── example
                    └── ApplicationTest.java

9 directories, 3 files
```

#### Run the tests

Once `ApplicationTest.java` has no more failing tests:

```console
mvn test
```

#### Check the code coverage

```console
firefox target/site/jacoco/index.html &
```

#### Check obsolete plugins

```console
mvn versions:display-plugin-updates
```

#### Check obsolete dependencies

```console
mvn versions:display-dependency-updates
```
