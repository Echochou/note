### item2添加远程主机
```
/**
	创建一个目录 ， 用于存不同远程主机配置文件
	到.profile目录下
	host_name 是自己起的相应名字  在里面写执行连接到远程主机的命令   zz 保存并退出
	将编辑好的这个文件路径记下
	到 iterm2里 profiles --> open profiles --> edit profiles
**/

mkdir .profile  
cd .profile  
vi host_name                       
command 里配置 expect ~/.profile/host_21
```


##### ssh连接远程主机
```
 ssh -p端口 用户名@ip
 ssh -p58958 admin@112.74.209.200 
```
