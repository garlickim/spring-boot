# Spring Boot Starter

Starter는 어플케이션 개발에 사용할 수 있는 편리한 dependancy 집약체.  
공식적으로 제공하는 Starter들은 spring-boot-starter-* 로 시작한다.

기본적인 Starter를 사용한 Bean 등록 예제이다.

~~~xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter</artifactId>
        <version>2.1.5.RELEASE</version>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <version>1.5.10.RELEASE</version>
        <scope>test</scope>
    </dependency>
~~~

* 하위 @Configuration, @EnableAutoConfiguration, @ComponentScan의 사용은 @SpringBootApplication으로 대체 가능  

~~~java 
//@SpringBootApplication
@Configuration
@EnableAutoConfiguration
@ComponentScan
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
~~~  


방법1) ==============================================================================

~~~java
@Controller
public class SampleController {

    // sample controller 생성
}
~~~

방법2) ==============================================================================

~~~java
public class SampleController {

    // sample controller 생성
}
~~~

~~~java
@Configuration
public class SampleConfiguration {

    @Bean
    public SampleController sampleController(){
        return new SampleController();
    }
}
~~~

@ComponentScan - 해당 anotation이 붙어있는 위치의 클래스 패키지 하위를 탐색하여 모두 Component로 등록한다.  
@Controller anotation을 제거하면 @Configuration anotation이 있는 클래스에서 @Bean anotation을 사용하여 Component로 등록한다.
