# TP Docker

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
docker run --name my-mysql -e MYSQL_ROOT_PASSWORD=ynov -d mysql:5.7
```

```
docker run --name my-phpmyadmin --link my-mysql:db -e PMA_HOST=db -e PMA_PORT=3306 -e PMA_USER=root -e PMA_PASSWORD=ynov -p 8081:80 -d phpmyadmin/phpmyadmin
```

![php_my_images_active](img/php_my_images_active.png)

# 7.b.

Connexion à l'interface de phpmyadmin

![phpmyadmin_UI](/img/phpmyadmin_UI.png)

Création de 2 tables, et insertions de données

![table_eleve](/img/table_eleve.png)

![table_note](/img/table_note.png)