
# Solution exercice section 3.2.2
<a href="/introduction-docker/1base/index.html#section322">Retour à la section</a>

- **Surprise !! :** cette page ne contient aucune solution proposé par le professeur. Au lieu de cela, c'est votre chance d'obtenir **1 point bonus pour le travail d'équipe**.

- La première équipe à faire un [```pull-request```](https://juanluck.github.io/Introduction-GIT/tp4/#pullrequest) sur ce fichier ```solutionSection322.md``` avec la bonne réponse pour résoudre l'exercice recevra ce point bonus.

- **Attention !! :** les modifications proposées du ```pull-request``` se feront uniquement sur ce fichier ```solutionSection322.md``` et sur la branche ```gh-pages```. [Voici le dépôt github](https://github.com/juanluck/introduction-docker).

- **Piste :**
Sans arrêter le conteneur : pour explorer l'arborescence du conteneur, nous pouvons utiliser la commande suivante :
```
docker exec -it <nom-du-conteneur> /bin/bash
```

## Solution fournie par votre équipe

1. Sauvegardez votre fichier `index.html` quelque part sur votre **machine personelle**.
2. Démarrez un invite de commande et déplacez vous dans le dossier du fichier.
3. Lancez un conteneur (s'il est absent) : `docker run --name httpd-soluce -d -p 8080:80 httpd`
4. Entrez `localhost:8080` dans votre navigateur pour visualiser le conteneur.
5. Récupérez l'identifiant du conteneur à l'aide de `docker ps`.
6. Executez la commande `docker cp index.html ID_CONTENEUR:/usr/local/apache2/htdocs/index.html`[^1] en remplaçant `ID_CONTENEUR` par l'identifiant récupéré.
7. Rafraichissez l'onglet qui a `localhost:8080` d'ouvert

[^1]: Le dossier `usr/local/apache2/htdocs` correspond au dossier racine du site web du conteneur.

## Membres de l'équipe

**Equipe 15 :**

- D2 - LANRIN Hugo
- D1 - HAGUES Louis 
- D2 - ROVIRA Adrien
- D1 - CARPENTIER Thibault

