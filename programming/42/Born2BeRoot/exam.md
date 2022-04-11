[[Born2beRoot]]

<u>**Partie obligatoire**</u>
Le projet consiste à créer et configurer une machine virtuelle suivant des règles strictes.

L'étudiant évalué doit vous expliquer simplement :
- Comment fonctionne une machine virtuelle :
une machine virtuelle est une illusion d'un appareil informatique créée par un logiciel d'émulation ou instanciée par un hyperviseur. Le logiciel d'émulation simule la présence de ressources matérielles et logicielles (mémoire, processeur, disque dur, système d'exploitation, pilotes) permettant d'exécuter des programmes dans les mêmes conditions que celles de la machine simulée. 
- Son choix de système d'exploitation
- Les différences fondamentales entre CentOS et Debian
![[Pasted image 20220409191552.png]]
- Le but de machines virtuelles :
un des intérêts est de pouvoir s'abstraire des caractéristiques de la machine physique utilisée, forte portabilité, gestion des systèmes hérités, sécurité d'isolation des applications, émulation de plusieurs machines sur une seule.
- Si l'étudiant évalué a choisi CentOS : ce que sont SELinux et DNF
Security-Enhanced Linux est un module de sécurité Linux définissant une politique de contrôle d'accès obligatoire aux éléments d'un système Linux.
Dandified YUM est un gestionnaire de paquet.
- Si l'étudiant évalué a choisi Debian, la différence entre aptitude et apt, et ce qu'est APPArmor :
Aptitude est une interface du gestionnaire de paquet APT qui offre plus de fonctionnalité que apt.
apt est le programme de gestion de paquets venant avec le paquet apt de Debian.
AppArmor 
![[Pasted image 20220409191953.png]]

Pendant la soutenance, un script doit afficher des informations toutes les 10 minutes. Son fonctionnement sera vérifié en détail ultérieurement. Si les explications ne sont pas claires, l'évaluation s'arrête ici.