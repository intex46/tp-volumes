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
* Créez un Dockerfile utilisant l'image de base debian:stretch déclarant un volume /mountPoint
* Construisez l'image à l'aide de la commande docker build et nommez la docker-vol
```
1 docker build -t docker-vol .
```
* Inspectez l'image construite à l'aide de la commande docker inspect que voyez vous ?
```
1 docker inspect docker-vol
```
* Lancez un conteneur à partir de notre image docker-vol et Vérifiez la présence du dossier /mountPoint
```
1 docker run --rm -it docker-vol
/# ls -ld /mountPoint
```
* Ajoutez un nouveau fichier dans /mountPoint
```
/# echo "Hello API Run" > /mountPoint/hello
```
* Dans un autre shell, inspectez le conteneur et trouvez l'emplacement du volume de données
```
docker inspect -f '{{json .Mounts}}' <mon-conteneur>
ls -l /var/lib/docker/volumes/720e2a2478e70a7cb49ab7385b8be627d4b6ec52e6bb33063e4144355d59592a/_data
```
## Tp3
* Lancer un conteneur à partir de l'image postgres:10 et utiliser les volumes docker pour héberger le contenu du dossier /var/lib/postgresql/data
```
docker run --name postgresql -d -e POSTGRES_PASSWORD=test -v "${PWD}"/data/postgresql:/var/lib/postgresql/data postgres:10 #only for linux / mac 
```
* Entrez dans le conteneur que vous venez de créer et ajoutez une table nommée test contenant une colonne varchar data de taille 255 et ajoutez-y une entrée de votre choix
```
docker exec -it postgresql psql -U postgres
postgres=# create table test(data varchar(255));
postgres=# insert into test(data) values('volume cool');
postgres=# select * from test;
```
* Détruisez votre conteneur de base de donnée
```
1 docker stop postgresql
2 docker rm postgresl
```
* Lancez un nouveau conteneur Docker PosgreSQL réutilisant le précédent volume de données. Vérifiez la présence des données que vous avez créées précédemment.
```
docker run --name postgresql2 -d -v /data/postgresql:/var/lib/postgresql/data postgres:10
docker exec -it postgresql2 psql -U postgres
postgres=# select * from test;
```


