Prérequis
Installez VirtualBox et Vagrant sur votre système.
Créez des machines virtuelles avec au moins 512 Mo de RAM et 2 CPU.

Installation
Déployez les machines virtuelles à l'aide d'un fichier Vagrant en utilisant la commande vagrant up.
Une fois les machines provisionnées, initialisez la connexion SSH.
Connectez-vous aux machines virtuelles à l'aide des clés SSH situées dans le répertoire /sshkey.
Lancez le playbook principal playbook-galera.yaml en utilisant la commande ansible-playbook -i inventory playbook-galera.yaml. Ce playbook initialise le cluster Galera.
Une fois le cluster initialisé, lancez le deuxième playbook playbook.yaml en utilisant la commande ansible-playbook -i inventory playbook.yaml. Ce playbook installe le load balancing actif-passif.

Partie Wordpress
Les variables pour la configuration de Wordpress sont situées dans le fichier vars/main.yaml. Si vous souhaitez surcharger ces variables, utilisez les variables présentes dans vars/main.yaml comme exemple.

Partie Base de données
Le fichier main.yaml contient plusieurs tâches pour la configuration de la base de données. Il installe les dépendances nécessaires à l'installation du cluster MariaDB, crée un fichier .my.cnf pour la configuration et crée la base de données.

Partie Backup
Un partage a été monté pour stocker les sauvegardes de la base de données. Un cron a été créé pour déposer les dumps dans le répertoire /mnt/backup.

Faute de temps , nous avons pu tester la partie keepalidved pour le bon fonctionnement des virtualip , ils sont implementer dans le role mais ils sont commenté . 

Prérequis : 
Installer un virtualbox et vagrant .
Machines virtuelle de 512 mo et 2 cpu .

Installation: 
Deploiement des machines virtuelles avec un vagrant file , on utilise la commande vagrant up . Une fois les machines provisionné , il faut initialisé la connexion ssh .

Par la suite , il faudra se connecter avec les clé ssh qui sont dans le repertoire /sshkey , ensuite il faut initialise la connexion qui lance le playbook  playbook-galera.yaml : 
ansible-playbook -i inventory  playbook-galera.yaml nous avons séparer les playbook principale car le cluster s'initalise une fois , une fois lancé il faudra lancer le deuxiéme playbook qui est playbook.yaml , il permet d'installer le load-balancing actif passif .

Pour la partie wordpress , les variables sont situé dans le dossier vars/main.yaml . Si on veut surcharger ces variables , il faudra prendre en exemple les variable qui sont dans /vars/main.yaml

Partie Base de donnée : 

Nous avons un main.yaml qui inclut plusieurs task , la premiere est les dépendances pour l'installation du cluster mariadb ensuite il créer un fichier .my.cnf pour la configuration puis pour finir il créer la base de donnée . 

Partie Backup : 

Nous avons choisit de monter un partage ou seront déposer les backups , un cron a été créer pour deposer les dumps sur /mnt/backup. 

Faute de temps , nous avons pu tester la partie keepalidved pour le bon fonctionnement des virtualip , ils sont implementer dans le role mais ils sont commenté .

Ajouter dans la partie host/ : 

192.168.20.100 monblog.projet.local
192.168.20.101 monblog.projet.local
 
192.168.20.12 monblog.projet.local
192.168.20.13 monblog.projet.local