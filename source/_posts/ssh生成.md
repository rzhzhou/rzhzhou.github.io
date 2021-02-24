---
title: ssh密钥生成
date: 2021-02-23 15:12:59
tags:
---

如何生成SSH key
==============

SSH key提供了一种与GitHub通信的方式，通过这种方式，能够在不输入密码的情况下，将GitHub作为自己的remote端服务器，进行版本控制.

步骤
==============

* 检查SSH keys是否存在
* 生成新的ssh key
* 将ssh key添加到GitHub中

第一步：检查ssh keys是否存在
------------------

进入到ssh目录下(在根目录下执行)
```
cd ~/.ssh
```
输入ls查看该目录下文件，如果有文件 `id_rsa.pub` 或 `id_dsa.pub` (例如下)，则直接进入步骤3将SSH key添加到GitHub中，否则进入第二步生成SSH key
```
rzhzhou@DESKTOP-VMA5FA6:/mnt/d/cmder$ cd ~/.ssh
rzhzhou@DESKTOP-VMA5FA6:~/.ssh$ ls
id_rsa  id_rsa.pub  known_hosts
```




第二步: 生成新的ssh key
-----------------

在命令行中输入以下命令生成`ssh key`(根目录下)

```
rzhzhou@DESKTOP-VMA5FA6:~$ ssh-keygen -t rsa
```

会出现以下信息, 一路enter 或者y.

```
Generating public/private rsa key pair.                                      
Enter file in which to save the key (/home/rzhzhou/.ssh/id_rsa):             
/home/rzhzhou/.ssh/id_rsa already exists.                                    
Overwrite (y/n)? y                                                           
Enter passphrase (empty for no passphrase):                                  
Enter same passphrase again:                                                 
Your identification has been saved in /home/rzhzhou/.ssh/id_rsa.             
Your public key has been saved in /home/rzhzhou/.ssh/id_rsa.pub.             
The key fingerprint is:                                                      
SHA256:gKAPmDU3u5ajZIQxDnbr8aPV3a4z82Vi/2ahc5Ba7PU rzhzhou@DESKTOP-VMA5FA6   
The key's randomart image is:                                                
+---[RSA 2048]----+                                                          
|+.+.o            |                                                          
|=B.+.+           |                                                          
|*..oo .          |                                                          
| +. oo... .      |                                                          
|  +.=+ .S. .. .  |                                                          
| o oo..   .  = o |                                                          
|  ..       ++o+ o|                                                          
|         +o.=+ +E|                                                          
|         .=. .*. |                                                          
+----[SHA256]-----+                                                          
```
按enter 是选择默认情况.下面只需要查看生成的ssh key就可以了,下面只需要找到ssh key即可.

__查看`id_rsa`文件__

```
cat ~/.ssh/id_rsa.pub
```

会出现类型以下信息：（`id_rsa.pub`文件内容）

    ssh- rsaAAAAB3NzaC1yc2EAAAADAQABAAABAQDLAgA7xxvU3jodJGEcJ+biK/rRaAGSIFo6tqUNtMmbDUzUWJsSqEiAYzlMgcZNYd6xynq/SDHiwUAPU2NsLqwDz6aPpk5vHXAC+Y+XISH+vbBDYrx/Zq8UhnuqbaBLjNdLK2rhJQlZGQsK78Uv5PogprpW0/hMRKZ08fq7Sbh37dHnAqQLM2+ky0Ag75LfcSyuMpYVphaBboaxIBHdw/pbHC+6Ku3AV/HRoZAnqkKtCOnYuJPGEta1YzMYDCqZODdQQMpKqTyJwmixCe0ceLv7piWtilLEfm4Os56JH4t9K/eVa1Y+MtoUEeoKVPn+Q1bnMo9bcs8rZf7o8T4ZLZPx rzhzhou@DESKTOP-VMA5FA6  


第三步：将ssh key添加到GitHub中
-----------------------------  

<img src="img/1.png">  

三步完成就添加成功了.