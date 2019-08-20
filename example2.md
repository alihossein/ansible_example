``` ansible
--- # install and restart Nginx
- hosts: solr
  gather_facts: yes
  become : yes
  become_user: root
  connection : ssh
  tasks:
    - name: install Nginx pacakge
      yum : 
        name : nginx
        state : latest
    - name: enable and restart nginx
      service:
        name: nginx
        enabled: yes
        state : restarted
```
