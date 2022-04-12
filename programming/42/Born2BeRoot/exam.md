[[Born2beRoot]]

<u>**Partie obligatoire**</u>
Le projet consiste à créer et configurer une machine virtuelle suivant des règles strictes.

L'étudiant évalué doit vous expliquer simplement :
- Comment fonctionne une machine virtuelle :
une machine virtuelle est une illusion d'un appareil informatique créée par un logiciel d'émulation ou instanciée par un hyperviseur. Le logiciel d'émulation simule la présence de ressources matérielles et logicielles (mémoire, processeur, disque dur, système d'exploitation, pilotes) permettant d'exécuter des programmes dans les mêmes conditions que celles de la machine simulée.
- Son choix de système d'exploitation
- Les différences fondamentales entre CentOS et Debian (tous deux Linux)
[CenOS](https://en.wikipedia.org/wiki/CentOS)
[Debian](https://en.wikipedia.org/wiki/Debian)
![[Pasted image 20220409191552.png]]
- Le but de machines virtuelles :
un des intérêts est de pouvoir s'abstraire des caractéristiques de la machine physique utilisée, forte portabilité, gestion des systèmes hérités, sécurité d'isolation des applications, émulation de plusieurs machines sur une seule.
- Si l'étudiant évalué a choisi CentOS : ce que sont SELinux et DNF
Security-Enhanced Linux est un module de sécurité Linux définissant une politique de contrôle d'accès obligatoire aux éléments d'un système Linux.
Dandified YUM est un gestionnaire de paquet.
- Si l'étudiant évalué a choisi Debian, la différence entre aptitude et apt, et ce qu'est APPArmor :
[APT](https://en.wikipedia.org/wiki/APT_(software)) (Advanced Packaging Tool) est un gestionnaire de paquets utilise par Debian.
[Aptitude](https://en.wikipedia.org/wiki/Aptitude_(software)) est une interface du gestionnaire de paquet [APT](https://en.wikipedia.org/wiki/APT_(software)) qui offre plus de fonctionnalité que **APT**.
**apt** est une commande de la distribution Debian de Linux introduite apres la commande **apt-get** qui permet plus de fonctionnalites que **apt-get**. Par exemple, la commande
```js
apt upgrade your_program
```
installe non seulement les paquets necessaire et leur dependances sans enlever les anciens paquets. De plus **apt** montre la progression de l'action visuellement.
[AppArmor](https://en.wikipedia.org/wiki/AppArmor) est un logiciel de securite pour Linux. Il permet a l'administrateur systeme d'associer a chaque programme un profil de securite qui restreint ses acces au systeme d'exploitation. Il comprend un mode d'apprentissage ou les transgressions au profil sont enregistrees mais pas empechees. Plus simple que SELinux car AppArmor travaille avec les chemins quand SELinux travaille s'appuie sur l'application d'indicateurs aux fichiers.
![[Pasted image 20220409191953.png]]

Pendant la soutenance, un script doit afficher des informations toutes les 10 minutes. Son fonctionnement sera vérifié en détail ultérieurement.

<u>**Simple setup Rappel :**</u>
Chaque fois que vous avez besoin d'aide pour vérifier quelque chose, l'étudiant évalué doit pouvoir vous aider.
- Assurez-vous que la machine ne dispose pas d'un environnement graphique au lancement.
- Un mot de passe vous sera demandé avant de tenter de vous connecter à cette machine.
- Enfin, connectez-vous avec un utilisateur avec l'aide de l'étudiant évalué. Cet utilisateur ne doit pas être root. Faites attention au mot de passe choisi, il doit suivre les règles imposées dans le sujet.
- Vérifiez que le service UFW est démarré avec l'aide de l'évaluateur :
Enable UFW:
```js
sudo ufw enable
```
Check status:
```js
sudo ufw status numbered
```
Configure rules:
```js
sudo ufw allow ssh
```
Configure port rules:
```js
sudo ufw allow 4242
```
Delete the new rule:
```js
sudo ufw status numbered
sudo ufw delete (rule number to be deleted)
```
- Vérifiez que le service SSH est démarré avec l'aide de l'évaluateur :
```js
sudo systemctl status ssh
```
or
```js
sudo service sshd status
```
to restart the SSH service:
```js
service ssh restart
```
SSH (Secure Shell) est un outils qui crypte l'identite, le mot de passe et les donnees permettant l'administration du systeme de securite, le transfer de fichiers et la communication sur un reseau non securise. SSH est un client, une commande qui permet de se connecter a distance a une machine distante.
SSHD est un serveur, un daemon qui tourne en arriere plan et permet des connections a distance.
- Vérifiez que le système d'exploitation choisi est Debian ou CentOS avec l'aide de l'évaluateur :
```js
hostnamectl
```
ou
```js
cat /etc/os-release
```
ou
```js
cat /proc/version
```
ou pour la version Linux kernel
```js
uname -r
```
<u>**User**</u>
- Le sujet demande qu'un utilisateur avec le login de l'étudiant évalué soit présent sur la machine virtuelle. Vérifiez qu'il a bien été ajouté et qu'il appartient aux groupes 'sudo' et 'user42'.
```js
getent group
```
ou
```js
getent group sudo
```
et
```js
getent group user42
```
- Assurez-vous que les règles imposées dans le sujet concernant la politique de mot de passe ont été mises en place en suivant les étapes suivantes :
```js
sudo vim /etc/pam.d/common-password
```
- Tout d'abord, créez un nouvel utilisateur :
```js
sudo adduser your_new_username
```
Pour effacer un utilisateur :
```js
sudo deluser --remove-all-files your_username
```
Pour voit tous les utilisateurs locaux :
```js
cut -d: -f1 /etc/passwd
```
Pour changer d'utilisateur :
```js
su your_username
```
- Attribuez-lui un mot de passe de votre choix, en respectant les règles du sujet. L'élève évalué doit maintenant vous expliquer comment il a pu mettre en place les règles demandées dans le sujet sur sa machine virtuelle. Normalement il doit y avoir un ou deux fichiers modifiés.
```js
sudo vim /etc/pam.d/common-password
```
- Maintenant que vous avez un nouvel utilisateur, demandez à l'étudiant évalué de créer un groupe nommé 'évaluant' devant vous et attribuez-le à cet utilisateur :
```js
sudo groupadd your_new_group
```
```js
sudo usermod -aG your_group your_username
```

- Enfin, vérifiez que cet utilisateur appartient au groupe 'évaluateur' :
```js
groups
```

- Enfin, demandez à l'étudiant évalué d'expliquer les avantages de cette politique de mot de passe, ainsi que les avantages et les inconvénients de sa mise en œuvre :
PAM permet de definir la strategie d'authentification sans devoir recompiler des programmes d'authentification, ne permet pas l'utilisation de Kerberos

<u>**Hostname and partitions :**</u> 
- Vérifiez que le nom d'hôte de la machine est correctement formaté comme suit :
login42 (login de l'étudiant évalué) :
Verifier hostname:
```js
hostnamectl
```
- Modifiez ce nom d'hôte en remplacant le login par le vôtre, puis redémarrez la machine. Si au redémarrage, le nom d'hôte n'a pas été mis à jour, l'évaluation s'arrête ici :
Changer le hostname :
```js
hostnamectl set-hostname new_hostname
```
Changer /etc/hosts file :
```js
sudo nano /etc/hosts
```
Changer old_hostname par new_hostname :
```js
127.0.0.1	localhost
127.0.0.1	new_hostname
```
Reboot et verifier le changement :
```js
sudo reboot
```
- Vous pouvez maintenant restaurer la machine sur le nom d'hôte d'origine :
Changer le hostname :
```js
hostnamectl set-hostname new_hostname
```
- Demandez à l'étudiant évalué comment afficher les partitions pour cette machine virtuelle :
```js
lsblk
```
- Comparez la sortie avec le exemple donné dans le sujet.
- Vérifiez que le programme 'sudo' est correctement installé sur la machine virtuelle :
```js
sudo --version
```
- L'étudiant évalué devrait maintenant afficher l'affectation de votre nouvel utilisateur au ' sudo' group :
```js
groups
```
Le sujet impose des règles strictes pour sudo. L'étudiant évalué doit d'abord expliquer l'intérêt et le fonctionnement de sudo à l'aide d'exemples de son choix.
Dans un deuxième temps, il doit vous montrer la mise en œuvre des règles imposées par le sujet
- Vérifier que le '/var/log/sudo/' existe et contient au moins un fichier
- Vérifiez le contenu des fichiers dans ce dossier, vous devriez voir un historique des commandes utilisées avec sudo :
```js
cat sudo.log
```
- Enfin, essayez d'exécuter une commande via sudo. Vérifiez si le ou les fichiers du dossier '/var/log/sudo/' ont été mis à jour.
```js
sudo adduser testsudo
```

<u>**UFW :**</u> 
- Vérifiez que le programme 'UFW' est correctement installé sur la machine virtuelle :
```js
sudo ufw --version
```
- Vérifiez qu'il fonctionne correctement
- L'étudiant évalué doit expliquer à vous en gros ce qu'est UFW et la valeur de son utilisation.
- Énumérez les règles actives dans UFW. Une règle doit exister pour le port 4242 :
```js
sudo ufw status numbered
```
- Ajoutez une nouvelle règle pour ouvrir le port 8080. Vérifiez que celle-ci a bien été ajoutée en listant les règles actives :
Ajouter 8080 dans environnement Virtual Box
```js
sudo ufw allow 8080
```
- Enfin, supprimez cette nouvelle règle avec l'aide de l'élève en cours d'évaluation :
```js
sudo ufw status numbered
sudo ufw delete (rule number to be deleted)
```

<u>**Script monitoring :**</u> 
- Comment fonctionne son script en vous montrant le code. L'étudiant évalué configure son script pour qu'il s'exécute toutes les 10 minutes à partir du démarrage du serveur :
```js
sudo crontab -u root -e
```
-u pour "user" definit comme "root"
-e pour editer le crontab de l'utilisateur definit
- Une fois le bon fonctionnement du script vérifié, l'étudiant évalué doit s'assurer que ce script s'exécute toutes les minutes.
- Une fois le bon fonctionnement du script vérifié, l'étudiant évalué doit s'assurer que ce script s'exécute toutes les minutes. Vous pouvez exécuter ce que vous voulez. Terminez l'évaluation pour vous assurer que le script s'exécute correctement avec des valeurs dynamiques.
- Enfin, l'étudiant évalué doit arrêter l'exécution du script au démarrage du serveur, mais sans modifier le script lui-même. Pour vérifier ce point, vous devrez redémarrer le serveur une dernière fois. Au démarrage, il faudra vérifier que le script existe toujours au même endroit, que ses droits sont restés inchangés, et qu'il n'a pas été modifié.