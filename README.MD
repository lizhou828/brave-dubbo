## Zipkin分布式日志跟踪(brave客户端)

运行环境：
```
   JDK 1.8
```


源码地址：
```
    https://github.com/lizhou828/brave-dubbo
```

前置条件：
```
    提前安装好zipkin服务端并启动，默认端口号是9411，
    zipkin服务端源码地址： https://github.com/openzipkin/zipkin/tree/master/zipkin-server
    zipkin是springboot项目，该jar包可直接通过java -jar zipkin.jar启动。启动完成后可访问 http://ip:9411查看。
    
    linux下：
        wget  -O zipkin.jar 'https://search.maven.org/remote_content?g=io.zipkin.java&a=zipkin-server&v=LATEST&c=exec'
        java -jar zipkin.jar  ## In-Memory方式存储
```

使用步骤：

### maven添加该项目jar包（自己打包安装到本地仓库）
```xml
        <dependency>
            <groupId>io.zipkin.brave</groupId>
            <artifactId>brave-dubbo</artifactId>
            <version>1.0.0-SNAPSHOT</version>
        </dependency>
```

### spring中配置
    
* 方式一
```
    <bean id="brave" class="com.github.kristofa.brave.dubbo.BraveFactoryBean" p:serviceName="serviceName" p:zipkinHost="http://127.0.0.1:9411/" p:rate="1.0" />
```
* 方式二
```
    <bean id="brave" class="com.github.kristofa.brave.dubbo.BraveFactoryBean" >
        <property name="serviceName" value="serviceName"/>
        <property name="zipkinHost" value="http://127.0.0.1:9411/"/>
        <property name="rate" value="1.0"/>
    </bean>
```


### 参考文档:
[http://www.tuicool.com/articles/f2qAZnZ](http://www.tuicool.com/articles/f2qAZnZ)
