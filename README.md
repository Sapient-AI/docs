# Sapient AI

- Sapient AI is Test Authoring as a Service which allow developers to focus on business requirements instead of tedious task of writing test codes.   

- Website: [https://www.sapient.ai](http://sapient.ai/)

<img alt="SapientAI" src="https://storage.googleapis.com/sapient-images/Sapient%20with%20wordmark%20-%20azure%20oxfordblue.png">



## Libraries required by Sapient Plugin

As of today Sapient supports unit test generation for Junit 5 and Junit 4 platform.

To successfully generate the unit tests Sapient Plugin requires Junit, Mockito and Hamcrest libraries to be present as dependency of the source project.

Listed below are the steps to add these dependencies in a project.

## Junit Platform

JUnit 5 introduced the concept of the JUnit Platform, which is a new foundation for running testing frameworks on the Java Virtual Machine (JVM). The JUnit Platform provides an execution environment for running tests and supports the creation of new testing frameworks. The JUnit Platform also introduced the concept of the JUnit Platform Launcher, which is responsible for discovering and executing tests on the platform.

The JUnit Platform supports different testing frameworks, and the term "engine" is often used to describe the individual components responsible for running tests written in a particular framework. For example:

JUnit Jupiter Engine: The engine that runs tests written using the JUnit Jupiter programming model.

JUnit Vintage Engine: The engine that runs tests written in JUnit 3 and JUnit 4 style.

## Junit 5 Platform

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

### JUnit Jupiter Engine 

It's required to add junit jupiter engine as dependency to run junit 5 tests, like described above.
 
## Junit 4 Platform

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

### JUnit Vintage Engine 

To use the new junit platform to run junit 4 tests its required to add junit vintage engine as a project dependency.

- Maven 
   
   ```
	<dependency>
	    <groupId>org.junit.vintage</groupId>
	    <artifactId>junit-vintage-engine</artifactId>
	    <version>5.9.2</version>
	    <scope>test</scope>
	</dependency>

  ```
  
- Gradle

 ``` 
      testRuntimeOnly group: 'org.junit.vintage', name: 'junit-vintage-engine', version: '5.9.2'
 ```
 
## Mockito Libraries ( JDK 8 : 4.x (recommended 4.11.0) )

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

## Mockito Libraries ( JDK 11 and Above : 5.x (recommended 5.2.0) )

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
  
## Hamcrest Library  
   

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

Sapient AI Test Coder requires gcc to be installed on linux before using the plugin.

## Java Version Requirement
Sapient AI Test Coder supports test generation for Java Version 8 to 17. Follow below steps to update java version for:

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
    <maven.compiler.source><VERSION></maven.compiler.source>
    <maven.compiler.target><VERSION></maven.compiler.target>
  </properties>
 ```


 
## Cyclomatic Complexity
  
Cyclomatic complexity of a source code section is the quantitative measure of the number of linearly independent paths in it. It is calculated by developing a Control Flow Graph of the code that measures the number of linearly-independent paths through a program module.

- LOW 
   If the count of independent paths is <= 7 then we label it as LOW in Sapient Plugin

- MEDIUM
   If the count of independent paths is > 7 and <= 10 then we label it as MEDIUM in Sapient Plugin

- HIGH 
   If the count of independent paths is > 10 then we label it as HIGH in Sapient Plugin

## Troubleshooting

- If you face the following issue when running the tests, please make sure you have at least byte-buddy version 1.12.9
 ```
    Could not initialize plugin: interface org.mockito.plugins.MockMaker
    Caused by: org.mockito.exceptions.base.MockitoInitializationException:
    It seems like you are running Mockito with an incomplete or inconsistent class path. Byte Buddy could not be loaded.
    Byte Buddy is available on Maven Central as 'net.bytebuddy:byte-buddy' with the module name 'net.bytebuddy'.
```   


## Disabled Generated Tests

If a method under test contains system calls, it could potentially be dangerous as it may exit the program, hang the thread, or possibly delete files or directories. When we detect such potential harmful calls, we add @Disabled on the test generated, so by default it won't be executed by the system. User is advised to review the details of the test, and may remove @Disabled if he thinks the test is harmless. 

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
In this case, AI Sapient detects that System.exit is called inside myMethod when true is passed as argument.

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

### Main Method

Main method is used to launch Java application, start server or setup infrastructure elements, so it has been excluded from unit testing.

### Getters and Setters Methods

Getters and Setters are standard methods used to maintain the state in a Java class. These are devoid of programming complexity, so they have been excluded from unit testing.

### Equals, hashCode, wait, notify, waitAll, notifyAll etc.

Common object methods such as equals, hashCode, wait, notify, waitAll, notifyAll etc. are excluded from unit testing.

## Environment 

Intellij runs over JetBrains Runtime (JRE), that was designed to be a high-performance runtime environment for running JetBrains IDEs and other Java-based applications. It is optimized for the specific needs of JetBrains products.

### Supporting projects with a java version greather than 17

The current default version of IntelliJ (2023.3) operates on JBR 17. Since the Sapient plugin is integrated with IntelliJ, we are committed to supporting projects using Java 17 or older. However, IntelliJ provides the flexibility to change the JBR version it runs on, allowing you to switch from 17 to 21. By doing so, you'll gain the ability to use Sapient with more recent Java versions.

To learn how to change the JBR of IntelliJ, refer to the [official guide](https://www.jetbrains.com/help/idea/switching-boot-jdk.html).

When you access the "Choose Boot Runtime for the IDE" dialog, simply navigate to the "New:" field, search among the options, and select the one with "21" in the description. This will enable you to use Sapient with Java versions beyond 17.

### Crashing Intellij build version 233 (2023.3) and Jetbrains Runtime 17 with JCFE

Some IntelliJ users encountered JVM crashes when using IntelliJ 2023.3 with JetBrains 17 and JCFE, which is the default option upon installing an IntelliJ version. The issue is documented in [IDEA-340379](https://youtrack.jetbrains.com/issue/IDEA-340379/JVM-crash-after-IDE-upgrade-with-shared-indexes-SIGSEGV-in-AppendOnlyLogOverMMappedFileRecordLayout.readHeader).

JetBrains has already addressed the bug, and the fix is scheduled to be released in the first version of the 2024 release.

Until then, we recommend our users to change the JRE that IntelliJ uses from the version with JCFE to the vanilla version. Refer to this [guide](https://www.jetbrains.com/help/idea/switching-boot-jdk.html) for instructions on how to change the JRE in IntelliJ.

When you access the "Choose Boot Runtime for the IDE" dialog, search in the "New:" field among the options and select the one with the description "JetBrains Runtime JBR (vanilla)" (the most recent version). This adjustment should help mitigate the JVM crash issue until the official fix is released.



