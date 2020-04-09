```yaml
---

- hosts: reporting
  remote_user: root
  become: yes
  # become_method: sudo
  name: Firewall Playbook
  gather_facts: false
  connection: ssh
  tasks:
      - name: start and enable firewall
        service:
          name: firewalld
          state: started
          enabled: yes 
      - name: add Ips to firewalld
        firewalld:
          source: "{{item}}"
          zone: trusted
          permanent: yes
          state: enabled
        with_items:
          - 192.168.100.142
          - 192.168.100.143
          - 192.168.100.144
      - name: reload Firewalld
        service:
          name: firewalld
          state: reloaded
          enabled: yes 
