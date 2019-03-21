切换配置文件需要访问config-server，即配置中心读取到github的配置信息
	http://localhost:8001/neo-config/dev
	返回：
		{"name":"neo-config","profiles":["dev"],"label":null,"version":"74750593125487fd8bb23697e20637d63fd5cb46","state":null,"propertySources":[{"name":"https://github.com/dewen2018/springcloud/config-repo/neo-config-dev.properties","source":{"neo.hello":"hello im dev update1"}}]}
直接查看配置文件中的配置信息：
	http://localhost:8001/neo-config-dev.properties
	返回：
		neo.hello: hello im dev update1
原理：仓库中的配置文件会被转换成web接口，访问可以参照以下的规则：
	/{application}/{profile}[/{label}]
	/{application}-{profile}.yml
	/{label}/{application}-{profile}.yml
	/{application}-{profile}.properties
	/{label}/{application}-{profile}.properties
	以neo-config-dev.properties为例子，它的application是neo-config，profile是dev。client会根据填写的参数来选择读取对应的配置。
	
	
对于client的配置：
	spring-cloud相关的属性必须配置在bootstrap.properties中，config部分内容才能被正确加载。因为config的相关配置会先于application.properties，而bootstrap.properties的加载也是先于application.properties。
问题：因为springboot项目只有在启动的时候才会获取配置文件的值，修改github信息后，client端并没有在次去获取，所以导致这个问题
Spring Cloud Config分服务端和客户端，服务端负责将git（svn）中存储的配置文件发布成REST接口，客户端可以从服务端REST接口获取配置。但客户端并不能主动感知到配置的变化，从而主动去获取新的配置。客户端如何去主动获取新的配置信息呢，springcloud已经给我们提供了解决方案，每个客户端通过POST方法触发各自的/refresh。
增加了spring-boot-starter-actuator包，spring-boot-starter-actuator是一套监控的功能，可以监控程序在运行时状态，其中就包括/refresh的功能。