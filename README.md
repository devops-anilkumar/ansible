# ansible


### inventory : it is nothing but list of ip adress or dns names that you want ansible to mannage 


ansible by default installs  2.9 as by default on AMI'S will get python2 
always go with the latest version of ansible,which can be installed from tools/ansible/install.sh


ansible has a lot of pre defined variables and we need to use them to supply user name and password it has to use to authenticate to the nodes


### ansible_user     :  predefined variable for user name 
### ansible_password :predefined variable for password 


.....

variables should be passed to ansible by using the flag -e

    Ex:  ansiible -i INVENTORY all -e ansible_user=userName -e  ansible_pass=password
....

ansible is collection of  modules / collections : Whatever the task that you want  yo perform is already predefined , all you need is just to consume them. 

there are thousands of modules avaliable : -m shell. -m yum, -m service 