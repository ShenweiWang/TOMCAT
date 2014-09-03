#Tomcat

##初始化

###初始化ClassLoader

StandardClassLoader继承URLClassLoader将在Tomcat8.0.x去除

1.创建commonLoader

commonLoader (名称:common.loader 父loader：null JMX：Catalina:type=ServerClassLoader,name=common)
->加载${catalina.base}/lib,${catalina.base}/lib/*.jar,${catalina.home}/lib,${catalina.home}/lib/*.jar

2.创建catalinaLoader
catalinaLoader(名称：server.loader 父loader：commonLoader JMX：Catalina:type=ServerClassLoader,name=server)->加载:null

3.创建sharedLoader
sharedLoader(名称：shared.loader 父loader：commonLoader JMX：Catalina:type=ServerClassLoader,name=shared)->加载:null

4.设置当前线程的ClassLoader为catalinaLoader

Thread.currentThread().setContextClassLoader(catalinaLoader);

