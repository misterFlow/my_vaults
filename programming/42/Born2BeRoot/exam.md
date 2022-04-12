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
[Aptitude](https://en.wikipedia.org/wiki/Aptitude_(software)) est une interface du gestionnaire de paquet [APT](https://en.wikipedia.org/wiki/APT_(software)) qui offre plus de fonctionnalité que apt.
apt est le programme de gestion de paquets venant avec le paquet apt de Debian.
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
or
cat /etc/os-release