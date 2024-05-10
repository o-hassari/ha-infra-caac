# ha-infra-caac

Prérequis : 
Installer un virtualbox et vagrant .
Machines virtuelle de 512 mo et 2 cpu .

Installation: 
Deploiement des machines virtuelles avec un vagrant file , on utilise la commande vagrant up . Une fois les machines provisionné , il faut initialisé la connexion ssh .

Par la suite , il faudra se connecter avec les clé ssh qui sont dans le repertoire /sshkey , ensuite il faut initialise la connexion qui lance le playbook  playbook-galera.yaml : 
ansible-playbook -i inventory  playbook-galera.yaml nous avons séparer les playbook principale car le cluster s'initalise une fois , une fois lancé il faudra lancer le deuxiéme playbook qui est playbook.yaml , il permet d'installer le load-balancing actif passif .

Partie Wordpress : 

Pour la partie wordpress , les variables sont situé dans le dossier vars/main.yaml . Si on veut surcharger ces variables , il faudra prendre en exemple les variable qui sont dans /vars/main.yaml

Partie Base de donnée : 

Nous avons un main.yaml qui inclut plusieurs task , la premiere est les dépendances pour l'installation du cluster mariadb ensuite il créer un fichier .my.cnf pour la configuration puis pour finir il créer la base de donnée . 

Partie Backup : 

Nous avons choisit de monter un partage ou seront déposer les backups , un cron a été créer pour deposer les dumps sur /mnt/backup.

