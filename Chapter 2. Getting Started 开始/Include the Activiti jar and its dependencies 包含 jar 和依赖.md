##Include the Activiti jar and its dependencies 包含 jar 和依赖

想要包含 jar 和依赖，建议使用 [Maven](http://maven.apache.org/) (或者 [Ivy](http://ant.apache.org/ivy/)) 来简化依赖管理。[http://www.activiti.org/community.html#maven.repository](http://www.activiti.org/community.html#maven.repository) 中包含了需要的 jar

如果不想用 Maven，你也可以自己把这些 jar 引入到你的项目中。Activiti 下载 zip 包包含了一个 libs 目录，包含了所有 Activiti的 jar 包（和源代码 jar 包）。依赖没有用这种方式发
布。 Activiti 引擎必须的依赖如下所示（通过 mvn dependency:tree生成）：

	org.activiti:activiti-engine:jar:5.17.0
	+- org.activiti:activiti-bpmn-converter:jar:5.17.0:compile
	|  \- org.activiti:activiti-bpmn-model:jar:5.17.0:compile
	|     +- com.fasterxml.jackson.core:jackson-core:jar:2.2.3:compile
	|     \- com.fasterxml.jackson.core:jackson-databind:jar:2.2.3:compile
	|        \- com.fasterxml.jackson.core:jackson-annotations:jar:2.2.3:compile
	+- org.activiti:activiti-process-validation:jar:5.17.0:compile
	+- org.activiti:activiti-image-generator:jar:5.17.0:compile
	+- org.apache.commons:commons-email:jar:1.2:compile
	|  +- javax.mail:mail:jar:1.4.1:compile
	|  \- javax.activation:activation:jar:1.1:compile
	+- org.apache.commons:commons-lang3:jar:3.3.2:compile
	+- org.mybatis:mybatis:jar:3.2.5:compile
	+- org.springframework:spring-beans:jar:4.0.6.RELEASE:compile
	|  \- org.springframework:spring-core:jar:4.0.6.RELEASE:compile
	+- joda-time:joda-time:jar:2.6:compile
	+- org.slf4j:slf4j-api:jar:1.7.6:compile
	+- org.slf4j:jcl-over-slf4j:jar:1.7.6:compile 

注意：只有使用了 [mail service task](http://www.activiti.org/userguide/index.html#bpmnEmailTask) 才必须引入 mail 依赖jar。

在 [Activiti 源代码](https://github.com/Activiti/Activiti)执行 mvn dependency:copy-dependencie 依赖将会轻松下载


