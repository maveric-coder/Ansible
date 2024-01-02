# Ansible test file

trying ansible


for user_site.yml
cat /etc/passwd
sudo cat /etc/shadow
ssh -i ~/.ssh/ansible yaay@10.0.0.5
whoami
try to perform some sudo privelage commands
cat .ssh/authorized_key

edit the config file and add
remote_user = yaay


after that run the playbook directly
ansible-playbook user_site.yml

copy the user_site.yml to bootstrap.yml and remove the user part from user_site and remove all other plays from bootstrap.yml

remove update_only: and upgrade: from user_site.yml
and add changed_when: false on same level as when

### for roles:
1. copy the existing playbook for backup
2. define all the reoles in the user_site.yml playbook
3. create a directory named roles and create sub-directories for each roles
4. make new directory named tasks inside each directories inside roles
5. now switch to tasks dir inside base directory and create main.yml aka taskbook
6. copy the default_site.html from root file dir to roles/web_servers/files dir


### Host variables and Handlers
1. create a new dir host_vars
2. create host variable file node1@10.0.0.5.yml ...