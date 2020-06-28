### 中间件应急手册

mariadb/mysql、redis、rabbitmq、influxdb等存储中间件，keepalived、haproxy、nginx、j等负载中间件，以及jenkins相关知识，未来文档内容多了会拆开

> 此小册由编程三分钟技术小组成员合著而成，目前仍然在不断地充实和完备内容和质量当中，由编程伐木累成员牵头，由各大互联网公司和高校的成员组成。涵盖各技术领域内容。

> 欢迎大家补充完善，小组成员可直接编辑，非小组成员可以在任意你觉得合适的模块直接在**评论区留言**，参与编写可申请成为小组正式成员喔。

github位置 [playdb-book](https://github.com/pzqu/playdb-book)

投稿贡献请在[此页](https://www.kancloud.cn/coding3min/playdb/1756341)提交评论申请

也可以在[github](https://github.com/pzqu/playdb-book)上发起pr

github中[各手册链接](https://github.com/pzqu/playdb-book/blob/master/book.json)

### 目录

* [投稿大纲](投稿大纲.md)
* [时间同步](时间同步.md)
* [jenkins](jenkins)
    * [jenkins快速入门](jenkins/jenkins快速入门.md)
* [mariadb/mysql](mariadb-mysql)
    * [集群](mariadb-mysql/集群)
        * [快速拉起](mariadb-mysql/集群/快速拉起.md)
    * [主从](mariadb-mysql/主从)
        * [建立主从](mariadb-mysql/主从/建立主从.md)
        * [relaylog详解](mariadb-mysql/主从/relaylog.md)
        * [主从切换](mariadb-mysql/主从/主从切换.md)
        * [集群方案切换为互为主从](mariadb-mysql/主从/集群方案切换为互为主从.md)
        * [常见故障](mariadb-mysql/主从/常见故障.md)
        * [mysql的expire_logs_days参数引发的主从状态丢失问题](mariadb-mysql/主从/mysql的expire_logs_days参数引发的主从状态丢失问题.md)
    * [运维](mariadb-mysql/运维)
        * [忘记密码](mariadb-mysql/运维/忘记密码.md)
        * [备份数据库](mariadb-mysql/运维/备份数据库.md)
        * [重建mysql数据库的方法](mariadb-mysql/运维/重建mysql数据库的方法.md)
        * [mysql正确清理binlog日志的两种方法](mariadb-mysql/运维/mysql正确清理binlog日志的两种方法.md)
        * [mysql.sock不要放在tmp目录下面](mariadb-mysql/运维/mysql.sock不要放在tmp目录下面.md)


