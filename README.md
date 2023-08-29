# Sapient AI

- Sapient AI is Test Authoring as a Service which allow developers to focus on business requirements instead of tedious task of writing test codes.   

- Website: [https://www.sapient.ai](http://sapient.ai/)

<img alt="SapientAI" src="https://storage.googleapis.com/sapient-images/Sapient%20with%20wordmark%20-%20azure%20oxfordblue.png">



## Libraries required by Sapient Plugin

As of today Sapient supports unit test generation for Junit 5 and Junit 4 platform.

To successfully generate the unit tests Sapient Plugin requires Junit, Mockito and Hamcrest libraries to be present as dependency of the source project.

Listed below are the steps to add these dependencies in a project.



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
         <groupId>org.junit.platform</groupId>
         <artifactId>junit-platform-launcher</artifactId>
         <version>1.9.2</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.junit.jupiter', name: 'junit-jupiter-api', version: '5.9.2'
       testImplementation group: 'org.junit.platform', name: 'junit-platform-launcher', version: '1.9.2'
 ```
 
 
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
 
 
## Mockito Libraries

- Maven 
   
   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>{$mockito.version}</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>{$mockito.version}</version>
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
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '{$mockito.version}'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '{$mockito.version}'
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.12.9
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.4'
 ```

- {$mockito.version} :
  ```
  	For JDK 8 : 4.x (recommended 4.11.0)
	For JDK 11 and Above : 5.x (recommended 5.2.0)
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



