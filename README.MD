# CIS for Ubuntu 14.04

## 先决条件

这个ansible playbook主要是为了强化Ubuntu14.04系统，应该也适用于debian 8 和ubuntu16.04，但是我没测试。ansible最低版本为2.3.

## 使用

- 编辑hosts文件，设置ubuntu组的ansible_ssh_host、ansible_ssh_user、ansible_ssh_pass。当然你也可以在其他地方设置。
```
[ubuntu]
10.2.250.103 ansible_ssh_host=10.2.250.103 ansible_ssh_user=root ansible_ssh_pass=xxx
```
- 编辑group_vars/all文件，设置全局变量。
- 编辑group_vars/ubuntu文件，设置ubuntu组变量。

执行命令：
```
ansible-playbook -i hosts site.yml 
```

## 变量说明

- modify_root_password: False ----如果设置为```True```，就会修改操作系统密码。密码为```root_password```设置的值。
- net_ipv4_ip_forward: 0 ----如果服务器用来搭建openstack或docker，请将参数设置为 ```1```.
- net_ipv4_conf_all_rp_filter: 1 ----如果服务器用来搭建openstack或docker，请将参数设置为 ```0```.
- net_ipv4_conf_default_rp_filter: 1 ----如果服务器用来搭建openstack或docker，请将参数设置为 ```0```.
- activate_ufw: True ---- 如果关闭ufw，请将参数设置为 ```False``` .

## 其他
执行后有一些是检查用的，最好将执行日志保存，然后仔细查阅。
