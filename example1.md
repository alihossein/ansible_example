```yaml
---
- hosts: solr
  gather_facts: yes
  become : yes
  become_user: root
  connection : ssh
  vars : 
    usernmae : alihossein
  tasks:
    - name: install tree pacakge
      yum : 
        name : tree
        state : latest
    - name: install ntpd
      yum:
        name: ntp
        state : latest
      notify:
        Start Ntp
  handlers:
    - name: Start Ntp
      service:
        name: ntpd
        state : started
```
