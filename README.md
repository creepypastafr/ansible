# ansible

#install ansible
apt install ansible
#verif de l'install
ansible --version

infra1 192.168.177.129
web1 192.168.177.131
db1 192.168.177.132
ansible 192.168.177.130

ansible-playbook -i inventory playbook.yml

faire clé ssh et se connecter sur serveur à gérer

faire fichier -> inventory
ajouter
#
mon_groupe]
monserveur ansible_host=web1 ansible_connection=ssh
#

intégrer le serveur et se connecter en ssh
ansible -m ping -i inventory all


monserveur ansible_host=192.168.63.130 ansible_connection=ssh ansible_ssh_username=user ansible_ssh_password=resu

user@user-virtual-machine:~/mon_projet$ tree
.
├── inventory
├── playbook.yml
└── roles
    └── common
        └── tasks
            └── main.yml


faire clé ssh et se connecter sur serveur à gérer

faire fichier -> inventory
ajouter
#
mon_groupe]
monserveur ansible_host=web1 ansible_connection=ssh
#

intégrer le serveur et se connecter en ssh
ansible -m ping -i inventory all

#lancer le playbook
ansible-playbook -i inventory playbook.yml

#exemple inventory
monserveur ansible_host=192.168.63.130 ansible_connection=ssh ansible_ssh_username=user ansible_ssh_password=resu
monserveur ansible_host=192.168.63.130 ansible_connection=ssh 

#tree exemple du playbook
user@user-virtual-machine:~/mon_projet$ tree

├── inventory
├── playbook.yml
└── roles
    └── common
        └── tasks
            └── main.yml

#exemple playbook
- hosts: mon_groupe
  roles:
    - role: common
    - name: "Ce playbook installe LAMP et Wordpress"              

                dans ce fichier main.yml:
    - name: Installation utilitaires
      become: yes
      apt:
        name:
          - htop
          - screen
          - open-vm-tools
          - dnsutils
          - curl
          - tree
          - net-tools
          - iptables
          - iptables-persistent
        state : present
        update_cache: yes
        cache_valid_time: 3600

    - name: Mise à jour système
      become: yes
      apt:
        upgrade: yes



Dockerhub équivalent pour ansible : http://galaxy.ansible.com
iptables -t nat -A PREROUTING -i vmbr0 -p tcp --dport 50500 -j DNAT --to 192.168.222.2:50500

Notes by Julien

1) Installation Ansible
Sur le CLIENT, installer pip3 :
    sudo apt install python3-pip
Puis installer ansible :
    sudo pip3 install ansible
Tester le bon fonctionnement d'ansible :
    ansible --version
    
Repo Git : https://github.com/xila76/ansible_wordpress

nano home/usr/mon_projet/roles/common/tasks/main.yml
- name: installation des packets htops screen open-vm-tools
  become: yes
  apt:
    name:
      - htops
      - screen
      - open-vm-tools
    state: present
    update_cache: yes
    cache-valid-time: 3600


git:

#crer un dossier git
    git init 
#add tout les fichier dans le dossier 
    git add .
#save
    git commit -m "mon commit"
#donner le lien du git pour le push
    git remote add origin "lien du git avec le dossier" 
#envoyer sur le git en ligne ce qu'on a fait dans la master
    git push origin master
#pour la co plus de mdp donc create token dans les setting de git

 A faire : 
 
sur "infra1" :
  Docker
  Gitlab
  Bonus : AWX
sur "web1" :
  un serveur web (au choix apache/nginx)
  PHP 7.x
  2 sites web dont un CMS au choix (wordpress, prestashop, autres ?)
sur "db1":
  mariadb (base de donnée pour le CMS au minimum)
  utilisateur et base de donnée créée via ansible


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
