```yaml
--- # install solr dependencies
- hosts: solr
  gather_facts: yes
  become : yes
  become_user: root
  connection : ssh
  vars : 
    solr_download_path : /opt/ali
  handlers:
    - name: start_ntp_handler
      service:
        name: ntpd
        state : started
  tasks:
    - name: install epel-release package (Extra Packages for Enterprise Linux)
      yum : 
        name : epel-release
        state : latest
    - name: Disable SELinux
      selinux:
        state: disabled
    - name: Install Telnet
      yum:
        name : telnet
        state: latest
    - name: Install htop
      yum:
        name : htop
        state: latest    
    - name:  install java-1.8.0-openjdk
      yum:
        name: java-1.8.0-openjdk
        state: latest
    - name: Install java-1.8.0-openjdk-devel 
      yum:
        name: java-1.8.0-openjdk-devel 
        state: latest
    - name: Install lsof
      yum:
        name: lsof
        state: latest
    - name : Install ntp
      yum :
        name: ntp
        state : latest
      notify:
        start_ntp_handler
    - name:
      unarchive:
        src: http://archive.apache.org/dist/lucene/solr/7.4.0/solr-7.4.0.tgz
        dest: /opt/ali
        remote_src: yes
    - name: Install Zookeeper
      unarchive:
          src: http://apache.mirror.anlx.net/zookeeper/zookeeper-3.4.14/zookeeper-3.4.14.tar.gz
          dest: /opt/ali
          remote_src: yes
    - name: Swappiness setting recommendation (echo "vm.swappiness=1" >> /etc/sysctl.conf & echo "1" > /proc/sys/vm/swappiness)
      sysctl:
        name: vm.swappiness
        value: 1
        state: present

```
