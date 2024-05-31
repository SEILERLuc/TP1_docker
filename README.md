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


# 5.e.

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

Lancement de la nouvelle image Nginx créée avec le Dockerfile

```
docker run --name my_nginx_image -p 8080:80 -d my_nginx_image
```