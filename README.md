# tp-volumes
tp sur les volumes docker

## Tp1
* Démarrez un bash interactif de l'image debian, en montant la racine de la machine hôte sur /host
* Démarrez un bash interactif avec un volume docker sur /data, créer un fichier avec la commande touch /data/toto
* Affichez la liste des volumes
* Détruisez et relancez le même conteneur, observez le contenu de /data
* Démarrez un second conteneur identique et afficher le contenu de /data.
* Testez l'option -v de la commande docker rm
## Tp2
* Créez un Dockerfile utilisant l'image de base debian:stretch déclarant un volume
* Construisez l'image à l'aide de la commande docker build et nommez la docker-vol
* Inspectez l'image construite à l'aide de la commande docker inspect que voyez vous ?
* Lancez un conteneur à partir de notre image docker-vol et Vérifiez la présence du dossier /mountPoint
* Ajoutez un nouveau fichier dans /mountPoint
* Dans un autre shell, inspectez le conteneur et trouvez l'emplacement du volume de données
## Tp3
* Lancer un conteneur à partir de l'image postgres:10 et utiliser les volumes docker pour héberger le contenu du dossier /var/lib/postgresql/data
* Entrez dans le conteneur que vous venez de créer et ajoutez une table nommée test contenant une colonne varchar data de taille 255 et ajoutez-y une entrée de votre choix
* Détruisez votre conteneur de base de donnée
* Lancez un nouveau conteneur Docker PosgreSQL réutilisant le précédent volume de données. Vérifiez la présence des données que vous avez créées précédemment.


