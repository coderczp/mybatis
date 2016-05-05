# mybatis 映射文件自动加载
mybatis mapper xml auto reload

###切莫用于生产环境（后果自负）！

* mybatis映射文件热加载（发生变动后自动重新加载）.

* 方便开发时使用，不用每次修改xml文件后都要去重启应用.

* 特性：
 * 支持不同的数据源。
 * 双线程实时监控，一个用来监控全局，一个用来实时监控热点文件。（100ms）（热点文件2分钟内没续修改自动过期）
 * 对于CPU不给力和映射文件庞大的应用，有一定程度的性能问题。

###使用方式(很简单)
1. 复制文件到自己的工程中 MybatisXmlMapperAutoReloader.java
2. spring添加配置 `<bean class="com.thomas.mybatis.MybatisXmlMapperAutoReloader" ></bean>`

## cxxxx
	<!-- mybatis自动热加载 -->
	`<bean class="com.thomas.mybatis.MybatisXmlMapperAutoReloader" >`
	
		<!-- 设置是否启用: 默认启用 -->
		<property name="enableAutoReload" value="${mybatis.enableAutoReload}" />
	
		<!-- 设置sqlSessionFactory -->
		<property name="sqlSessionFactory" ref="sqlSessionFactory" />
	
		<!-- 设置映射文件地址 -->
		<property name="mapperLocations" value="classpath*:mybatis/bean/mapper/*.xml" />
	</bean>

