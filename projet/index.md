<a id='main'></a>
# Projet SAE 2.03
[Retour à la page principale](../index.md)


## 1. Objectif

- Ce projet consiste à proposer l'installation d'un service réseau à l'aide de docker. Avant de commencer le projet, l'étudiant doit suivre le cours d'[introduction à docker](https://juanluck.github.io/introduction-docker/) qui, associé aux ressources Web proposées dans la SAE, expliquera les concepts nécessaires à la réalisation du projet.

- Le projet à réaliser est au choix de chaque équipe, mais il doit être lié à l'installation des services réseaux. Dans le cours, un projet est proposé à titre d'exemple ([sur ce lien](https://github.com/juanluck/exempleDockerfile/)).

- En guise d'aide, nous proposons ci-dessous une série de sujets (avec un niveau de complexité différent) qui peuvent être abordés dans le projet.  Cela ne vous empêche pas de choisir un sujet différent :
    - [Service LDAP](https://fr.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)
    - [Partage de fichiers](https://fr.wikipedia.org/wiki/Serveur_de_fichiers)
    - [Serveur gitlab](https://fr.wikipedia.org/wiki/GitLab)
    - [Vidéo à la demande](https://fr.wikipedia.org/wiki/Vid%C3%A9o_%C3%A0_la_demande)

- La complexité et la créativité du projet seront valorisées positivement mais, dans tous les cas, n'allez pas au-delà de vos possibilités.

## 2. Contraintes

- Le projet sera basé sur dockerfile et sera hébergé dans un dépôt github ```docker-sae203``` pour chaque équipe.

- Tout le monde devrait partir de la base officielle de ```debian```, c'est-à-dire que la première ligne du Dockerfile devrait être ```FROM debian:latest```.

- Le projet doit fournir un seul service et non plusieurs. Cela signifie plusieurs choses :
    - Nous allons utiliser un seul dockerfile et non des outils plus avancés comme docker compose ou docker swarm.
    - Cela signifie que le conteneur ne doit fournir qu'un seul service, par exemple un serveur à la demande, et non plusieurs.
    - En ce sens, le projet devrait ressembler un peu à l'exemple d'un [serveur Apache vu en cours](https://github.com/juanluck/exempleDockerfile/) mais avec un peu plus de complexité.
 

## 3. Instructions pour le rapport de projet

- Comme nous l'avons déjà vu dans [le cours d'introduction à git (tp5)](https://juanluck.github.io/Introduction-GIT/tp5/#sae), chaque équipe va créer un dépôt ```docker-sae203``` sur github.

- Ce référentiel ```docker-sae203``` nous servira à la fois pour stocker notre projet ainsi que le site web :
    - Dans la branche principale, nous aurons le projet docker qui devrait au moins contenir deux fichiers (peut être plus) :
        - Dockerfile
        - README.md : Avec les instructions d'installation. Voir [ce site comme exemple](https://github.com/juanluck/exempleDockerfile/)
    - Dans la branche ```gh-pages```, nous allons héberger le site web du projet. Vous pouvez voir [le tp5 de l'introduction à git](https://juanluck.github.io/Introduction-GIT/tp5/) comme guide.

- Le site web sera à la fois le compte-rendu du projet ainsi que le support de la présentation de votre soutenance.

## 4. Dépôt du projet

- Pour déposer votre projet, allez sur [ce dépôt github](https://github.com/juanluck/depot-de-projets-SAE203-2022/) et suivez les instructions.

## 5. Date limite pour le dépôt du projet

- **Date à déterminer (25 mai 2022 minuit)**

## 6. Soutenances

- Dans la soutenance, chaque équipe disposera d'un temps compris entre 10 et 15 minutes (à décider ultérieurement).

- En utilisant le site web du projet comme support, le format de la présentation consistera en une brève explication du projet et une démonstration pratique.


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
