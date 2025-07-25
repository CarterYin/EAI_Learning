# 这是Linux的学习步骤
# 基于这个视频合集：https://www.bilibili.com/video/BV1ZZ37zdEp2?p=6&vd_source=4fd6c4265e65c0785c912874692a3971
# 设备基于rockylinux系统，vmware station,xshell
## Step1：下载rockylinux,xshell,vmware station（以及常用的Ubuntu，centos等操作系统）
## Step2：VMware的三种网络模式
- 桥接-vnet0
- 仅主机-vnet1
- NAT-vnet8
## Step3：VMware快照与克隆
- 最多不超过3个快照
- Linux注意克隆后的主机名和MAC地址需要不同
## Step4：Linux内核与发行版
- Linux操作系统=Linux内核+GNU软件+x windows+sendmail+http web等等
## Step5：Linux学习方法
- 由浅入深，空杯心态。
- 共有500多个命令，常用只有50个，高频甚至只有20多个，不必记太多。
- 命令结合英文原意来记，做成笔记。
- 重点，热门技术，过时技术等等。
## Step6：Linux登录之本地登录
- 图形和文本登录
- shutdown -h now
## Step7：Linux远程登录
- ssh工具
## Step8：Bash Shell Linux命令构成
- shell的种类
- 常用命令echo $BASH ，more /etc/shells等
- #表示超级管理员，$表示普通用户
- shell命令的结构
- Linux系统环境变量和登录信息提示
## Linux文件层次结构
## Linux命令补全及长命令换行
- bash-completion命令行补全
- \用于长命令换行
- 多命令执行1 command1;command2 前后命令无关
- 多命令执行2 command1 && command2 后一个命令执行的前提是前一个命令执行成功
- 多命令执行3 command1 || command2 后一个命令执行的前提是前一个命令执行失败
- 命令帮助 man page

  
  
