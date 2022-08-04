## Creating a Project
```sh
mvn archetype:generate \
  -DgroupId=com.mycompany.app \
  -DartifactId=my-app \
  -DarchetypeArtifactId=maven-archetype-quickstart \
  -DarchetypeVersion=1.4 \
  -DinteractiveMode=false
```
### Compile, package and run project
```sh
mvn clean package
java -jar target/MavenProject-1.0.jar 
```

## How to use a specific version of Java in Maven
We can check the default JDK version of Maven. Running the mvn -v command will show the Java version in which Maven runs.

### Method 1: Change the JAVA_HOME path
Maven uses the JAVA_HOME environment variable to find which Java version it is supposed to run. If a different version of Java is needed, set the JAVA_HOME to the path of the specific version of JDK.

For example, if Java 8 is needed:
```sh
JAVA_HOME=/usr/local/java8
```

### Method 2: Maven Compiler plugin properties
The following properties can be configured to set the Java version in Maven.

- maven.compiler.source
- maven.compiler.target

If Java 8 is needed, In the pom.xml, add the above two properties.
```xml
 <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.target>1.8</maven.compiler.target>
    <maven.compiler.source>1.8</maven.compiler.source>
 </properties>
```

### Method 3: Configure the Maven Compiler plugin
Add the source and target while you configure the Maven compiler plugin in the pom.xml file.

If Java 8 is needed, refer to the following code.
```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.8.1</version>
        <configuration>
          <encoding>UTF-8</encoding>
          <source>1.8</source>
          <target>1.8</target>
          <archive>  
            <manifest>  
                <mainClass>com.daghan.App</mainClass>  
            </manifest>  
          </archive>  
        </configuration>
    </plugin>
  </plugins>
</build>
```
