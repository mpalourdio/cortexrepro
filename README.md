1.  `git clone` this project
2. Download GraalVM for JDK 21 Community 21.0.2 : https://github.com/graalvm/graalvm-ce-builds/releases/download/jdk-21.0.2/graalvm-community-jdk-21.0.2_linux-x64_bin.tar.gz
3. Add it to your PATH and export JAVA_HOME

```bash
export JAVA_HOME=/path/to/graalvm/untared
export PATH=$JAVA_HOME/bin:$PATH
```

4. `cd /path/to/cloned/repo`
5. `./mvnw clean -Pnative native:compile` or `./mvnw -e -X clean -Pnative native:compile` for more logging
6. Wait a few minutes
8. Run `target/cortex`

The application fails to load with

```log
2026-06-10T11:49:34.031+02:00  WARN 46085 --- [cortex] [           main] o.s.c.support.GenericApplicationContext  : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'org.springframework.aop.config.internalAutoProxyCreator': java.panw.PanwHooks.HookArgs2(Ljava/lang/Object;Ljava/lang/Object;)V [symbol: Java_java_panw_PanwHooks_HookArgs2 or Java_java_panw_PanwHooks_HookArgs2__Ljava_lang_Object_2Ljava_lang_Object_2]
Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'org.springframework.aop.config.internalAutoProxyCreator': java.panw.PanwHooks.HookArgs2(Ljava/lang/Object;Ljava/lang/Object;)V [symbol: Java_java_panw_PanwHooks_HookArgs2 or Java_java_panw_PanwHooks_HookArgs2__Ljava_lang_Object_2Ljava_lang_Object_2]
at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:607)
at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
at org.springframework.context.support.PostProcessorRegistrationDelegate.registerBeanPostProcessors(PostProcessorRegistrationDelegate.java:265)
at org.springframework.context.support.AbstractApplicationContext.registerBeanPostProcessors(AbstractApplicationContext.java:806)
at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:609)
at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
at com.example.cortex.CortexApplication.main(CortexApplication.java:10)
at java.base@25.0.2/java.lang.invoke.LambdaForm$DMH/sa346b79c.invokeStaticInit(LambdaForm$DMH)
Caused by: java.lang.UnsatisfiedLinkError: java.panw.PanwHooks.HookArgs2(Ljava/lang/Object;Ljava/lang/Object;)V [symbol: Java_java_panw_PanwHooks_HookArgs2 or Java_java_panw_PanwHooks_HookArgs2__Ljava_lang_Object_2Ljava_lang_Object_2]
at org.graalvm.nativeimage.builder/com.oracle.svm.core.jni.access.JNINativeLinkage.getOrFindEntryPoint(JNINativeLinkage.java:152)
at org.graalvm.nativeimage.builder/com.oracle.svm.core.jni.JNIGeneratedMethodSupport.nativeCallAddress(JNIGeneratedMethodSupport.java:41)
at java.panw.PanwHooks.HookArgs2(Native Method)
at org.springframework.beans.AbstractPropertyAccessor.setPropertyValues(AbstractPropertyAccessor.java)
at org.springframework.beans.AbstractPropertyAccessor.setPropertyValues(AbstractPropertyAccessor.java:79)
at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1737)
at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1454)
at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:599)
... 15 more
```
