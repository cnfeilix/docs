前提：本地安装好本地git客户端，在github.com上注册好帐号，并且建立了仓库（带有README.md和license）

1.在本地创建ssh key
	打开Git Bash
	输入命令：使用的邮箱地址要与github.com上的保持一致
	$ ssh-keygen -t rsa -b 4096 -C "84311848@qq.com"
	终端输出：
	$ Generating public/private rsa key pair.
	$ Enter file in which to save the key (/c/Users/feilix/.ssh/id_rsa):这里直接回车，使用默认文件名
	$ Created directory '/c/Users/feilix/.ssh'.
	$ Enter passphrase (empty for no passphrase):这里直接回车，不使用密码
	$ Enter same passphrase again:这里直接回车，不使用密码
	$ Your identification has been saved in /c/Users/feilix/.ssh/id_rsa.
	$ Your public key has been saved in /c/Users/feilix/.ssh/id_rsa.pub.
	$ The key fingerprint is:
	$ SHA256:vtyjpohNmynYl+Awo2NkKz985y32KePLnNApbjD9FVY 84311848@qq.com
	$ The key's randomart image is:
	$ +---[RSA 4096]----+
	$ |                 |
	$ |          E      |
	$ |         .       |
	$ |        o        |
	$ |   .   .S.       |
	$ |+o+ .. o.        |
	$ |+O.++oo..        |
	$ |=o*==XB+.+.      |
	$ |ooo*B=OOB...     |
	$ +----[SHA256]-----+
2.将ssh key添加到ssh-agent
	ssh-agent是本地git客户端程序的一部分，用于代理与git服务器的ssh认证。
	a.让ssh-agent处于运行状态
		打开Git Bash
		输入命令：
		$ eval "$(ssh-agent -s)"
		终端输出：
		Agent pid 线程id
	b.添加ssh key文件到ssh-agent
		输入命令：
		$ ssh-add ~/.ssh/id_rsa
		终端输出：
		$ Identity added: /c/Users/feilix/.ssh/id_rsa (/c/Users/feilix/.ssh/id_rsa)
	
3.将ssh key添加到GitHub帐号
	打开Git Bash
	输入命令：复制公钥文件的内容
	$ clip < ~/.ssh/id_rsa.pub
	打开GitHub网站
	Personal settings->SSH and GPG keys->New SSH key
	
4.将GitHub仓库（项目）同步到本地
	在本地要放置的文件夹下，右键打开Git Bash
	输入命令：
	$ git clone git@github.com:cnfeilix/test-netty.git
	
	