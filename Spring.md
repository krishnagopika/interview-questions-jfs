## Technical

1. What are Spring Beans?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Core business component defined insider Spring applications is termed as `Bean`. 
- In simple terms `Bean` is an object that is instantiated, assembled, and managed by a Spring IoC container.
- Each technology has branded their core business components by certain nomenclature. For example, Business component in `JavaEE` applications are termed as `Servlet`, in `Web Services` they are named as `Resource` in `Struts` framework they are called `ActionForm` etc.
</blockquote> 

</details>

---
2. How do you decide whether to create `Singleton` bean or `Prototype` bean in application?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Though Spring IOC container has excellent support to manage the lifecycle of different types of beans,
Spring does not manage the complete lifecycle of a prototype bean.
- The IOC container instantiates, configures, decorates, and otherwise assembles a prototype object, hands it to the client and then has no further knowledge of that `Prototype` instance.
- For most of the simple to average applications `Singleton` bean are sufficient and serve the purpose at each layer e.g. DAO, Service, Controller etc.
- Developer need to take smart decisions & identify which beans must be singleton, else multiple client requests using singleton bean can modify the state of common objects wrongly.
- Some dependent objects need a bean that has private state so that they can conduct their processing separately from other objects that depend on the bean. In this case, singletons are clearly not suitable, and we consider prototypes.
- If you have a bean that has a lot of writable state, you may find that the cost of synchronization is greater than the cost of creating a new instance to handle each request from a dependent object that time you can use prototype bean.

</blockquote> 

</details>

---

3. When do you use `Session` and `Request` bean in Spring?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

- Both beans are used mainly in Web Application.
- If the bean scope is `Request`, then on every request (from same user or different user) a new bean will be created.
- If the bean scope is `Session` then on every request same bean would be returned if requests are within the same user session also made from a client which is capable of maintaining the session (`curl` command can't maintain the user session unless pass cookie/session identifier header).
- `Session` beans are not destroyed until session timeout up or session destroyed.

</details>
    
</blockquote> 

---

4. How an IOC container is configured in a spring console based application?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

- Spring IOC container is primarily responsible for holding all business components termed as `Bean`.
- Few of these beans are added by spring framework and rest all are defined by developers.
- These beans can be configured using XML configuration file (usually named as `applicationContext.xml`) or using Java Configuration class (usually named as `AppConfig.java`).
- **`applicationContext.xml` sample** -
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
     http://www.springframework.org/schema/beans/spring-beans-4.3.xsd">

    <bean id="intelProcessor" class="com.revature.model.Intel">
        <property name="modelName" value ="Intel i7"/>
        <property name="cacheMemory" value="64MB" />
        <property name="price" value="6700.00"/>
        <property name="numberOfCores" value="7 Cores" />
    </bean>
    <bean id="myLaptop" class="com.revature.model.Laptop" autowire="no">
        <property name="modelName" value="Lenovo Think PagEdge" />
        <property name="price" value="78900.00" />
        <property name="processor" ref="intelProcessor" />
    </bean>
    <bean id="yourLaptop" class="com.revature.model.Laptop" autowire="no">
        <constructor-arg value="Alienware"></constructor-arg>
        <constructor-arg value="98900.00"></constructor-arg>
        <constructor-arg ref="intelProcessor" ></constructor-arg>
    </bean>
</beans>
```
- **`AppConfig.java` sample** -

```java
package com.revature.config;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Description;
import org.springframework.context.annotation.Scope;
//Assume below model classes exist in the application
import com.revature.model.Intel;
import com.revature.model.Laptop;

@Configuration
public class AppConfig {
    @Bean(name = "i7")
    @Description("This bean is used to injection dependency inside Laptop class")
    public Intel getIntelProcessor() {
        return new Intel("Intel i7", "64MB", 6700.0, "7 Cores");
    }

    @Bean
    @Description("My Lenovo Laptop Bean")
    public Laptop myLaptop() {
        // This is JavaConfig Alternative for Setter Based Injection
        Laptop myLappy = new Laptop();
        myLappy.setModelName("Lenovo Think PagEdge");
        
        // In applciationContext.xml this value will be in double quotes unlike
        // java developers who want it without double quotes
        myLappy.setPrice(78900.00);
        myLappy.setProcessor(getIntelProcessor());
        return myLappy;
    }

    @Bean
    @Description("Your Mac Book Pro Laptop Bean")
    @Scope("singleton")
    public Laptop yourLaptop() {
        // This is JavConfig Alternative for Constructor Based Injection
        Laptop yourLappy = new Laptop("Mac Book Pro",149000.0, getIntelProcessor());
        return yourLappy;
    }

    /* --- Comparison ---
        @Configuration  //== applicationContext.xml
        class AppConfig
        @Bean   //== <bean>
        public Amd amd(){  // id=amd class="com.revature.model.Amd"
        Amd a= new Amd();
        a.setPrice();     // <property name="price" value="23232"/>
        ....
        ....
        return a;
        }
    */
}
```
- The Spring IOC container can be programmatically accessed using two interfaces namely: `BeanFactory` & `ApplicationContext`.
- It's always advisable to use ApplicationContext which is child interface of BeanFactory.
- There are multiple implementations available of ApplicationContext depending upon your bean configuration.
- For `applicationContext.xml` based bean configuration we use `ClassPathXmlApplicationContext` class.
```java
package com.revature.client;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import com.revature.model.Laptop;
public class App {
    public static void main(String[] args) {
        Laptop lenovoLaptop, secondLaptop;
        ApplicationContext appContext = new ClassPathXmlApplicationContext("applicationContext.xml");
        lenovoLaptop = (Laptop) appContext.getBean("myLaptop");
        System.out.println(lenovoLaptop);
        secondLaptop = (Laptop) appContext.getBean("yourLaptop");
        System.out.println(secondLaptop);
        ((ClassPathXmlApplicationContext) appContext).close();
    }
}
```
- For `AppConfig.java` based bean configuration we use `AnnotationConfigApplicationContext` class.

```java
package com.revature.client;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import com.revature.config.AppConfig;
//Assume below model classes exist in the application
import com.revature.model.Laptop;
import com.revature.model.Processor;
public class App {
    public static void main(String[] args) {
        AnnotationConfigApplicationContext  appContext = new AnnotationConfigApplicationContext(AppConfig.class);
        Laptop lenovoLaptop, secondLaptop;
        Processor intelProcessor;

        System.out.println("/////////////////////////////////");
        intelProcessor= (Processor) appContext.getBean("i7");
        System.out.println(intelProcessor);
        
        System.out.println("/////////////////////////////////");
        lenovoLaptop = (Laptop) appContext.getBean("myLaptop");
        System.out.println(lenovoLaptop);
        
        System.out.println("/////////////////////////////////");
        secondLaptop = (Laptop) appContext.getBean("yourLaptop");
        System.out.println(secondLaptop);
            
        appContext.close();
        
    }
}
```

</blockquote> 
    
</details>

---

5. How to decide upon choosing BeanFactory or ApplicationContext in Spring application?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

- The Spring IOC container can be programmatically accessed using two interfaces namely: `BeanFactory` & `ApplicationContext`
- The BeanFactory is the root interface and the ApplicationContext extends the features of BeanFactory.
- BeanFactory loads beans on-demand (`Lazy Loading`), while ApplicationContext loads all beans at startup(`Eager Loading`). 
- BeanFactory is lightweight as compared to ApplicationContext.
- BeanFactory only supports two scopes — Singleton and Prototype, but ApplicationContext supports all types of bean scopes. 
- ApplicationContext enhances BeanFactory to provide several features that are suitable for enterprise applications.
- ApplicationContext provides messaging (`i18n` or internationalization) functionality, event publication functionality, annotation-based dependency injection, and easy integration with Spring AOP features.
- It's always advisable to use ApplicationContext.
- We should use BeanFactory only when memory consumption is critical.
    
</blockquote> 

</details>

---

6. What are the ways through which the Spring beans are configured?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>
    
<blockquote> 

- There are broadly two ways in which Spring beans are configured in application-
    - Using XML configuration – We usually define xml file with standard name as `applicationContext.xml` inside `src/main/resources` folder of your maven project.
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-4.3.xsd">
        <bean id="intelProcessor" class="com.revature.model.Intel">
            <property name="modelName" value ="Intel i7"/>
            <property name="cacheMemory" value="64MB" />
            <property name="price" value="6700.00"/>
            <property name="numberOfCores" value="7 Cores" />
        </bean>
    </beans>
    ```
    - Using Annotation configuration - `@Bean`, `@Component`, `@Service`, `@Repository`, `@Controller`, `@RestController`
    ```java
    @Component("employeeDtoForReport")  // Bean id - employeeDtoForReport
    public class EmployeeDto{
    //.....
    }

    @RestController // Bean id - employeeRestController 
    public class EmployeeRestController {
    //.....
    }

    @Repository   //Bean id - DepartmentRepository 
    public interface DepartmentRepository extends JpaRepository<Department, Long> {
    //.....
    }

    @Service //Bean id - employeeServiceImpl
    public class EmployeeServiceImpl implements EmployeeService {
    //.....
    }

    @Controller
    public class PayrollController {
    //.....
    }
    
    @Configuration
    public class AppConfig {
        @Bean 
        public void beanName(){   
            //.....
        }
    }
    ```
</blockquote> 

</details>

---
7. How Spring supports connection pooling? Elaborate what is connection pooling?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>
    
<blockquote> 

- Database connections are expensive operation.
- A connection pool is like a collection of open connections. 
- If a connection is established or created it should be added to the connection pool.
- When a connection is released, it's returned back to the pool, so other clients can reuse it.
- While the connection is open it can be used again and again.
- Spring support connection pooling by supporting configuration of DataSource inside application.
- Spring provides `DriverManagerDataSource` for testing application during development phase.
- There are third party DB connection pooling providers like `Apache DBCP`, `Hikari CP` etc. which can also be configured in application.
- `DriverManagerDataSource` sample -

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-4.3.xsd
            http://www.springframework.org/schema/context
            http://www.springframework.org/schema/context/spring-context-4.3.xsd">

        <bean id="accountDao" class="com.revature.dao.AccountDaoImpl"
            autowire="no">
            <!-- Setter based IOC/DI -->
            <property name="jdbcTemplate" ref="jdbcTemplate" />
        </bean>
        <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
            <!-- Constructor based IOC/DI -->
            <constructor-arg ref="dataSource" />
        </bean>
        <bean id="dataSource"
            class="org.springframework.jdbc.datasource.DriverManagerDataSource">
            <property name="driverClassName" value="com.mysql.cj.jdbc.Driver" />
            <property name="url" value="jdbc:mysql://localhost/gd_hibernate"></property>
            <property name="username" value="root"></property>
            <property name="password" value="admin"></property>
        </bean>
    </beans>
    ```
- `Apache DBCP` maven dependency(ies)-

    ```xml
    <!-- Apache DBCP jar -->
        <dependency>
            <groupId>commons-dbcp</groupId>
            <artifactId>commons-dbcp</artifactId>
            <version>1.4</version>
        </dependency>
    ```
- `Apache DBCP` sample -

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:p="http://www.springframework.org/schema/p"
        xmlns:context="http://www.springframework.org/schema/context"
        xsi:schemaLocation="http://www.springframework.org/schema/beans  
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd  
    http://www.springframework.org/schema/context  
    http://www.springframework.org/schema/context/spring-context-3.0.xsd">

        <context:component-scan base-package="com.revature" />
        <bean
            class="org.springframework.web.servlet.view.InternalResourceViewResolver">
            <property name="viewClass" value="org.springframework.web.servlet.view.JstlView"></property>
            <property name="prefix" value="/WEB-INF/jsp/"></property>
            <property name="suffix" value=".jsp"></property>
        </bean>
        <bean id="dao" class="com.revature.dao.EmpDao">
            <property name="template" ref="jt"></property>
        </bean>
        <bean id="jt" class="org.springframework.jdbc.core.JdbcTemplate">
            <property name="dataSource" ref="ds"></property>
        </bean>
        <bean id="ds" class="org.apache.commons.dbcp.BasicDataSource">
            <property name="driverClassName" value="com.mysql.cj.jdbc.Driver" />
            <property name="url" value="jdbc:mysql://localhost/gd_hibernate"></property>
            <property name="username" value="root"></property>
            <property name="password" value="admin"></property>
            <property name="initialSize" value="2" />
            <property name="maxActive" value="10" />
        </bean>
    </beans>  
    ```
</blockquote> 

</details>

---

8. What is usual cause of `org.springframework.beans.factory.NoUniqueBeanDefinitionException`?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Exception thrown when a BeanFactory is asked for a bean instance for which multiple matching candidates have been found when only one matching bean was expected.
- To understand problem, consider below situation where we have three input interfaced namely `Keyboard`, `Mouse` and `Joystick` implementing `Usb` interface.
- The class `Counterstrike` has one dependency called `gameControl` of type `Usb`.
- The Spring container while injecting dependency gameControl has confusion, as there are three qualifying beans for desired match, hence we will get `NoUniqueBeanDefinitionException` exception.

    ```java
    @Component
    public class Keyboard implements Usb{
        //....
    }
    @Component
    public class Mouse implements Usb{
        //....
    }
    @Component
    public class Joystick implements Usb{
        //....
    }

    @Component
    public class Counterstrike {
        @Autowired
        private Usb gameControl;
        //....
    }
    ```
- The solution for the exception will be using `@Qualifier` annotation with exact matching bean name-
    ```java
    @Component
    public class Counterstrike {
        @Autowired
        @Qualifier("joystick")
        private Usb gameControl;
        //....
    }
    ```
</blockquote> 

</details>

---
9. Have you configured Init & Destroy spring bean lifecycle hooks? 

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Spring provides several ways through which you can tap into the bean lifecycle. 
- For example, once a bean is instantiated, you might need to perform some initialization to get the bean into a usable state. 
- Similarly, you might need to clean up resources before a bean is removed from the container.
- These actions can be achieved by configuring Init and Destroy lifecycle hooks into Spring application.
- `@PostConstruct` Annotation:
    - Whenever we annotate a method in Spring Bean with `@PostConstruct` annotation, it gets executed after the spring bean is initialized. 
    - We can have only one method annotated with `@PostConstruct` annotation. 
- `@PreDestroy` Annotation: 
    - When we annotate a Spring Bean method with PreDestroy annotation, it gets called when the bean instance is getting removed from the context.
    - Note: if your spring bean scope is `Prototype` then it’s not completely managed by the spring container and the PreDestroy method won’t get called. 
- Both of the above annotation are part of Common Annotations API and it’s part of JDK module `javax.annotation-api`. 
- Let’s look at simple example below:
- `MailService.java` file-
```java
package com.revature;
import java.util.HashMap;
import java.util.Map;
import javax.annotation.PostConstruct;
import javax.annotation.PreDestroy;
import org.springframework.beans.factory.config.ConfigurableBeanFactory;
import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

@Component
@Scope(scopeName = ConfigurableBeanFactory.SCOPE_SINGLETON)
public class MailService {
   private Map<String, String> map=null;
   public MailService() {
      map=new HashMap<>();
   }
   public void send(String mailTo){
      //Send mail code
      System.out.println("Inside send email method - "+mailTo);
   }
   @PostConstruct
   public void init() {
      map.put("host", "mail.gd.com");
      map.put("port", "25");
      map.put("from", "example@gd.com");
      System.out.println("Inside init method - "+map);
   }
   @PreDestroy
   public void destroy() {
      map.clear();
      System.out.println("Inside destroy method - "+map);
   }
}
```
- `MainApp.java` file-

```java
package com.revature.app;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import com.revature.MailService;

public class MainApp {
   public static void main(String[] args) {
      AnnotationConfigApplicationContext context = 
            new AnnotationConfigApplicationContext(AppConfig.class);
      // Send mail 1
      MailService mailService1 = (MailService) context.getBean("mailService");
      mailService1.send("coupancodes@gd.com");
      // Send mail 2
      MailService mailService2 = context.getBean(MailService.class);
      mailService2.send("newletters@gd.com");
      context.close();
   }
}

```
</blockquote> 

</details>

---
10. How do you decide as developer to choose among `.properties` or `.yaml` configuration file in Spring Boot application? 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- In Spring Boot, we use an external configuration to define our properties.
- This allows us to use the same application code in different environments.
- We can use properties files, YAML files, environment variables and command-line arguments.
- `application.properties` file, which uses a key-value format:
    - Here each line is a single configuration, so we need to express hierarchical data by using the same prefixes for our keys. 
```
management.endpoint.health.group.custom.include=*
management.endpoint.health.group.custom.show-components=always
management.endpoint.health.group.custom.show-details=always
```
- `application.yml` file, which uses a key-value format:
    - YAML is a convenient format for specifying hierarchical configuration data. 
    - The below code is more readable than .properties file alternative, due to lack of repeated prefixes.
```yml
management:
  endpoints:
    web:
      base-path: /
  endpoint:
    health:
      show-details: ALWAYS
      probes:
        enabled: true
      group:
        readiness:
          include: db, diskSpace
```
</blockquote>

</details>

---
11. Can we achieve DI with Core Java without using Spring framework?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Yes, Dependency Injection is a concept rather and then a framework. 
- When the application under question is small, we can always meet the needs by injecting dependencies manually, without using any framework like Spring.
- We can use Factory Design Pattern and create dependencies which will then be passed to required classes.
- Though such code cannot replace the DI framework like Spring which provide much more extensive set of features.
</blockquote> 

</details>

---

12. Brief us on Spring Framework.

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

The Spring Framework is a Java platform that provides comprehensive infrastructure support for developing Java applications. Spring handles the infrastructure so application developer can focus on your application.

</blockquote>

</details>

---

13. What is Dependency Injection? 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

Dependency Injection (DI) is a design pattern that removes the dependency from the programming code so that it can be easy to manage and test the application. Dependency Injection makes our programming code loosely coupled.

</blockquote>

</details>

---

14. How many types of spring beans are there? 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

There are 5 types of bean scope in Spring :-

1. **Singleton:-** It return a single bean instance per spring IOC Container.
2. **Prototype:-** It return a new bean instance each time when requested.
3. **Request:-** It return a single instance for every HTTP request call.
4. **Session:-** It returns a single instance for every HTTP request call.
5. **Global session:-** Global session scope is equal as session scope on portlet-based web applications.

</blockquote>

</details>

---


## Technical

1. Is there difference between Object Oriented Programming (OOP) and Aspect-Oriented Programming (AOP)?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Object Oriented Programming (OOP) and Aspect-Oriented Programming (AOP) are not mutually exclusive.
- AOP can be good addition to OOP.
- OOP is mainly used to model business logic whereas AOP helps to organize non-functional aspects (called cross cutting concerns) like Auditing, Logging, Transaction Management, Security etc.
- AOP helps to build methods without clogging up the business code with the cross-cutting concerns.
</blockquote> 

</details>

---
2. Why we need to use AspectJ in Spring application?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Spring provides simple and powerful ways of writing custom aspects (a modularization of a concern that cuts across multiple classes) by using @AspectJ annotation style. 
- @AspectJ refers to a style of declaring aspects as regular Java classes annotated with annotations. 
- The @AspectJ style was introduced by the AspectJ project as part of the AspectJ 5 release. 
- Spring interprets the same annotations as AspectJ 5, using a library supplied by AspectJ for pointcut parsing and matching. 
- Spring seamlessly integrates Spring AOP and IoC with AspectJ, to enable all uses of AOP within a consistent Spring-based application architecture.
- The @AspectJ support can be enabled with XML- or Java-style configuration. 
- In either case, we also need to ensure that AspectJ’s `aspectjweaver.jar` library is on the class path of application (version 1.8 or later). 
- This library is available in the lib directory of an AspectJ distribution or from the Maven Central repository.
- `pom.xml` sample-
```xml
    <properties>
        <aspectJ.version>1.6.11</aspectJ.version>
    </properties>
    <dependencies>
        <!-- AspectJ -->
        <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjrt</artifactId>
            <version>${aspectJ.version}</version>
        </dependency>
        <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjweaver</artifactId>
            <version>${aspectJ.version}</version>
        </dependency>
    </dependencies>
```
</blockquote> 

</details>

---
3. You must capture all exceptions caused in repository, service & controller layer using Spring AOP, how you can do it?

![Complex](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Complex%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Exception being one of the cross-cutting concern in Spring application which can be handled using Spring AOP.
- Ensure the AspectJ dependencies are added in pom.xml file.
- Define central logging class named `LoggingAspect.java` 
```java
import java.util.Arrays;
import org.aspectj.lang.JoinPoint;
import org.aspectj.lang.ProceedingJoinPoint;
import org.aspectj.lang.annotation.AfterThrowing;
import org.aspectj.lang.annotation.Around;
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Pointcut;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Component;

@Aspect
@Component
public class LoggingAspect {
    private final Logger log = LoggerFactory.getLogger(this.getClass());
    @Pointcut("within(@org.springframework.stereotype.Repository *)" +
        " || within(@org.springframework.stereotype.Service *)" +
        " || within(@org.springframework.web.bind.annotation.RestController *)")
    public void springBeanPointcut() {
        // Method is empty as this is just a Pointcut, the implementations are in the advice.
    }
    @Pointcut("within(com.revature.dao..*)" +
        " || within(com.revature.service..*)" +
        " || within(com.revature.controller..*)")
    public void applicationPackagePointcut() {
        // Method is empty as this is just a Pointcut, the implementations are in the advice.
    }
    //Advice that logs methods throwing exceptions.
    @AfterThrowing(pointcut = "applicationPackagePointcut() && springBeanPointcut()", throwing = "e")
    public void logAfterThrowing(JoinPoint joinPoint, Throwable e) {
        log.error("Exception in {}.{}() with cause = {}", joinPoint.getSignature().getDeclaringTypeName(),
            joinPoint.getSignature().getName(), e.getCause() != null ? e.getCause() : "NULL");
    }
}
```
- In above code, we have defined pointcut expression for DAO, Service & Controller layer.
- The `..` notation means "any package or subpackage", whereas `*` at the end of the expression after `..` means "any method in any class".
</blockquote>

</details>

---
4. You have to measure performance (or time taken by method execution), how can you achieve it with AOP?

![Complex](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Complex%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Apart from standard cross cutting concerns like Auditing, Logging, Transaction Management, Security etc. there are occasions where we want to deal with custom cross cutting concerns.
- Measuring performance of the method execution can be one of such example of cross cutting concerns.
- Ensure the AspectJ dependencies are added in pom.xml file.
- Define central logging class named `ExecutionTimeAspect.java` 
```java
package com.revature.aop;
import org.aspectj.lang.ProceedingJoinPoint;
import org.aspectj.lang.annotation.Around;
import org.aspectj.lang.annotation.Aspect;

@Aspect
public class ExecutionTimeAspect {
    @Around("execution(public String com.revature.service.RefundService.process(Long))")
    public Object measureExecutionTime(ProceedingJoinPoint joinPoint) throws Throwable {
        long start = System.currentTimeMillis();
        Object proceed = joinPoint.proceed();
        long executionTime = System.currentTimeMillis() - start;
        System.out.println(joinPoint.getSignature() + " executed in " + executionTime + "ms");
        return proceed;
    }
}
```
- In above code, we have defined pointcut expression to measure performance of `public String com.revature.service.RefundService.process(Long)` method.
</blockquote> 

</details>

---

5. Why we use pointcut expression in Spring application.

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Pointcut is an expression language of spring AOP which is basically used to match the target methods to apply the advice.
</blockquote> 

</details>

---
6. Why do we use @EnableAspectJAutoProxy?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Enables support for handling components marked with AspectJ's @Aspect annotation. 
- This annotation is usually defined on class marked with @Configuration.
```java
 @Configuration
 @EnableAspectJAutoProxy
 public class AppConfig {
    @Bean
     public FooService fooService() {
        return new FooService();
    }
    @Bean
    public MyAspect myAspect() {
        return new MyAspect();
    }
 }
```
</blockquote> 

</details>

---

## Technical

1. How do you decide whether to choose either Spring or Spring Boot framework for the application?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- It’s simple, any console/desktop or web application that wants to leverage DI & other key features provided by Core Spring modules can use the Spring framework.
- Spring Boot framework was evolved on top of Spring framework to support microservices-based architecture on the cloud.
- Spring Boot framework is popularly used to develop Web/Enterprise Applications, RESTful API & Microservices.
</blockquote>

</details>

---
2. Why do we need a `Service layer`? Can’t we call the `Repository layer` directly inside the `Controller layer`?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- There is no restriction from compiler, and we can call the Repository layer from the Controller layer directly.
- The layering helps to segregate the Spring application responsibilities and enables loose coupling between the objects.
- Service layer in the application facilitates communication between the Controller and the Persistence/Repository/DAO layer.
- Service layer usually holds business logic e.g. It may include validation logic.
- One Service layer may depend on multiple Repository layers to serve a specific business purpose.
- The method names in Service layer are usually named as per the business purpose they serve whereas method names in Repository are named as standard CRUD operations supported by that Repository.
- Hence, we need Service layer between DAO and Controller layer.
</blockquote> 

</details>

---
3. Is it safe to keep the DB & other critical passwords directly inside property file(s)?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Since property file(s) are readable by anyone who has access to the codebase it is highly recommended not to keep the DB and other critical credentials inside property file(s).
- They are usually stored inside cloud environment variables or passed through command line arguments while executing the application.
```
mvn spring-boot:run -Dspring-boot.run.jvmArguments='
-Dspring.datasource.url=jdbc:postgresql://localhost:5432/mydb 
-Dspring.datasource.username=admin 
-Dspring.datasource.password=gd123'
````
</blockquote> 

</details>

---
4. As a developer you need to check your production application status daily, how does Spring Boot could help here?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- One of the routine tasks for a developer is to check the status of the already launched production application periodically.
- To simplify this task, Spring Boot provides a sub-project named Spring Boot Actuator.
- Spring Actuator exposes operational information about the executing application, including, metrics, info, dump, env, etc. 
- The information is accessed usually via HTTP endpoints, a few of which are listed below:
    - `/health` summarizes the health status of our application.
    - `/beans` returns all available beans in our BeanFactory.
    - `/envy returns the current environment properties. 
- To enable Spring Boot Actuator, we just need to add the spring-boot-actuator dependency to our maven package manager.

```XML
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```
- To access the actuator endpoints using HTTP, we need to both enable and expose them.
- Only the /health and /info endpoints are exposed by default.
- We need to add the following configuration to expose all endpoints: 
`management.endpoints.web.exposure.include=*`

</blockquote> 
</details>

---
5. What is Spring profile and why do we use it?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Spring Profiles provide a way to segregate parts of your application configuration and make it only available in certain environments. 
- Any `@Component`, `@Configuration` or `@ConfigurationProperties` can be marked with `@Profile` to limit when it is loaded.
```java
@Configuration
@Profile("prod")
public class ProductionConfiguration {
 // ...
}

@Configuration
@Profile("test")
public class TestConfiguration {
 // ...
}
```
- In the normal Spring way, you can use a `spring.profiles.active` environment property to specify which profiles are active. 
- You can specify the property in any of the usual ways, for example, you could include it in your application.properties:
`spring.profiles.active=test`
or specify on the command line using the switch `--spring.profiles.active=prod`.
</blockquote> 

</details>

---
6. How can you define multiple profiles in the Spring Boot application? How to add an active profile?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- The application development process undergoes different stages; the typical ones are development, testing, and production. 
- Spring Boot profiles help group parts of the application configuration and make it available only in certain environments.
- A profile is a set of configuration settings. 
- Spring Boot allows to definition profile of -specific property files in the form of `application-{profile}.properties`.
- We can define both profile-specific and default application.properties file in the application. (For example, if your application activates a profile named prod and uses YAML files, then both application.yml and application-prod.yml will be considered).
- The local/default profile (`application.properties`) is usually called `default`; all the beans that do not have a profile set belong to the `default` profile.
- Spring automatically loads the properties in an application.properties file for all profiles and the ones in profile-specific property files only for the specified profile. 
- The keys in the profile-specific property override the ones in the default property file.
- There are plenty of ways of defining active profiles in Spring Boot, including command line arguments, Maven settings, JVM system parameters, environment variables, spring.profiles.active property, and SpringApplication methods.
- We commonly set active profiles using the `spring the .profiles.active` property or command line argument.
- For Example, we have three profiles (`local/default`, `dev`, `prod`) and two profile-specific property files as below:
```
pom.xml
src
├── main
│   ├── java
│   │   └── com
│   │       └── revature
│   │           └── Application.java
│   └── resources
│       ├── application-dev.properties
│       ├── application-prod.properties
│       └── application.properties
└── test
    └── java
```
</blockquote> 

</details>

---
7. What happens when two profiles are set for property `spring.profiles.active` in the Spring application?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- If several profiles are specified, a last-wins strategy applies. 
- For example, if profiles prod,live are specified by the spring.profiles.active property (i.e. `spring.profiles.active=prod,live`), values in `application-prod.properties` can be overridden by those in `application-live.properties`.
</blockquote> 

</details>

---
8. Which `pom.xml` file inside the Spring Boot framework defines versions of all pre-configured dependencies?

![Complex](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Complex%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Spring Boot framework has utilized the concept of parent and child pom file inheritance and defined all the dependencies specific to its release version under `spring-boot-dependencies` module.
- For example, refer to this link: https://repo1.maven.org/maven2/org/springframework/boot/spring-boot-dependencies/2.7.3/spring-boot-dependencies-2.7.3.pom

</blockquote> 

</details>

---
9. What is Bean Validation API? How can we use it in Spring?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- To restrict the input provided by the user in Spring MVC applications, the Spring >=4 supports and uses `Bean Validation API`.
- The Bean Validation API is a Java specification which is used to apply constraints to the fields of a class via annotations. 
- Using Bean Validation API we can validate a length, number, regular expression, etc. as well, and build custom validations.
- `Hibernate Validator` is the most famous/used implementation of the Bean Validation API specification.
- There are 3 types of variables that can be validated using Bean Validation API:
  - The request body,
  - Variables within the path (e.g., id in /api/{id}) and,
  - Query parameters.
- Spring Boot comes with the validation starter, which needs to be included in `pom.xml` file and the intern added the `hibernate-validator` dependency as below:

```xml
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
  </dependency>
```

</blockquote> 

</details>

---
10. Explain a few `hibernate-validator` Spring bean validation annotations?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Few common validation annotations are listed below:
  - `@NotNull`: Field must not be null.
  - `@NotEmpty`: List field must not be empty.
  - `@NotBlank`: String field must not be the empty String (i.e., it must have at least one Character).
  - `@Min` and `@Max`: Numerical field is only valid when its value is above or below a certain value.
  - `@Pattern`: String field is only valid when it matches a certain regular expression.
  - `@Email`: String field must be a valid email address.
</blockquote> 

</details>

---
11. What does the `@Valid` annotation indicate in Spring?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- The `@Valid` annotation can be added to variables in a `RestController` mapping method to validate them. 
- In the below code our POST request takes in a request body, and we're mapping that request body to a class InputForm.
- The `@Valid` annotation will tell Spring to go and validate the data passed into the controller i.e., age is between 18 and 60 inclusive because of those Bean Validation API annotations (min and max).
```java
@RestController
public class ValidateFormController {
  @PostMapping("/validateInput")
  ResponseEntity<String> validateBody(@Valid @RequestBody InputForm inputForm) {
    return ResponseEntity.ok("valid");
  }
  // ...
}

public class InputForm {
  @Min(18)
  @Max(60)
  private int age;
  // ...
}
```

</blockquote> 

</details>

---

12. What is the use of `@ControllerAdvice` in the Spring application?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `@ControllerAdvice` is a specialization of the `@Component` annotation which allows handling exceptions across the whole application in one global handling component.
- It intercepts exceptions thrown by methods annotated with `@RequestMapping` and similar.
- All you need to have is a class annotated with @ControllerAdvice. 
- If any exception is raised in the defined controller [you can define to which packages this controller advice should listen for exception in base packages] then it is handled by ControllerAdvice.
```java
@ControllerAdvice(basePackages = "{com.revature.controller}")
public class RestApiExceptionHandlerAdvice {
    /** Handle all business exceptions here */  
}
```
</blockquote> 

</details>

---

13. What is the use of `@ExceptionHandler` in the Spring application?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- The `@ExceptionHandler` is an annotation used to handle a specific exception in the controller and send a custom response to the client.
- We need to have a method annotated with @ExceptionHandler which takes Exception Class (any exception that you want to handle) as an argument, if any of these exceptions are raised in the controller, then this handler method will handle it.
- If we have two handler methods in the same controller say for example one handler for Exception and another handler for RuntimeException, then the handler method which is closer to the Exception Class hierarchy is triggered. 
- For example, if NullPointerException is thrown then IOException handler method is triggered, which is the closest to the Exception class.
```java
@ControllerAdvice(basePackages = "{com.revature.controller}")
public class RestApiExceptionHandlerAdvice {
    @ExceptionHandler(value = BadRequestException.class)
    public ErrorMessage handleBadRequest(BadRequestException exception) {
        //code...
        return errMsg;
    }
    @ExceptionHandler(value = GatewayTimeoutException.class)
    public ErrorMessage handleGatewayTimeout(GatewayTimeoutException exception) {
        //code...
        return errMsg;
    } 
}
```
</blockquote> 

</details>

---
14. Have you used the HAL browser in Spring? How to use it?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- HAL stands for Hypertext Application Language.
- HAL is a simple format that gives a consistent and easy way to hyperlink between resources in your API.
- Adopting HAL make API explorable, and its documentation easily discoverable from within the API itself. 
- In short, it makes API easier to work with and therefore more attractive to client developers.
- The HAL browser provides an in-browser GUI to traverse your Spring RESTful API.
- Below is the single dependency needed to integrate the HAL browser into our REST API. 

```xml
  <dependency>
	  <groupId>org.springframework.data</groupId>
	  <artifactId>spring-data-rest-hal-explorer</artifactId>
  </dependency>
```
- If we have the above dependency, Spring will auto-configure the HAL browser, and make it available via the default endpoint.
- All we need to do now is press run and switch to the browser. The HAL browser will then be available on http://localhost:8080/
</blockquote> 

</details>

---
15. What is the use of the `ResponseEntity` class in Spring?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `ResponseEntity` represents an HTTP response, including headers, body, and status. 
- While `@ResponseBody` puts the return value into the body of the response, ResponseEntity also allows us to add headers and HTTP Status codes.
- It can be used in both `@RestController` and `@Controller`.
```java
 @RequestMapping("/handle")
 public ResponseEntity<String> handle() {
   URI location = ...;
   HttpHeaders responseHeaders = new HttpHeaders();
   responseHeaders.setLocation(location);
   responseHeaders.set("MyResponseHeader", "MyValue");
   return new ResponseEntity<String>("Hello World", responseHeaders, HttpStatus.CREATED);
 }
```
</blockquote> 

</details>

---

16. What is Spring Boot?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

Spring Boot is a microservice-based framework and making a production-ready application in it takes very less time.

</blockquote>

</details>

---

17. What is the use of `@RestController`?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

`@RestController` is a convenience annotation for creating Restful controllers. It is a specialization of @Component and is autodetected through classpath scanning. It adds the @Controller and @ResponseBody annotations. It converts the response to JSON or XML.

</blockquote>

</details>

---
## Technical

1. What is the difference between `Spring JDBC` and `Spring Data JDBC`?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `Spring JDBC`, a sub-module under the Spring framework project, provides Spring abstractions over the plain JDBC `DataSource` that we can use with the Spring Framework.
- `Spring JDBC` nicely hooks support for `Transaction Management`, `Exception Handling`, `DB connection management`, `Connection pool configuration`, avoiding boilerplate code using `JdbcTemplate` etc.
- `Spring Data JDBC`, a sub-module under the Spring Data project, makes it easy to implement JDBC-based repositories.
- `Spring Data JDBC` is an Object Relational Mapper (ORM) based on the `Repository` abstraction.
- `Spring Data JDBC` nicely hooks support for `CrudRepository`, `@Query`, `PagingAndSortingRepository`, `@Value` in persistence constructors etc. 

</blockquote> 

</details>

---

2. What do you mean by database dialect? 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- A database dialect is a configuration setting for platform-independent software (`JPA`, `Hibernate`, etc.) which allows such software to translate its generic SQL statements into vendor-specific DDL, DML.
</blockquote> 

</details>

---

3. Why does Spring Data JDBC need database dialect?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- One of the core features of `Spring Data JDBC` is to generate automatic queries using `CrudRepository` for vendor-specific databases.
- To generate the queries `Spring Data JDBC` internally uses database dialects.
</blockquote> 

</details>

---

4. `Spring Data JDBC` includes direct support for which database dialects?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- In terms of databases, `Spring Data JDBC` requires a dialect to abstract common `SQL` functionality over vendor-specific flavors. 
- `Spring Data JDBC` includes direct support for the following databases:
    - `DB2`
    - `H2`
    - `HSQLDB`
    - `MariaDB`
    - `Microsoft SQL Server`
    - `MySQL`
    - `Oracle`
    - `Postgres`
</blockquote> 

</details>

---

5. Why do we use `PagingAndSortingRepository` in Spring?

![Complex](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Complex%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `Spring Data JDBC` sub-module under the Spring Data project provides `PagingAndSortingRepository` which is an extension of `CrudRepository` to provide additional methods to retrieve entities using the pagination and sorting abstraction.

</blockquote> 

</details>

---
6. The `CrudRepository` interface does not have an `update` method then how do we update the record in the database? 

![Complex](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Complex%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `CrudRepository` has only `save` but it acts as an `update` as well.
- When we `save` an entity with an empty `id` it will do a save.
- When you do `save` on the entity wan its existing `id` it will do an `update`.
- This means after we used findById and changed something in returned object, we can call save on that object and it will do an update because after findById you get an object with a populated id that exists in our database.
- `save` in `CrudRepository` can accept a single entity or Iterable of our entity type.
</blockquote> 

</details>

---
7. Is it mandatory to call the `save` method to update an object inside a transactional method for `CrudRepository`?

![Complex](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Complex%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Calling the `save` method to update an object inside a transactional method is not mandatory.
- When we use the `findById` method to retrieve an entity within a transactional method, the returned entity is managed by the persistence provider. 
- Hence, any change to that entity will be automatically persisted in the database, regardless of whether we are invoking the save method inside a transactional method.
</blockquote> 

</details>

---
8. What is the use of `@Query` annotation in Spring Data?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `Spring Data` provides multiple ways to define a query that we can execute.
- One of these popular methods is using `@Query` annotation.
- We can annotate the `Spring Data` repository method with the `@Query` annotation where its `value` attribute contains the `JPQL` or `SQL` to be executed.
- It's a convenient approach to place a query definition just above the method inside the repository rather than inside our domain model as named queries.
</blockquote> 

</details>

---
9. Explain the query builder mechanism in the Spring Data repository?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- The query builder mechanism built into the `Spring Data` repository infrastructure is useful for building constraining queries over entities of the repository.
- The query method names are divided into `subject` and `predicate`.
- The first part (`find…By`, `exists…By`) defines the subject of the query, and the second part forms the predicate.
- Few Queries subject keywords - `find…By`, `get…By`, `count…By`, `…Distinct…`, `delete…By`,`Top<number>…`
- Few Queries predicate keywords - `Containing`, `After`, `Before`, `Between`, `EndingWith`, `StartsWith`, `LessThan`, `GreaterThan`
- Few Query predicate modifier keywords - `IgnoreCase`, `OrderBy…`
- Example-
```java
interface PersonRepository extends Repository<Person, Long> {

  List<Person> findByEmailAddressAndLastname(EmailAddress emailAddress, String lastname);

  // Enables the distinct flag for the query
  List<Person> findDistinctPeopleByLastnameOrFirstname(String lastname, String firstname);
  List<Person> findPeopleDistinctByLastnameOrFirstname(String lastname, String firstname);

  // Enabling ignoring the case for an individual property
  List<Person> findByLastnameIgnoreCase(String lastname);
 
  // Enabling ignoring the case for all suitable properties
  List<Person> findByLastnameAndFirstnameAllIgnoreCase(String lastname, String firstname);

  // Enabling static ORDER BY for a query
  List<Person> findByLastnameOrderByFirstnameAsc(String lastname);
  List<Person> findByLastnameOrderByFirstnameDesc(String lastname);
}
```

</blockquote> 

</details>

---
10. How you will implement the `SQL` `LIKE` query in Spring Data using method names? Give an example.

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Let’s consider the Login entity comprising the userId attribute.
- There can be four different variations of LIKE query formed using method names as follows:
  - Exact Match `SELECT ... LIKE userId`
    - `List<User> findByUserIdLike(String userId);`
  - Starting With `SELECT ... LIKE userId%`
    - `List<User> findByUserIdStartingWith(String userId);`
  - Ending With `SELECT ... LIKE %userId`
    - `List<User> findByUserIdEndingWith(String userId);`
  - In Between `SELECT ... LIKE %userId%`
    - `List<User> findByUserIdContaining(String userId);`
</blockquote> 

</details>

---
11. What is `Spring Data JPA`?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `Spring Data JPA`, a sub-module under the Spring Data project, makes it easy to implement `JPA` based repositories.
- `Spring Data JPA` provides repository support for the `Java Persistence API (JPA)`. 
- It eases the development of applications that need to access JPA data sources. 
- `Spring Data JPA` nicely hooks support for `JpaRepository`, `Hibernate`, `OpenJPA`, `EclipseLink`, `Querydsl`, `@Modifying`
</blockquote> 

</details>

---
12.  What is the use of `@Modifying` in Spring Data JPA?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Adding `@Modifying` annotation indicates the query is not for a `SELECT` query.
- `@Modifying` annotation lets you execute `DML` inserts, updates, and deletes)and `DDL` using `JPA` `@Query` annotations.
- `@Modifying` annotation is only relevant in combination with the `@Query` annotation, derived query methods or custom methods do not require this Annotation.
</blockquote> 

</details>

---

## Technical

1. What is DispatcherServlet in the Spring MVC application?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- In the case of Spring MVC, DispatcherServlet is the front controller. 
- DispatcherServlet acts as an entry and exit point for any request received by the rom client. 
</blockquote> 

</details>

---

2. How DispatcherServlet handle requests &responses in the Spring MVC application?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Whenever a request comes it first goes to the DispatcherServlet where it then tries to identify its handler method (the methods defined in the specific controller to handle the requests) using Handler mapping.
- Once the handler mapping returns the controller the DispatcherServlet knows the controller which can handle the request and goes there for further request processing.
- Once the controller returns the view the DispatcherServlet goes to the view resolver to identify where the view is located.
- DispatcherServlet then grabs the view and returns as the final l response.
</blockquote> 

</details>

---

3. How Spring MVC DispatcherServlet is registered in the web.xml file?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Since DispatcherServlet is one type of Servlet the web.xml file configuration is the same as normal servlet.
- Additionally, as DispatcherServlet is our front controller we need to ensure that all the incoming requests should be routed to it using "/" url pattern.
```xml
<servlet>
    <servlet-name>dispatcher</servlet-name>
    <servlet-class>
        org.springframework.web.servlet.DispatcherServlet
    </servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>dispatcher</servlet-name>
    <url-pattern>/</url-pattern>
</servlet-mapping>
```
- If we are using `the spring-boot-starter-web` starter, DispatcherServletauto-configured to the URL pattern "/". So, we don't need to do any additional configuration in the web.xml file. 
</blockquote> 

</details>

---
4. How to change the default context path URL pattern of DispatcherServlet in Spring MVC?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- It's very simple, we need to change two properties inside the application.properties file.
```
server.servlet.context-path=/admin
spring.mvc.servlet.path=/v2
```
- With the above customizations, DispatcherServlet is configured to handle the URL pattern /v2 and the rcontext Path will be /admin. 
- Thus, DispatcherServlet listens at http://localhost:8080/admin/v2/.
</blockquote> 

</details>

---

5. Can we have one `@RestController` class with multiple `@GetMapping` methods?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Yes, we can have one `@RestController` class with multiple `@GetMapping` methods.
- Defining not only Get but any HTTP method-compliant mappings purely depend on the context of the application and its use cases.
- Below three GetMappings can be defined inside one UserRestController.
```java
@RestController
public class UserRestController{
    @GetMapping(path="/users/")
    public ResponseEntity<UserInfoDTO> getUserByUsername(@RequestParam String username) {
    }
    // GET user details by username: <protocol>://<hostUrl>/users?username=<username>

    @GetMapping(path="/users")
    public ResponseEntity<List<UserInfoDTO>> getAllUsers() {
    }
    // GET all user details: <protocol>://<hostUrl>/users

    @GetMapping(path="/users/{id}")
    public ResponseEntity<UserInfoDTO> getUserById(@PathVariable Long id)
    // GET user details for specific userid: <protocol>://<hostUrl>/users/<userid>
}
```
</blockquote> 

</details>

---
6. How do you ensure both "/" and "/welcome" request mappings land in the "index" view in Spring MVC applications?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `@RequestMapping` annotation in Spring MVC has a String[] value parameter, so we can specify multiple values like the below to return the index view of the rom controller class as below:
```java
@RequestMapping(value={"/", "welcome"})
public String homePage(){
  return "index";
}
```
</blockquote> 

</details>

---
7. Can @Controller annotation be used for both Spring MVC and RESTful applications?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Yes, @RestController is a convenience annotation that does nothing more than the @Controller and @ResponseBody annotations.
- Hence the following two controller definitions are the same:

```java
@Controller
@ResponseBody
public class RestControllerA { 

}

@RestController
public class RestControllerB { 

} 
```
</blockquote> 

</details>

---
8. What does @Controller & @RestController returns?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- @Controller returns a view in the Spring MVC application.
- @RestController returns an object as a response instead of a view.
</blockquote> 

</details>

---
9. What is the use of @ResponseBody in Spring?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- @ResponseBody is a Spring annotation which binds a method return value to the web response body. 
- It is not interpreted as a view name. 
- It uses `org.springframework.http.converter Interface HttpMessageConverter<T>` to convert the return value to the HTTP response body, based on the content type in the request HTTP header.
</blockquote> 

</details>

---
10. What are MIME Types?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- MIME stands for Multi-purpose Internet Mail Extensions. 
- MIME types form a standard way of classifying file types on the Internet. 
- Internet programs such as Web servers and browsers all have a list of MIME types so that they can transfer files of the same type in the same way, no matter what operating system they are working in.
- A MIME type has two parts: a `type` and a `subtype`. They are separated by a slash (`/`) i.e., `type/subtype`. 
- For example, the MIME type for Microsoft Word files is an application and the subtype is ms-word. Together, the complete MIME type is application/ms-word.
- The entire list of MIME types is available under Internet Assigned Numbers Authority (IANA) website- https://www.iana.org/assignments/media-types/media-types.xhtml
- The MIME types & extensions can be found under-https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types 
</blockquote> 

</details>

---
11. What is the use of `@RequestBody` in Spring?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `@RequestBody` annotation request body to method parameters. 
- We use the `@RequestBody` annotation to have the request body read and deserialized into an Object through an `HttpMessageConverter`. 
- Additionally, automatic validations can be applied by annotating the argument with @Valid annotation.
</blockquote> 

</details>

---
12. What is the meaning of Content Negotiation?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- Content negotiation is the process of selecting one of the multiple possible representations to return to a client, based on client or server preferences.
- When a consumer sends a request, it can specify two HTTP Headers related to Content Negotiation `Accept` and `Content-Type`.
- `Content-Type` indicates the content type of the body of the request.
- `Accept` indicates the expected content type of the response.
</blockquote> 

</details>

---
13. What is RESTprotocol-dependentependent?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- REST is about resource state manipulation through their representations at the top of stateless communication between client and server. 
- It's a protocol-independent architectural style but, in practice, it's commonly implemented on top of the HTTP protocol.
</blockquote> 

</details>

---
14. What are “representation", "state" and "transfer" in Representational State Transfer (REST)?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 

- To understand REST let us first understand the-    
  - What is a `resource`- 
    - The key abstraction of information in REST is a resource. 
    - There is no restriction on what a resource can be. 
    - Any information that can be named can be a resource: a document or image, a temporal service (e.g., "today's weather in Los Angeles"), a collection of other resources, a non-virtual object (e.g., a person), and so on.
  - What is a `representation`-
    - A JSON document can be used to represent the state of a particular resource. A resource can have many representations, such as JSON and/or XML documents, and the client can use content negotiation to request different representations of the same resource.
  - What is a `state transfer`-
    - The state of a given resource can be retrieved and manipulated using representations.
</blockquote> 

</details>

---
15. What is REST API versioning? 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- API versioning is the process of transparently managing changes to your API.
- Versioning aims at effective communication around changes to API, so consumers/subscribers know what to expect from it. 
</blockquote> 

</details>

---
16. How do we provide a version to RESTful APIs in Spring?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- APIs only need to be up-versioned when a breaking change is made. Breaking changes include:
  - Change in the format of the response data for one or more calls
  - Change in the request or response type (i.e., changing an integer to a float)
  - Removing any part of the API.
- There are multiple ways to version RESTful API-
  - One controller class with multiple methods having separate versions for mapping URLs.
  - One controller class with one method having separate versions number passed as path variables.
  - One controller class with one method having separate versions number passed as a custom request header.
  - Multiple controller classes marked with version names with their method names. 
- Breaking changes should always result in a change to the major version number for an API or content response type.
- Non-breaking changes, such as adding new endpoints or new response parameters, do not require a change to the major version number.
- Example of using two controller classes serving different versions-
```java
@RestController
@RequestMapping("/api/v1")
public class ControllerV1 {
  //...
}

@RestController
@RequestMapping("/api/v2")
public class ControllerV2 {
  //...
}
```
</blockquote> 

</details>

---
17. Which object is used as a base context in the Spring MVC application? Why?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `WebApplicationContext` object is used as the base object in the Spring MVC application.
- WebApplictionContext is an extension of ApplicationContext `public interface WebApplicationContext extends ApplicationContext`.
- WebApplicationContext is a web-aware ApplicationContext i.e., it has Servlet Context information. 
- In one web application, there can be multiple WebApplicationContext. 
- In one web application, there can be multiple DispatcherServlet, one for handling request and returns view whereas another which handle REST request & responses. 
- Each DispatcherServlet is associated with a single WebApplicationContext. 
- The WebApplicationContext configuration file `*-servlet.xml` is specific to the DispatcherServlet and a web application can have more than one DispatcherServlet configured to handle the requests and each DispatcherServlet would have a separate `*-servlet.xml` file to configure.
</blockquote> 

</details>

---
18. What is the difference between `applicationContext.xml` and `*-servlet.xml` in Spring Framework?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details> <summary> <b> Show Answer </b> </summary>

<blockquote> 
    
- `applicationContext.xml` defines the beans that are shared among all the servlets. 
- If our application has more than one servlet, then defining the common resources in the `applicationContext.xml` would make more sense.
- `*-servlet.xml` defines the beans that are related only to specific DispatcherServlet. 
- All our Spring MVC controllers are defined in this file.
- There is nothing wrong in defining all the beans in the `*-servlet.xml` if we are running only one DispatcherServlet in our web application.
</blockquote> 

</details>

---



