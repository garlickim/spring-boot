# Externalized Configuration

Spring Boot는 Configuration을 여러가지 방식으로 지원하고, 각 방식마다 우선 순위가 존재한다.  
Configuration 방식에는 properties 파일, yml 파일, 환경 변수, Command-line arguments 이 있다.

##### Configuration 우선 순위를 하기와 같이 정의한다(많이 사용하는 방식에 대한 우선 순위만 정의함)  

~~~txt
우선순위 1 : Command line arguments.  --> java -foo=bar -jar OO.jar
우선순위 2 : Java System properties.  --> java -Dfoo=bar -jar OO.jar
우선순위 3 : 패키지 jar 외부에 위치한 properties 파일
우선순위 4 : 패키지 jar 내부에 위치한 properties 파일
~~~  
</br>

##### 정의한 property를 읽어오는 방식
1. Value annotation 이용
~~~java
@Value(${name})
~~~
2. Environment 이용
~~~java
@Autowired
private Environment env;

env.getProperty("name");
~~~
