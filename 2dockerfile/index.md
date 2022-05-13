

<a id='main'></a>
# Dockerfile pour la création d'images
[Retour à la page principale](../index.md)

Jusqu'à présent, nous avons appris à utiliser les images disponibles sur hub.docker.com pour lancer des conteneurs dans notre environnement. Cependant, une question se pose : **y a-t-il une image pour chaque type de service que l'on peut imaginer ?** La réponse est claire : **non**. 

À partir d'une image existante, le fichier ```Dockerfile``` nous permet, entre autres, d'installer de nouveaux packages, de configurer la visibilité des ports et de définir le programme en cours d'exécution par défaut. En d'autres termes, ```Dockerfile``` nous permet de générer n'importe quel type d'image avec les caractéristiques que nous voulons.

## 1. Introduction à Dockerfile

Les paramètres et les instructions d'un dockerfile sont nombreux, nous n'allons donc pas tous les voir. Au lieu de cela, nous allons travailler avec des exercices d'un ordre croissant de complexité qui nous permettront de découvrir progressivement comment créer notre propre dockerfile. Si nous avons besoin de connaître de nouvelles fonctionnalités ou la syntaxe d'une instruction spécifique, vous pouvez consulter [ce manuel de référence de dockerfile](https://docs.docker.com/engine/reference/builder/).

### 1.1. Notre premier dockerfile

- Pour construire une image, un fichier ```Dockerfile``` est créé avec les instructions qui précisent ce qui va aller dans l'environnement, à l'intérieur du conteneur (réseaux, volumes, ports vers l'extérieur, fichiers qui sont inclus).

- Indique comment et avec quoi construire l'image.

- Voyons un exemple simple de fichier ```Dockerfile``` :

```shell
# Utiliser l'image httpd officielle comme image parent
FROM httpd

# Copier le répertoire html du répertoire courant vers le répertoire de l'image /usr/.../htdocs
COPY ./html/ /usr/local/apache2/htdocs/

# Exécuter la commande echo sur le conteneur 
# (il peut s'agir de n'importe quelle autre commande)
RUN echo 'Hello world! Voici notre premier dockerfile'


# Rendre le port 80 accessible au monde en dehors de ce conteneur
EXPOSE 80
```
### 1.1.1. Structure des répertoires

Le dockerfile doit être situé dans un répertoire spécifique. Ensuite, nous allons créer cette structure de répertoires :

- Accédez à un répertoire de votre choix.

- Créez un nouveau répertoire qui hébergera le dockerfile. Nous pouvons l'appeler premierDockerfile :
```
mkdir premierDockerfile
```

- Accéder au répertoire :
```
cd premierDockerfile
```

- Dans le référentiel actuel, créez un fichier appelé ```Dockerfile``` et copiez le code du Dockerfile ci-dessus. 

- Si nous voyons le code ```Dockerfile```, il y a une ligne dans laquelle nous indiquons que nous voulons copier le répertoire ```html``` de l'hôte dans le répertoire ```XX``` du conteneur. Nous devons donc maintenant créer ce répertoire ```html```. Tapez :
```
mkdir html
```

- Dans le répertoire ```html```, créez un fichier ```index.html``` avec le contenu html de votre choix.

- Revenons au répertoire ```premier Dockerfile``` pour que la commande ```tree``` affiche cette arborescence :

```
$ tree
.
├── Dockerfile
└── html
    └── index.html
```

<center>
<b style="color:red">Félicitations!! Nous avons terminé la structure de répertoires.</b>
</center>

### 1.1.2. Créer l'image et lancer le conteneur

- Pour construire l'image décrite dans le dockerfile, nous utiliserons la commande suivante :
```shell
docker build -t <choisir-un-nom-pour-l'image> .
```
- Voici la signification des différents paramètres :
    - ```docker build``` : commande qui nous permet d'indiquer que nous allons construire une nouvelle image.
    - ```-t <choisir-un-nom-pour-l'image>``` : indique le nom de l'image que nous allons construire. Essayez d'être bref mais descriptif. Un exemple : ```<votre nom>-httpd-1ere-img```
    - ```.``` : le dernier point indique le répertoire où se trouve le fichier dockerfile.

- Ensuite, lancer le serveur web :
```shell
docker run --name <nom du conteneur de votre choix> -d -p <port hôte>:80 <nom-de-l'image-choisie>
```

- Vérifier que l'application est en cours d'exécution. Pour ce faire, ouvrez un navigateur et tapez ```localhost:<port hôte>```

- Vérifier que le conteneur associé est actif :
```shell
docker ps
```

- La sortie de ```docker ps``` doit être similaire à :
```shell
CONTAINER ID   IMAGE          COMMAND              CREATED          STATUS          PORTS                                   NAMES
b8f8f406b03c   httpd-juanlu   "httpd-foreground"   30 minutes ago   Up 30 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   quirky_tesla
```

- Finalement, arrêtez le conteneur avec la commande suivante (les dernières chiffres sont le code de hachage affiché par docker ps):
```shell
docker stop b8f8f406b03c
```

- Encore, si on souhaite supprimer le conteneur, on peut taper :
```shell
docker rm b8f8f406b03c
```

**NOTE :** Au lieu du code de hachage, on peut toujours taper le nom du conteneur. Dans le cas d'exemple ce nom est ```quirky_tesla```

<center>
<b style="color:red">Félicitations!! Nous avons lancé notre premier conteneur avec notre image personnelle.</b>
</center>

[Haut de la page](#main)

---

### 1.2. Installer un service apache à partir d'une image vierge debian

L'exemple dockerfile ci-dessus est très simple, puisque l'image httpd est préconfigurée pour lancer un service apache. Cependant, pourrait-on configurer une image avec le service apache à partir d'une image debian sur laquelle apache n'est pas installé ? La réponse est oui et nous apprendrons comment dans cette section.

```
# Utiliser l'image debia officielle comme image parent
FROM debian:latest

# Installer des services et des packages
RUN  apt-get update && \
    apt-get -y install  \
    apache2

# Copier les fichiers de l'hôte vers l'image
COPY ./html /var/www/html

# Exposer le port 80
EXPOSE 80

# Lancer le service apache au démarrage du conteneur
CMD ["/usr/sbin/apache2ctl","-DFOREGROUND"]
```

[Haut de la page](#main)

---

## 2. Dockerfile + github

Faciliter le deployement des applications.

[Exemple de serveur apache prêt à être déployé](https://github.com/juanluck/exempleDockerfile)


[Exemple de serveur apache + mariadb + php (lamp)](https://github.com/juanluck/lampDocker)
[Haut de la page](#main)

---

## 3. (Avancé et facultatif)  Docker compose

Le service docker compose n'est pas installé sur les machines de l'IUT.

[Exemple de docker compose à plusieurs conteneurs](https://github.com/juanluck/docker_customer_catalog)


[Haut de la page](#main)

---



<style type="text/css" media="screen">
   #tip {
      min-height: 100px;
      background-image: url(../images/tip.png);
      background-repeat: no-repeat;
      background-position: left ;
      margin-bottom: 10px;
      padding-left:100px;
      padding-top:5px;
     color: #000000;
     font-size: 18px !important;
     border-color: #FFFFFF; !important;
     background-color: rgba(84,174,255,0.1); !important;
     border-radius: 4px !important;
     border: 1px solid #000000; !important;
   }
   
      #homework {
      min-height: 100px;
      background-image: url(../images/homework.png);
      background-repeat: no-repeat;
      background-position: left ;
      margin-bottom: 10px;
      padding-left:100px;
      padding-top:5px;
     color: #000000;
     font-size: 18px !important;
     border-color: #FFFFFF; !important;
     background-color: rgba(0,255,0,0.1); !important;
     border-radius: 4px !important;
     border: 1px solid #000000; !important;
   }
   
    #attention {
      min-height: 100px;
      background-image: url(../images/attention.png);
      background-repeat: no-repeat;
      background-position: left ;
      margin-bottom: 10px;
      padding-left:100px;
      padding-top:5px;
     color: #000000;
     font-size: 18px !important;
     border-color: #FFFFFF; !important;
     background-color: rgba(255,0,0,0.1); !important;
     border-radius: 4px !important;
     border: 1px solid #000000; !important;
   }

</style>
