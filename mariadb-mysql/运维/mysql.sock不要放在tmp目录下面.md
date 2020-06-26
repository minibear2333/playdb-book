
执行命令，更改`mariadb.sock`文件位置，防止`/tmp`目录下文件被删除导致挂掉

``` BASH
sed -i "s/\/tmp\/mariadb.sock/\/data\/mariadb\/mariadb.sock/g" /etc/my.cnf.d/client.cnf 
sed -i "s/\/tmp\/mariadb.sock/\/data\/mariadb\/mariadb.sock/g" /etc/my.cnf
```

修改完确认上面命令中的两个文件是不是都成功修改了`mariadb.sock`的目录，为`/data/mariadb/mariadb.sock`，如果没有手动修改。
