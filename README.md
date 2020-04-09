# ansible_example


#### disable selinux

ansible-playbook disable_selinux_playbook.yml  --extra-vars "hosts=airflow"


#### start and add new ips to firewall
ansible-playbook firewall_playbook.yml  --extra-vars "hosts=airflow"


#### install general packages
ansible-playbook install_general_os_packages_playbook.yml  --extra-vars "hosts=airflow"


