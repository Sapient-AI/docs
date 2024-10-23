# Sapient AI

- Sapient.ai is an advanced AI-driven platform that transforms the landscape of software development through automated unit test generation. Its main features include exceptional code integrity assurance, fast and responsive test generation, and personalized code feedback to improve overall code quality. For software engineers, it expedites the development cycle, enhances code reliability, and offers valuable insights for code refinement.   

- Website: [https://www.sapient.ai](http://sapient.ai/)

<img alt="SapientAI" width="200" height="auto" src="https://assets-global.website-files.com/644c54b9f870d8f15c27f21a/650a35c8f6932ac72a30ccba_Sapient-Horizontal-1-p-500.png"> <h1>Sapient.ai</h1></img>



## Libraries required by Sapient Plugin

In order to ensure successful test generation, the Sapient Plugin mandates the presence of JUnit, Mockito, and Hamcrest libraries as dependencies in the source project.

Below are the steps to seamlessly integrate these dependencies into your project:

## Junit Platform

Sapient facilitates unit test generation across JUnit 5, JUnit 4, or TestNG platforms. The tool automatically identifies the JUnit version by inspecting the unit testing libraries declared in the project. If the project doesn't currently employ any unit testing libraries, it's necessary to include one of these libraries to enable seamless integration with Sapient. If the project contains multiple JUnit libraries (e.g., JUnit 4 and TestNG), users have the option to set their preferred platform in the settings.



JUnit 5 introduced the concept of the JUnit Platform, which is a new foundation for running testing frameworks on the Java Virtual Machine (JVM). The JUnit Platform provides an execution environment for running tests and supports the creation of new testing frameworks. The JUnit Platform also introduced the concept of the JUnit Platform Launcher, which is responsible for discovering and executing tests on the platform.

The JUnit Platform supports different testing frameworks, and the term "engine" is often used to describe the individual components responsible for running tests written in a particular framework. For example:

JUnit Jupiter Engine: The engine that runs tests written using the JUnit Jupiter programming model.

JUnit Vintage Engine: The engine that runs tests written in JUnit 3 and JUnit 4 style.

## Junit 5 Platform
Sapient utilizes the JUnit Jupiter programming model for test code generation and employs the respective engine to execute and validate the tests if Junit 5 libraries have been included in the project. Following dependencies can be included for JUnit 5:

- Maven 
   
   ```
      <dependency>
         <groupId>org.junit.jupiter</groupId>
         <artifactId>junit-jupiter-api</artifactId>
         <version>5.9.2</version>
         <scope>test</scope>
      </dependency>
      
       <dependency>
         <groupId>org.junit.jupiter</groupId>
         <artifactId>junit-jupiter-engine</artifactId>
         <version>5.9.2</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.junit.jupiter', name: 'junit-jupiter-api', version: '5.9.2'
       testRuntimeOnly group: 'org.junit.jupiter', name: 'junit-jupiter-engine', version: '5.9.2'
 ```

 
## Junit 4 Platform

Sapient utilizes the JUnit 4 Vintage programming model for test code generation and employs the respective engine to execute and validate the tests if Junit 4 libraries have been included in the project. Following dependencies can be included for JUnit 4:

- Maven 
   
   ```
      <dependency>
         <groupId>junit</groupId>
         <artifactId>junit</artifactId>
         <version>4.13.2</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'junit', name: 'junit', version: '4.13.2'
 ```

## TestNG Platform

Sapient utilizes the TestNG programming model for test code generation and employs the respective engine to execute and validate the tests if TestNG libraries have been included in the project.

For Java version 11 and higher:
- Maven

   ```
      <dependency>
         <groupId>org.testng</groupId>
         <artifactId>testng</artifactId>
         <version>7.9.0</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle

	``` 
       testImplementation group: 'org.testng', name: 'testng', version: '7.9.0'
	```
For Java Versions less than 11
- Maven

   ```
      <dependency>
         <groupId>org.testng</groupId>
         <artifactId>testng</artifactId>
         <version>7.5</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle
	
	``` 
       testImplementation group: 'org.testng', name: 'testng', version: '7.5'
	```

## Mockito Libraries ( JDK 11 and Above : 5.x)

Mockito is a library designed for creating mocks and stubs of objects, enabling isolation across logical layers in the code. To ensure compatibility with Java 11 or newer versions, it is recommended to use Mockito version 5.x or later.

For JDK 21, 22 (recommended mockito version 5.7.0, we need byte-buddy that is equal to or above 1.14.9 and so we exclude the byte-buddy that is shipped with mockito-inline)
For JDK 23 (recommended mockito version 5.7.0, we need byte-buddy that is equal to or above 1.14.16 and so we exclude the byte-buddy that is shipped with mockito-inline)

- Maven for JDK 23

   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>5.7.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
    	 <exclusions>
            <exclusion>
               <groupId>net.bytebuddy</groupId>
               <artifactId>byte-buddy</artifactId>
            </exclusion>
    	 </exclusions>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.14.16 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.16</version>
         <scope>test</scope>
      </dependency>
  ```

- Maven for JDK 21, 22

   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>5.7.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
    	 <exclusions>
            <exclusion>
               <groupId>net.bytebuddy</groupId>
               <artifactId>byte-buddy</artifactId>
            </exclusion>
    	 </exclusions>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.14.9 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.9</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle for JDK 23

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.7.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '5.2.0'{
		exclude group: 'net.bytebuddy', module: 'byte-buddy
	}
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.14.16
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.16'
 ```

- Gradle for JDK 21, 22

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.7.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '5.2.0'{
		exclude group: 'net.bytebuddy', module: 'byte-buddy
	}
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.14.9
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.9'
 ```

For JDK 11 to JDK 20  (recommended mockito version 5.2.0)

- Maven 
   
   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.12.9 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.4</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.2.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '5.2.0'
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.12.9
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.4'
 ```

## Mockito Libraries ( JDK 8 : 4.x (recommended 4.11.0) )

Mockito is a library designed for creating mocks and stubs of objects, enabling isolation across logical layers in the code. To ensure compatibility with Java 8 version, it is recommended to use Mockito version 4.x or older.
- Maven 
   
   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>4.11.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>4.11.0</version>
         <scope>test</scope>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.12.9 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.4</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '4.11.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '4.11.0'
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.12.9
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.4'
 ```


## Hamcrest Library  
It brings substantial enhancements in terms of readability, expressiveness, composability, and error message reporting. For a detailed exploration of these advantages, you can refer to our blog post at: [Understanding Hamcrest: Advantages and Disadvantages for Java Testing](https://www.sapient.ai/blog/understanding-hamcrest-advantages-and-disadvantages-for-java-testing).

- Maven 
   
   ```
      <dependency>
         <groupId>org.hamcrest</groupId>
         <artifactId>hamcrest</artifactId>
         <version>2.2</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.hamcrest', name: 'hamcrest', version: '2.2'
 ```

## OS Libraries

- Linux

Sapient AI Test Coder requires libgcc and libstdc++6 to be installed on linux before using the plugin. Please make sure these two packages are installed in your machine. For Ubuntu distribution you could install executing the following commands: 
 ``` 
       sudo apt install libgcc-s1
       sudo apt install libstdc++6
 ```

## Java Version Requirement
Sapient supports unit test generation for project using Java Version 8 to 17 without any adjustments. However for Java 18 or later versions, configuring Intellij IDEA is required to boot up with the respective versions, as described below.

### Supporting projects with a java version 18 or later
The current IntelliJ version (2024.1) defaults to boot up with Java 17, which may limit plugins' ability to interpret and process classes generated using Java 18 or later versions. 

Please follow below instructions to update the Java Runtime in IntelliJ.

	- In the main menu, go to Help | Find Action
	- Find and select the Choose Boot Java Runtime for the IDE action.
	- Select the new desired runtime ex: JetBrains Runtime JBR (vanilla).
	- Click OK.
	- If necessary, you can change the location where IntelliJ IDEA will download the selected runtime.
	- Wait for IntelliJ IDEA to restart with the new runtime.
	- This adjustment should help mitigate the JVM crash issue until the official fix is released.

![alt text](https://github.com/Sapient-AI/docs/blob/main/images/choose-boot-java-runtime-for-ide.png?raw=true)

Intellij's Official documentation available here [official guide](https://www.jetbrains.com/help/idea/switching-boot-jdk.html) to change the default Java version for IntelliJ boot-up.

### Fixing Java Version

Following steps are required to fix the java version in the project:

- Gradle
 ```
 java {
    sourceCompatibility = JavaVersion.<VERSION>
    targetCompatibility = JavaVersion.<VERSION>
}
 ```

- Maven
 ```
<properties>
    <maven.compiler.source>VERSION</maven.compiler.source>
    <maven.compiler.target>VERSION</maven.compiler.target>
</properties>
 ```

 
## Cyclomatic Complexity
  
The cyclomatic complexity of a section of source code is a quantitative measure indicating the number of linearly independent paths within it. This metric is derived by constructing a Control Flow Graph of the code, effectively quantifying the number of linearly independent paths through a given program module. It's labeled as LOW, MEDIUM or HIGH based on number of independent paths.

- LOW 
   No. of independent paths is less than or equal to 7.

- MEDIUM
   No. of independent paths is between 7 and 10.

- HIGH 
   No. of independent paths is greater than 10.


## Disabled Generated Tests

When a method under test involves system calls, there's a potential for adverse effects such as program termination, thread hang, or file/directory deletion. To mitigate risks, we identify and flag such potentially harmful calls by adding @Disabled to the generated test. By default, these tests won't be executed. Users are encouraged to review test details and may choose to remove @Disabled if they determine the test is safe.

For example, the test generated may look like this:
 ```
    //Sapient generated method id: ${3f698e62-d52c-38cd-bce6-39784a59918a}
    @Disabled(value = "Potential harmful system call (System.exit) detected; Learn more: https://github.com/Sapient-AI/docs#disabled-test-due-to")
    @Test()
    void myMethodWhenParam() {
        /* Branches:
         * (param) : true
         */
        TestSystemExit target = new TestSystemExit();
        String result = target.myMethod(true);
        assertAll("result", () -> assertThat(result, equalTo("!")));
    }
 ```


The following Java functions are considered potentially dangerous, and if detected during test generation, @Disabled will be added to the test.

- Regular Functions:
	- java.lang.Runtime: exec, exit, halt, wait
	- java.lang.Thread: destroy, interrupt, run, start, stop, suspend, wait
	- java.net.ServerSocket: accept, bind
	- java.nio.channels.Selector: (all functions)
	- java.util.concurrent.CompletableFuture: complete, completeAsync
	- java.util.concurrent.CountDownLatch: await, countDown
	- java.util.concurrent.CyclicBarrier: await
	- java.util.concurrent.ExecutorService: awaitTermination, invokeAll, invokeAny, shutdown, shutdownNow, submit
	- java.util.concurrent.Future: get

- Static Functions:
	- java.nio.file.Files: delete, deleteIfExists
	- java.lang.System: exit

## Batch Generation
Sapient offers a robust feature enabling the specification of one or multiple source folders for unit test code generation. These folders yield numerous classes, each of which is meticulously analyzed and processed to generate test code. Sapient methodically examines every method within these classes, compiling a comprehensive list of test cases and associating them with their respective test methods. Notably, certain methods, such as main methods for launching applications or getters/setters for data access, are purposefully excluded. This ensures that unit test code generation remains focused on functional code and avoids unnecessary code sprawl.


### Main Method

Main method is used to launch Java application, start server or setup infrastructure elements, so it has been excluded from unit testing.

### Getters and Setters Methods

Getters and Setters are standard methods used to maintain the state in a Java class. These are devoid of programming complexity, so they have been excluded from unit testing.

### Equals, hashCode, wait, notify, waitAll, notifyAll etc.

Common object methods such as equals, hashCode, wait, notify, waitAll, notifyAll etc. are excluded from unit testing.


## Troubleshooting

### Byte buddy minimal version

If you face the following issue when running the tests, please make sure the version of  byte-buddy is **1.12.9** or later
 ```
    Could not initialize plugin: interface org.mockito.plugins.MockMaker
    Caused by: org.mockito.exceptions.base.MockitoInitializationException:
    It seems like you are running Mockito with an incomplete or inconsistent class path. Byte Buddy could not be loaded.
    Byte Buddy is available on Maven Central as 'net.bytebuddy:byte-buddy' with the module name 'net.bytebuddy'.
```   

### Crashing Intellij build version 233 (2023.3) and Jetbrains Runtime 17 with JCFE

Some IntelliJ users have encountered JVM crashes when using IntelliJ 2023.3 with JetBrains 17 and JCFE, which is the default option upon installing an IntelliJ version, as reported here [IDEA-340379](https://youtrack.jetbrains.com/issue/IDEA-340379/JVM-crash-after-IDE-upgrade-with-shared-indexes-SIGSEGV-in-AppendOnlyLogOverMMappedFileRecordLayout.readHeader).

JetBrains has already acknowledged and scheduled to release the fix in the 2024 release. Till then, users are recommended to change the JRE that IntelliJ uses from the version with JCFE to the vanilla version. 

Please refer to instructions mentioned in section [Supporting projects with a java version 18 or later](#Supporting-projects-with-a-java-version-18-or-later)

### Unable to update build.gradle/build.gradle.kts/pom.xml

In case of a message like `Unable to update build.gradle.kts. Please update with these instructions` we are usually not able to find the build files because of: 
- Either it is missing in the package.
- It is renamed.
To resolve it please follow along the doc to add these dependencies to your build file. After a successful sync, the plugin will start generating tests for your repository. 

