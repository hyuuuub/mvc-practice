# mvc-practice

스프링 MVC 프로젝트로 게시판을 구축한 프로젝트

https://gmlwjd9405.github.io/2018/05/09/mysql-workbench-guide.html


### pom.xml 수정

- spring version -> **4.3.2.RELEASE** 로 수정
- junit version -> **4.12** 로 수정
- JSON 사용을 위한 Jackson 라이브러리 추가
- MySQL과 MyBatis, JDBC 등의 라이브러리 추가

```xml
<!--Jackson -->
<dependency>
	<groupId>com.fasterxml.jackson.core</groupId>
	<artifactId>jackson-databind</artifactId>
	<version>2.9.9</version>
</dependency>

<!-- MySQL -->
<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
	<version>6.0.5</version>
</dependency>
        
<!-- MyBatis -->
<dependency>
	<groupId>org.mybatis</groupId>
	<artifactId>mybatis</artifactId>
	<version>3.4.6</version>
</dependency>
		
<!-- MyBatis-Spring -->
<dependency>
	<groupId>org.mybatis</groupId>
	<artifactId>mybatis-spring</artifactId>
	<version>1.3.2</version>
</dependency>
        
<!-- Spring JDBC -->
<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-jdbc</artifactId>
	<version>${org.springframework-version}</version>
</dependency>

<!-- Spring Test -->
<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-test</artifactId>
	<version>${org.springframework-version}</version>
	<scope>test</scope>
</dependency>
```



### Root-context.xml 수정

- root-context.xml은 웹과 관련되지 않은 자원들에 대한 설정을 입력하는 곳이다.

- Namespaces 탭에서 아래를 모두 체크해준다.

```xml
  aop
  beans
  context
  jdbc
  mybatis-spring
```

- Source 탭에서 DataSource와 SqlSessionFactoryBean을 설정한다.

```xml
<!-- MySQL dataSource -->
<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
	<property name="driverClassName" value="com.mysql.cj.jdbc.Driver"></property>
	<property name="url" value="jdbc:mysql://데이터베이스 주소:포트번호/스키마이름?useSSL=false&amp;serverTimezone=UTC">
	</property>
	<property name="username" value="MySQL 계정"></property>
	<property name="password" value="비밀번호"></property>
</bean>        
        
 
 
<!-- 자신의 PC(로컬)에 MySql을 설치했을 경우 -->
<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
	<property name="driverClassName" value="com.mysql.cj.jdbc.Driver"></property>
	<property name="url" value="jdbc:mysql://127.0.0.1:3306/스키마이름?useSSL=false&amp;serverTimezone=UTC">
	</property>
	<property name="username" value="MySQL 계정"></property>
	<property name="password" value="비밀번호"></property>
</bean>
```

