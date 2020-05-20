1.代码中包含安全模块，如果不需要使用安全，可在main函数中注释掉loginWithKerberos方法即可.  
2.如果使用了安全，那么需要在windows的c:windows下放置对应集群的/etc/krb5.conf并改名为krb5.ini并重启ide环境.  
3.正常使用代码需要在本地配置HADOOP_HOME和winutils相关，百度有很多相关的解释咱不赘述.  
4.这个安全代码支持zk强认证与非强认证模式.  
5.建议从集群中取出coresite.hbasesite,hdfssite,hyperbase.keytab放入对应的resource目录中，如果需要查看日志，那么添加一下log4j.properties.  
6.将core-sixt.xml中的如下配置属性注释掉. 
>     <property>
>         <name>hadoop.security.group.mapping.ldap.bind.password.file</name>
>         <value>/etc/hdfs1/conf/ldap-conn-pass.txt</value>
>     </property>
7.如果遇到报错：OAuth2 configuration not found,将core-site.xml中的如下配置属性改成false. 
>     <property>
>         <name>hadoop.security.authentication.oauth2.enabled</name>
>         <value>true</value>
>     </property>
>     <property>
>         <name>hadoop.security.authentication.web.oauth2.enabled</name>
>         <value>true</value>
>     </property>
