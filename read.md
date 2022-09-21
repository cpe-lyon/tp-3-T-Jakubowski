## Exercice 1
---

1. Pour créer un group dev et infra on utilise ```sudo groupadd dev; sudo groupadd infra```
2. Pour créer un user on va utiliser ```sudo useradd -m dave```, le -m permet de créer le repertoire personel avec et on réutilise cette commande pour les 4 utilisateurs.
3. On pour mettre un utilisateur dans un groupe, on utilise ```usermod -a -G dev alice```, dev est le nom du groupe et alice le nom du user.
4. Pour voir tous les membre du groupe infra on va utiliser la commande ```getent group infra```, ou ```awk -F':' '/infra/{print $4}' /etc/group```
5. Pour changer le groupe propriétaire d'un répertoir on fait ```chgro infra /home/dave``` infra est le nom du groupe et /home/dave et le repertoire
6. Pour changer le groupe primaire d'un user on fait ```usermod dave -g infra```ou dave correspond au user et infra au groupe.
7. On crée le dossier dans home avec ```mkdir``` puis on modifie les permissions avec ```chmod 770 infra``` infra étant le nom du répertoire.
8. Il faut enlever le 'write' pour le groupe et other et le laisser au propriétaire donc en utilisant ```chmod 750 infra```
9. On peut pas ouvrir une session en tant qu'alice car tant que l'utilisateur n'a pas de mot de passe il est considéré comme inactif
10. Pour changer le mot de passe d'un utilisateur on utilise ```passwd alice``` ou alice est le nom du user. Ensuite en faisant ```su alice``` on se connecte bien a alice.
11. Pour obtenir le gid et le uid on utilise ```id alice```
12. Pour trouver un user avec l'uid on utilise ```id -nu 1003```
13. Pour trouver l'id d'un groupe on fait ```getent group dev``` ou dev est le nom du groupe.
14. Pour voir quel groupe a pour id 1002 on fait ```getent group 1002```
15. On retire charlie du grp infra grace a ```gpasswd -d charlie infra```. Il va avoir les permissions other et perdre celles du groupe.
16. Pour mettre l'expiration du compte de dave le 1 juin 2023 on fait ```chage -E 2023/06/01 dave```
    On mets un minimum de 5 jours avant changement du mot de passe ```chage -m 5 dave```
    On mets un maximum de 90 jours avant changement du mot de passe ```chage -M 90 dave```
    On mets une alerte 14 avant que le mot passe doivent être changer ```chage -W 14 dave```
    On met le compte inactif apres 30 jours apres que son mot de passe soit bloquer ```chage -I 30 dave```
17. L'interpreteur de commande du root est bash
18. Le compte nobody est celui qui a le moins de persmission sur les fichiers et dossiers
19. Sudo garde le mot de passe pendant 15 minutes si on veut le forcer à oublier il faut faire ```sudo -k```
    
## Exercice 2
---

1. On a les droit -rw-rw-r-- sur le fichier qu'on crée dans notre répertoire personnel
2. Le root a tous les droit même sur un fichier ou personne n'a de droit dessus
3. Avec les permission -wx on pourra écrire dans le fichier mais en utilisant nano pour aller dedans on ne voit rien, nous n'avons pas les permissions.
4. On ne peux pas executer le fichier en tant que user sans la permission read alors qu'avec sudo on peut. Car le fichier affiche du texte et qu'on a pas le droit de le lire
5. On perds les permissions sur les fichier présents dans le dossiers ou nous n'avons pas les permissions.
6. En enlevant la permission write sur le fichier on ne peux plus écrire dedans, en la remettant on peux réécrire dedans puis le supprimer
7. En enlevant la permission d'éxecution sur le dossier test on ne peux plus entrer dedans, plus créer de dedans, plus supprimer dedans, etc...
8. Il se passe la même chose qu'a la question précédente en se plaçant dedans
9. On execute la commande ```chmod 755 fichier``` pour n'est pas le droit en ecriture mais qu'il puisses le lire
10. Il faut faire un ```umask 077 ./``` pour ne laisser aucune permissions dans notre repertoire personnel, il ne pourra plus lire, écrire et se déplacer dans notre repertoire personnel.
11. Il faut faire un ```umask 000 ./``` pour laisser toutes les permissions dans notre repertoire personnel, il pourra lire, écrire et se déplacer dans notre repertoire personnel.
12. Il faut faire un ```umask 033 ./``` pour laisser ne laissant uniquement la capacité de lire aux autre personnes et nous laisser toutes les permissions.
13. Transcrivez les commandes suivantes de la notation classique à la notation octale ou vice-versa (vous
pourrez vous aider de la commande stat pour valider vos réponses) :
- chmod u=rx,g=wx,o=r fic  => ```chmod 534 fic```
- chmod uo+w,g-rx fic en sachant que les droits initiaux de fic sont r--r-x---   =>  ```chmod 600 fic```
- chmod 653 fic en sachant que les droits initiaux de fic sont 711  =>  ```chmod u-x,g+r,o+w fic```
- chmod u+x,g=w,o-r fic en sachant que les droits initiaux de fic sont r--r-x---   =>  ```chmod 520 fic```

14. Les permission sont -rw-r--r-- sur le fichier /etc/passwd, donc on ne peux que lire a part le root qui a tous les droit. Et l'utilisateur qui a crée le fichier peux lire et écrire dedans.
