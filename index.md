<style type="text/css" media="screen">
   #tip {
      min-height: 100px;
      background-image: url(images/tip.png);
      background-repeat: no-repeat;
      background-position: left ;
      margin-bottom: 90px;
      padding-left:100px;
      padding-top:5px;
     color: #000000;
     font-size: 18px !important;
     border-color: #FFFFFF; !important;
     background-color: rgba(84,174,255,0.1); !important;
     border-radius: 4px !important;
     border: 1px solid #000000; !important;
   }
</style>

<a id='main'></a>
# Introduction à Docker
<sup><sub>(Basé sur le séminaire : https://ualmtorres.github.io/SeminarioDockerPresentacion/)</sub></sup>

[Docker](https://www.docker.com/) est [un projet open source créé en 2013](https://en.wikipedia.org/wiki/Docker_(software)) et a été une révolution pour le développement et le déploiement des opérations. Docker fait abstraction du matériel et du système d'exploitation de l'hôte en exécutant des applications dans des **conteneurs** : des compartiments isolés qui contiennent toutes les ressources d'une application ou d'un service.

Dans ce cours nous verrons comment utiliser Docker pour le développement d'applications simples ainsi que 


apprendre à créer des services avec Docker Compose, clusters avec Docker Swarm et interagir à distance avec la machine Docker.

## Objectifs



Le but de ce premier TP est de commencer à se familiariser avec git. Plus précisément, nous allons apprendre: 

>1. Connaître les composants de base de Docker
2. Créer des conteneurs à partir d'images Docker Hub
3. Apprenez à utiliser Dockerfile pour la création d'images
4. Utiliser Docker Compose pour créer des environnements de conteneurs
5. Utiliser des volumes pour le stockage persistant
6. Étudier Docker Swarm pour la mise à l'échelle des applications
7. Créer des clusters avec Docker Machine
8. Étudier des exemples d'environnements élastiques

[Haut de la page](#main)


---