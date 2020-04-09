# ansible_example


#### disable selinux

ansible-playbook disable_selinux_playbook.yml  --extra-vars "hosts=airflow"


#### start and add new ips to firewall
ansible-playbook firewall_playbook.yml  --extra-vars "hosts=airflow"

