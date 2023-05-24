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

## Java Version Requirement
Sapient AI supports test generation for Java Version 8 through 17. To update java version for:

- Gradle
 ```
 java {
    sourceCompatibility = JavaVersion.VERSION_17
    targetCompatibility = JavaVersion.VERSION_17
}
 ```

- Maven
 ```
<properties>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
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
