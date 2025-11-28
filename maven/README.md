# 🚀 Maven Build Tool




## 🧭 **Table of Contents**

1. [What is Maven?](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#what-is-maven)
2. [Why Maven? (Beginner Perspective)](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#why-maven-beginner-perspective)
3. [How Maven Works (High-Level)](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#how-maven-works-high-level)
4. [Maven Installation](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#maven-installation)
5. [Project Structure](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#project-structure)
6. [`pom.xml` Deep Explanation](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#pomxml-deep-explanation)
7. [Maven Build Lifecycle](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#maven-build-lifecycle)
8. [Maven Plugins](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#maven-plugins)
9. [Repositories (Local, Central, Remote)](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#repositories-local-central-remote)
10. [Dependency Management](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#dependency-management)
11. [Profiles](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#profiles)
12. [Common Maven Commands](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#common-maven-commands)
13. [Running Tests](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#running-tests)
14. [Multimodule Projects](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#multimodule-projects)
15. [Maven Wrapper (mvnw)](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#maven-wrapper-mvnw)
16. [Troubleshooting](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#troubleshooting)
17. [Best Practices](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#best-practices)

---

# 1️⃣ What is Maven?

**Maven is a build automation and project management tool for Java.**

It helps developers:

- Build Java projects
- Manage dependencies
- Run tests
- Package applications (JAR/WAR)
- Maintain standard project structure
- Automate repetitive tasks
- Manage multi-module projects

Maven uses an XML-based configuration file called **`pom.xml`** to define everything.

---

# 2️⃣ Why Maven? (Beginner Perspective)

| Without Maven | With Maven |
| --- | --- |
| Manually download libraries | Automatic dependency download |
| Complex build commands | Simple `mvn package` |
| Manual classpath management | Maven manages classpath |
| No standard folder structure | Standard, uniform structure |
| Hard to share projects | Easy to share with POM |

**Maven standardizes Java development across the industry.**

---

# 3️⃣ How Maven Works (High-Level)

1. You write a `pom.xml` → defines project info & dependencies
2. You run a command → `mvn package`
3. Maven downloads required dependencies
4. It executes build lifecycle phases
5. Produces output (JAR/WAR)

**Everything is plugin-based.**

---

# 4️⃣ Maven Installation

### 1. Install Java (JDK)

```bash
java -version
```

### 2. Install Maven

Download: [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi)

### 3. Verify installation

```bash
mvn -v
```

---

# 5️⃣ Project Structure

Maven follows a standard directory layout:

```
my-app/
 ├── src/
 │   ├── main/
 │   │   ├── java/          # Application source
 │   │   ├── resources/     # Config files
 │   └── test/
 │       ├── java/          # Test cases
 ├── target/                 # Compiled output
 ├── pom.xml                 # Project Object Model file
```

---

# 6️⃣ `pom.xml` Deep Explanation

Your project's **blueprint**.

### ✔️ Minimal Example

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>my-app</artifactId>
    <version>1.0.0</version>

</project>
```

---

## ✔️ Important Fields Explained

### **`groupId`**

- Organization / project namespace
- Example: `com.company.project`

### **`artifactId`**

- Project name
- Example: `payment-service`

### **`version`**

Semantic version like:

```
MAJOR.MINOR.PATCH
```

### **`packaging`**

Defines output type:

| Type | Purpose |
| --- | --- |
| `jar` | Java libraries |
| `war` | Web apps |
| `pom` | Parent/multimodule project |

Defaults to `jar`.

---

## ✔️ Add Dependencies

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-core</artifactId>
        <version>5.3.30</version>
    </dependency>
</dependencies>
```

---

## ✔️ Dependency Scopes

| Scope | Meaning |
| --- | --- |
| **compile** | default, available everywhere |
| **provided** | provided by container (Tomcat, JDK) |
| **runtime** | needed only at runtime |
| **test** | only for testing |
| **system** | local JAR (rare) |

---

## ✔️ Build Section

Used to configure plugins.

Example:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.10.1</version>
            <configuration>
                <source>17</source>
                <target>17</target>
            </configuration>
        </plugin>
    </plugins>
</build>
```

---

# 7️⃣ Maven Build Lifecycle

Maven has 3 main lifecycles:

---

## ⭐ **1. Clean Lifecycle**

| Phase | Description |
| --- | --- |
| `clean` | Deletes `target/` |

---

## ⭐ **2. Default (Build) Lifecycle**

Most important.

| Phase | Purpose |
| --- | --- |
| `validate` | Check structure |
| `compile` | Compile source code |
| `test` | Run unit tests |
| `package` | Create JAR/WAR |
| `verify` | Check package |
| `install` | Install JAR to local repo |
| `deploy` | Deploy to remote repo |

---

## ⭐ **3. Site Lifecycle**

Generates documentation.

---

## ✔️ Running Lifecycle Phases

```bash
mvn compile
mvn package
mvn test
mvn install
```

Running a phase runs **all previous phases automatically**.

Example:

`mvn package` will run:

```
validate → compile → test → package
```

---

# 8️⃣ Maven Plugins

Everything in Maven is powered by **plugins**.

### Common Plugins

| Plugin | Purpose |
| --- | --- |
| `maven-compiler-plugin` | Compile Java |
| `maven-surefire-plugin` | Run tests |
| `maven-jar-plugin` | Build JAR |
| `maven-war-plugin` | Build WAR |
| `maven-install-plugin` | Install to local repo |

---

# 9️⃣ Repositories (Local, Central, Remote)

### ✔️ Local Repository

Stored at:

```
~/.m2/repository
```

### ✔️ Central Repository

Default global repository maintained by Apache Maven.

### ✔️ Remote/Company Repos

Example: Nexus, Artifactory.

---

# 🔟 Dependency Management

### ✔️ View dependencies

```bash
mvn dependency:tree
```

### ✔️ Exclude transitive dependencies

```xml
<dependency>
    <groupId>org.example</groupId>
    <artifactId>app</artifactId>
    <version>1.0.0</version>
    <exclusions>
        <exclusion>
            <groupId>commons-logging</groupId>
            <artifactId>commons-logging</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```

---

# 1️⃣1️⃣ Profiles

Profiles allow different builds for different environments.

Example:

```xml
<profiles>
    <profile>
        <id>dev</id>
        <properties>
            <env>development</env>
        </properties>
    </profile>

    <profile>
        <id>prod</id>
        <properties>
            <env>production</env>
        </properties>
    </profile>
</profiles>
```

Run:

```bash
mvn package -Pdev
mvn package -Pprod
```

---

# 1️⃣2️⃣ Common Maven Commands

### Build

```bash
mvn package
mvn install
```

### Tests

```bash
mvn test
```

### Clean

```bash
mvn clean
```

### View dependencies

```bash
mvn dependency:tree
```

### Skip tests

```bash
mvn package -DskipTests
```

---

# 1️⃣3️⃣ Running Tests

Maven uses **Surefire Plugin**.

- Test files must follow naming:

```
*Test.java
Test*.java
```

Run tests:

```bash
mvn test
```

---

# 1️⃣4️⃣ Multimodule Projects

Useful for microservices or layered Java projects.

**Parent project `pom.xml`:**

```xml
<packaging>pom</packaging>

<modules>
    <module>service-api</module>
    <module>service-impl</module>
</modules>
```

Each module has its own `pom.xml`.

---

# 1️⃣5️⃣ Maven Wrapper (mvnw)

Wrapper ensures everyone uses same Maven version.

Generate wrapper:

```bash
mvn -N io.takari:maven:wrapper
```

Run:

```bash
./mvnw clean install
```

---

# 1️⃣6️⃣ Troubleshooting

### ❗ Clean everything

```bash
mvn clean install
```

### ❗ Delete corrupted local repo files

```bash
rm -rf ~/.m2/repository
```

### ❗ Enable debug logs

```bash
mvn -X package
```

### ❗ Skip tests

```bash
mvn package -DskipTests
```

---

# 1️⃣7️⃣ Best Practices

- ✔ Follow Maven standard folder structure
- ✔ Always define versions explicitly
- ✔ Keep dependencies minimal
- ✔ Use dependency management for versions
- ✔ Use profiles for environments
- ✔ Don’t hardcode paths in POM
- ✔ Prefer Maven Wrapper (`mvnw`)
- ✔ Keep modules small and clean

---