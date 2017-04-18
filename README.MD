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

## 变量说明

- modify_root_password: False --如果设置为True，就会修改操作系统密码。密码为root_password设置的值。
