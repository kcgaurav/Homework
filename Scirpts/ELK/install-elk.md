---
- name: Install ELk
  hosts: elk
  remote_user: azadmin
  become: true
  tasks:

    - name: Intall docker.io
      apt:
        update_cache: yes
        name: docker.io


    - name: Install pip3
      apt:
        name: python3-pip


    - name: Install Docker python module
      pip:
        name: docker


    - name: Increase Virt Memory
      sysctl:
        name: vm.max_map_count
        value: 262144

    - name: Download Docker
      docker_container:
        name: elk
        image: sebp/elk:761
        state: started
        restart_policy: always
        published_ports:
         - 5601:5601
         - 9200:9200
         - 5044:5044

    - name: Enabled Docker Service
      systemd:
        name: docker
        enabled: yes