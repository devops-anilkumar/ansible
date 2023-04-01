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

### ansible can be approached in 2 ways :
.....
1) manual approach      : using ansible command  : with this you can excute one command at a time.
2) Automated approach   : using ancible playbook : with this you can excute all the set of tasks that need to be excuted , things that will happend in the declared approach 
.......

### Automated Approach : This uses Play book

......
playbooks are written using a language called YAML

YAML is just markup language ; Markup language is nothing a presentation language 

......

'YAML' is indentation specific.

### what is a playbook ?
....
* playbook : it is a list of plays.  (thats why its always start with - )
*  play     : it is a list of tasks.
*  task  :  task is nothing but an action that we wish to perform 
.....

### how to run a playbook ?
.....
ansible-playbook -i inv -e ansible_user=userName -e  ansible_pass=password name of the playbook.yml

### ansible facts :
.....
facts are the properties of the remote node that you ansible is going to collect : based on these facts collected ansible decides weather to perform the action or not 

facts that are callected by ansible?
Ansible uses a module called as setup using that we can check the collected facts 


$ ansible -i inventory all -e ansible_user=centos -e ansible_password=DevOps321 -m setup
