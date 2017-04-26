# CIS for Ubuntu 14.04

## 说明

1. 这个ansible playbook主要是为了强化Ubuntu14.04系统，应该也适用于debian 8 和ubuntu16.04，但是我没测试。
2. 执行过程中会自动设置root和ubuntu用户的密码，密码设置参见变量说明章节。
3. 执行完成完成完成后，会禁用root通过ssh登录。只能通过普通用户登录。
4. 这个playbook是参见github上[cis-ubuntu-ansible](https://github.com/awailly/cis-ubuntu-ansible.git)

![http://media.giphy.com/media/7U1XfwZ94okRW/giphy.gif](http://media.giphy.com/media/7U1XfwZ94okRW/giphy.gif)

## 版本

Aansible：2.3

## 使用

- 编辑hosts文件，设置ubuntu组的ansible_ssh_host、ansible_ssh_user。当然你也可以在其他地方设置。
```
[ubuntu]
10.2.250.103 ansible_ssh_host=10.2.250.103 ansible_ssh_user=root
```
- 编辑group_vars/all文件，设置全局变量。
- 编辑group_vars/ubuntu文件，设置ubuntu组变量。

执行命令：
```
ansible-playbook -i hosts site.yml -k
SSH password: 	# 输入ansible_ssh_user密码
```

## 变量说明

- modify_root_password: False ----如果设置为```True```，就会修改操作系统密码。密码为```root_password```设置的值。
- net_ipv4_ip_forward: 0 ----如果服务器用来搭建openstack或docker，请将参数设置为 ```1```.
- net_ipv4_conf_all_rp_filter: 1 ----如果服务器用来搭建openstack或docker，请将参数设置为 ```0```.
- net_ipv4_conf_default_rp_filter: 1 ----如果服务器用来搭建openstack或docker，请将参数设置为 ```0```.
- activate_ufw: True ---- 如果关闭ufw，请将参数设置为 ```False``` .

## 其他
执行后有一些是检查用的，最好将执行日志保存，然后仔细查阅。
```
脚本执行后，会禁用ssh的root登录，所以执行前请先设置好非root用户密码。
```
因为本次安全加固未涉及到ubuntu用户的密码修改，所以请事先设置好复杂密码。
