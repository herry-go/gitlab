# gitlab
 ## 1.gitlab镜像拉取  
```
docker pull gitlab/gitlab-ce
```
 ## 2.运行gitlab镜像  
```
docker run -d  -p 443:443 -p 18448:18448 -p 222:22 --name gitlab --restart always -v /gitlab/config:/etc/gitlab -v /gitlab/logs:/var/log/gitlab -v /gitlab/data:/var/opt/gitlab gitlab/gitlab-ce
```
 ## 3.配置  
`1、 编辑 gitlab.rb配置文件`
```
vim /gitlab/config/gitlab.rb
```
`2、添加external_url`
```
external_url 'http://218.244.148.241:18448'
```
`3、添加访问地址和端口`
```
gitlab_rails['gitlab_ssh_host'] = '218.244.148.241:18448'
gitlab_rails['gitlab_shell_ssh_port'] = 222
```
`4、保存配置文件并退出`
```
:wq
```
 ## 4.重启  
```
docker restart gitlab
```
 ## 5.git命令
 ```
1.git init
2.git add .
3.git commit -m 'first commit'
4.git remote add origin 你的远程库地址
5.git pull --rebase origin master 获取远程库与本地同步合并（如果远程库不为空必须做这一步，否则后面的提交会失败
6.git push -u origin master
```
 
