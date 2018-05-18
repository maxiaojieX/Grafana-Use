
# Grafana

* ### [Linux安装](#install) 
* ### [安装包信息](#package) 
* ### [启动Grafana](#start)
* ### [开始使用](#use) 


<hr>
<br>
<h3 id="install">Linux安装</h2>
使用yum方式直接安装<br>
yum install https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-4.4.3-1.x86_64.rpm
<br><br>
<h3 id="package">安装包信息</h2>
二进制文件： /usr/sbin/grafana-server<br>
init.d 脚本： /etc/init.d/grafana-server<br>
环境变量文件： /etc/sysconfig/grafana-server<br>
配置文件： /etc/grafana/grafana.ini<br>
启动项： grafana-server.service<br>
日志文件：/var/log/grafana/grafana.log<br>
默认配置的sqlite3数据库：/var/lib/grafana/grafana.db<br>
<br><br>
<h3 id="start">启动Grafana</h2>
启动命令： sudo service grafana-server start<br>
(init.d脚本文件中默认指定了使用/etc/grafana/grafana.ini作为默认配置文件,不能将默认的grafana.ini作为配置文件使用，否则会报错，根据需要修改配置文件。配置文件附文档末)
<br><br>
<h3 id="use">开始使用</h2>
默认使用的端口为3000<br>
默认账户密码都为admin<br><br>
 创建一个数据库连接<br>
点击Data Sources菜单，添加一个数据源。根据需要添加数据源连接信息。<br><br>
创建一个仪表盘<br>
点击Dashboards-Home菜单，会显示已经创建并保存的仪表盘列表。
添加一个仪表，选择样式图形，点击Edit，编辑仪表名称。<br><br>
关键点：Metrics配置<br>
根据规则配置SQL<br>
SELECT<br>
	UNIX_TIMESTAMP(create_time) as time_sec,<br>
	load_value as value<br>
FROM<br>
	systemload_log<br>
ORDER BY create_time  ASC<br>
数据库表中必须有一个字段为时间或时间戳 as time_sec
想要展示的数据 as value

