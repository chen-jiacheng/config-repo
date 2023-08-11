# config-repo
> 一个 spring-cloud-config-server 的 git 配置仓库。

## 优先级
1. application.properties
2. application-{profile}.properties
3. {application}-{profile}.properties

## 构建配置服务服务端
1. 引入依赖
```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-config-server</artifactId>
</dependency>
```
2. 引导类注解
```java
@EnableConfigServer
```
3. 添加配置
```properties
# application.properties
server.port=8071
spring.application.name=config-server
spring.profiles.active=git
spring.cloud.config.server.git.uri=https://github.com/chen-jiacheng/config-repo
```

## 构建配置服务客户端
1. 引入依赖
```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-config</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-bootstrap</artifactId>
</dependency>
```
2. 添加配置
```properties
# bootstrap.properties
spring.application.name=some-service
server.port=8080
spring.profiles.active=dev
spring.config.import=optional:configserver:http://127.0.0.1:8888
```
