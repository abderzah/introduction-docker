
<a id='main'></a>
# Introduction à Docker
<sup><sub>(Basé sur le séminaire : https://ualmtorres.github.io/SeminarioDockerPresentacion/)</sub></sup>

[Docker](https://www.docker.com/) est [un projet open source créé en 2013](https://en.wikipedia.org/wiki/Docker_(software)) et a été une révolution pour le développement et le déploiement des opérations. Docker fait abstraction du matériel et du système d'exploitation de l'hôte en exécutant des applications dans des **conteneurs** : des compartiments isolés qui contiennent toutes les ressources d'une application ou d'un service.

Dans ce cours nous verrons comment utiliser Docker pour le développement d'applications simples ainsi que pour l'[installation de services réseau](https://di.iut.univ-lehavre.fr/pedago/info1/SAE_2_03/index.xml). 

<center>

<iframe width="560" height="315" src="https://www.youtube.com/embed/iPKnqTb95i4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 
</center>


## Objectifs

>1. Connaître les composants de base de Docker
2. Créer des conteneurs à partir d'images Docker Hub
3. Apprenez à utiliser Dockerfile pour la création d'images
4. Utiliser des volumes pour le stockage persistant

[Haut de la page](#main)


---

## Découverte de docker

>1. [TP1 Fonctionnement de base de Docker](./1base/index.md)
2. [TP2 Dockerfile pour la création d’images](./2dockerfile/index.md)

[Haut de la page](#main)


---

## Consignes projet SAE 2.03

-  [Consignes Projet](./projet/index.md)


[Haut de la page](#main)


---


## Installation

- Pour installer docker sur votre machine personnelle suivez les instructions :
    - [Guide d'installation de docker sur plussieurs plate-formes](https://docs.docker.com/get-docker/)
- Pour configurer docker sur votre machine de l'IUT suivez les instructions :
    -  [Guide de Configuration Docker sur les machines de l'IUT](instructions-di-docker.md)


[Haut de la page](#main)


---


## Ressources

- [Docker cheatsheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)
- [Docker hub ](https://hub.docker.com/) : un référentiel avec différentes images docker
- [Page de documentation principale de docker](https://docs.docker.com/). Ce site contient :
    - [Guide d'installation de docker sur plussieurs plate-formes](https://docs.docker.com/get-docker/)
    - [Manuel d'initiation à docker](https://docs.docker.com/get-started/)
- [Cours d'introduction à git et github](https://juanluck.github.io/Introduction-GIT/)


- Cette documentation a été rédigée par notre collègue Juanlu qui travaille maintenant à Grenade en Espagne. 
- Voici le lien originel de la documentation :  [Juanlu](https://github.com/juanluck/Inroduction-Git/).
[Haut de la page](#main)


---


<!--<div id="attention">
	<p>
	Les images Docker occupent une certaine quantité d'espace sur votre disque dur. Normalement, ce n'est pas un problème si vous travaillez sur votre machine personelle. En revanche, si vous faites les exercices sur les machines de l'IUT, nous risquons de dépasser le quota de stockage. Pour éviter cela, n'oubliez pas de supprimer les images avec les commandes suivantes après la fin de chaque exercice.
	</p>

	<h3>1. Arrêter tous les conteneurs en cours d'exécution</h3>
	<p><code>
		docker stop $(docker ps -qa)
	</code></p>

	<h3>2. Supprimer tous les conteneurs</h3>
	<p><code>
		docker rm $(docker ps -qa)
	</code></p>

	<h3>3. Suppression de toutes les images Docker</h3>
	<p><code>
		docker rmi $(docker images -q)
	</code></p>
</div>

[Haut de la page](#main)

---
-->

<style type="text/css" media="screen">
   #tip {
      min-height: 100px;
      background-image: url(images/tip.png);
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
      background-image: url(images/homework.png);
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
      background-image: url(images/attention.png);
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
