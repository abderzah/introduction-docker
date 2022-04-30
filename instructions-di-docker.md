<a id='main'></a>
# Configuration Docker sur les machines de l'IUT

[Retour à la page principale](../index.md)

## À prendre en compte
<div id="tip">
<p>
Les machines à l'IUT n'ont pas de version de docker installée. Docker à l'IUT est situé sur un serveur appelé <b>di-docker</b>. Ce mini-tuto vous explique comment configurer votre machine à l'IUT pour qu'elle ait accès au serveur di-docker et que vous puissiez l'utiliser en toute transparence depuis votre poste de travail local.
</p>

<p>
L'utilisation d'un serveur partagé par tous ne posera pas de problème dans la plupart des exercices. Cependant, nous devons être attentifs aux points suivants :

<ul>
	<li> <b style="font-size:22px">Serveur par défaut :</b></li>
	<ul>
		<li>Si vous travaillez sur une machine personnelle, votre serveur par défaut sera <b>localhost</b>. Cependant, sur une machine de l'IUT, le nom du serveur sera <b>di-docker</b> (par exemple, lorsque vous le saisissez dans un navigateur).</li>
	</ul>

	<li> <b style="font-size:22px">Utilisation des ports :</b></li>
	<ul>
		<li>Comme tous les utilisateurs vont partager le même serveur, le plus gros problème qui peut survenir est que deux utilisateurs essaient d'utiliser le même port pour une application.</li>
		<li>Pour éviter ce conflit, nous allons l'éviter en attribuant un numéro de port unique à chaque utilisateur en suivant la méthode suivante :</li>
		<ul>
			<li>Obtenez le code de hachage de votre nom. Par exemple, disons que je m'appelle John Smith :
			<code>
				$ echo "John Smith" | shasum <br/>
				8d0ed1ffa6ba0f6e6cbb74534b4785a916d73ec0
			</code>
			</li>
			<li> Enregistrez les quatre derniers chiffres, c'est-à-dire <code>3ec0</code></li>
			<li> Traduisez ce code à quatre chiffres de l'hexadécimal au décimal. Par exemple, vous pouvez utiliser ce convertisseur hexadécimal <a href="https://www.rapidtables.com/convert/number/hex-to-decimal.html">convertisseur hexadécimal</a></li>
			<li><b>3ec0</b> en hexadécimal est égal à <b>16064</b>.</li>
			<li>Le numéro de port pour l'utilisateur <em>John Smith</em> sera désormais <b>16064</b>.</li>
			<li>Si <em>John Smith</em> a besoin de plus de ports, nous utiliserons des valeurs corrélatives : <b>16065</b>, <b>16066</b>,<b>...</b></li>
		</ul>
	</ul>

</ul>

</p>
</div>

<div id="homework">
<b >Calculez votre numéro de port et enregistrez-le pour l'utiliser pendant le cours.</b>
</div>

[Haut de la page](#main)


---

## Instructions

- 1) Vérifier sur votre machine à l'IUT si vous avez une clé publique :
```
$ cat .ssh/id_rsa.pub
```

- **Si la clé existe :** copier la clé.
- **Si elle n'existe pas :**
    - Générez la clé avec : 
    ```shell
    $ ssh-keygen
    ```
    - Repondre à tout avec un retour chariot -> passphrase vide.
    - Afficher et **copier** la clé : ```$ cat .ssh/id_rsa.pub```


- 2) On va sur le serveur di-docker :
```shell
ssh <votre-utilisateur-iut>@di-docker
```

- 3) Sur di-docker, éditer le fichier :
```shell
$ nano vi .ssh/authorized_keys
```

- 4) Coller la clé publique sur ce fichier. **Attention**, il ne doit pas y avoir de ligne vide dans le fichier authorized_key.


- 5) Dans un nouveau terminal de la machine, vérifier que la connection ssh est ok. Avec cette commande, on va  donc lister son HOME sur di-docker :
```shell
$ ssh <votre-utilisateur-iut>@di-docker ls -la
```

- 6) Normalement, vous avez déjà accès au serveur di-docker. À partir de la machine iut, tapez :
```shell
$ docker --version
```



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
</div>-->

[Haut de la page](#main)


---

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
     text-align: center;
     vertical-align: baseline;
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