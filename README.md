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
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.2.0'
 ```
 
 
 ## Mockito  

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
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.2.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '5.2.0'
 ```
 
 ## Hamcrest  

- Maven 
   
   ```
      <dependency>
         <groupId>org.hamcrest</groupId>
         <artifactId>hamcrest</artifactId>
         <version>2.2.0</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.hamcrest', name: 'hamcrest', version: '2.2'
 ```
 
 
