title: "MYSQL 修改密码"
date: 2015-01-08 12:00:00
tags: MYSQL
category: MYSQL
---

控制面板\所有控制面板项\管理工具 >> 本地安全策略 >> IP 安全策略,在本地计算机

php code：
```bash
UPDATE mysql.user SET password=password(\''.$password.'\') where user=\''.$user.'\' limit 1
```

忘记密码：
1.关闭正在运行的MySQL。
2.打开DOS窗口，转到mysql\bin目录。
3.输入mysqld --skip-grant-tables回车。如果没有出现提示信息，那就对了。
4.再开一个DOS窗口(因为刚才那个DOS窗口已经不能动了)，转到mysql\bin目录。
5.输入mysql回车，如果成功，将出现MySQL提示符 。
6.连接权限数据库>use mysql; (>是本来就有的提示符,别忘了最后的分号)
7.改密码：> update user set password=password("123456") where user="root"; (别忘了最后的分号)
8.刷新权限(必须的步骤)>flush privileges。
9.退出，重新使用用户名root和刚才设置的新密码123456登陆。
