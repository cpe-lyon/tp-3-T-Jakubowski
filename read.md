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
15. 