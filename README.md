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
