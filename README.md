# TP Docker

## Luc Seiler

<!-- ![docker_logo](img/docker_logo.png) -->
<!-- ![nginx_logo](img/nginx_logo.png) -->

# 4

Création du repository sur l'interface GitHub.

![repo](img/github_repo.png)

(mettre les commandes git: init, add, commit, push)

# 5.a.

```
docker pull nginx
```

![docker_pull](img/nginx_pull.png)

L'image de Nginx est récupérée depuis le hub de Docker.

# 5.b.

```
docker images
```

```
docker ps -a
```

![docker_images](img/nginx_local.png)

L'image de Nginx est bien installée en local sur la machine.

# 5.c.

```
sudo nano index.html
```

Création du fichier index.html

![index_html](img/index_html.png)

# 5.d.

Copie du fichier dans le repertoire html/ de Nginx

```
sudo cp index.html ~/nginx/html/index.html
```

Démarrage de l'image sur le port 8080, via un volume

```
docker run --name nginx -v ~/nginx/html:/usr/share/nginx/html:ro -p 8080:80 -d nginx
```

![index_html](img/nginx_index_ok.png)


# 6.a.

Arrêt de l'image de Nginx

```
docker stop nginx
```

Création du Dockerfile (fichier 'Dockerfile')

![dockerfile](img/dockerfile.png)

Création d'une nouvelle image custom

```
docker build -t my_nginx_image
```

-t permet de dire que l'on définit un tag pour le conteneur

![nginx_custom](img/nginx_custom.png)

# 6.b.

Lancement de la nouvelle image Nginx créée avec le Dockerfile

```
docker run --name my_nginx_image -p 8080:80 -d my_nginx_image
```

# 7.a.

```
docker pull phpmyadmin/phpmyadmin
docker pull mysql:5.7
```

![php_my_images](img/php_my_images.png)

Activer les deux conteneurs

```
docker run --name my-mysql -e MYSQL_DATABASE=ynov -e MYSQL_USER=user -e MYSQL_PASSWORD=ynov -e MYSQL_ROOT_PASSWORD=ynov -d mysql:5.7
```

```
docker run --name my-phpmyadmin --link my-mysql:db -e PMA_HOST=my-mysql -e PMA_PORT=3306 -e PMA_USER=user -e PMA_PASSWORD=ynov -p 8081:80 -d phpmyadmin/phpmyadmin
```

![php_my_images_active](img/php_my_images_active.png)

![php_mysql](img/pma_mysql.png)

# 7.b.

Connexion à l'interface de phpmyadmin

![phpmyadmin_UI](img/phpmyadmin_UI.png)

Création de 2 tables, et insertions de données

![table_eleve](img/table_eleve.png)

![table_note](img/table_note.png)

# 8

Création du fichier `docker-compose.yml` (`docker-compose_pma_mysql.yml`)

<!-- ![docker_compose_file](img/docker-compose-file.png) -->

Démarrage des conteneurs via le fichier et docker-compose

```
docker compose up -d
```

-d permet de lancer le conteneur en arrière plan, évitant de prendre le terminal 

![docker_compose](img/docker-compose.png)

Je peux toujours accéder à phpmyadmin, port 8081

# 8.a

Le fichier `docker-compose.yml` permet un meilleur confort de configuration. Il permet de configurer tous les conteneurs en un seul fichier

Il est également pratique si l'on veut donner une certaine configuration à quelqu'un. Il n'aura qu'à récupérer le fichier et taper une seule commande. Cela simplifie donc le déploiement, et évite de faire des erreurs dans les différentes commandes qu'il peut y avoir pour récupérer un conteneur, d'une certaine version, configurer la base de données, l'utilisateur...

Il permet de rendre une configuration plus facile à gérer. Il n'y aura qu'à modifier ce fichier et le renvoyer/réexecuter

# 8.b

On peut rajouter des configurations en plus dans le fichier docker-compose.yml

![phpmyadmin_docker_compse](img/phpmyadmin_docker-compose.png)

# 9

# 9.a

![docker_compose_2](img/docker-compose-file_9.png)

![docker_compose_2](img/docker-compose_9.png)