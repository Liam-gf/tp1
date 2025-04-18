**Nom :** Girard--Fourneaux Liam

**Groupe :** Equipe 01

**Année :** 2025

**IUT Le Havre - Cours GIT**

# Compte-rendu TP1 Introduction GIT



## 1. Configuration de GIT


### 1.1 Votre identité

Afin de définir un nom d'utilisateur et une adresse e-mail sur git il faut utiliser les commandes 
suivantes dans le terminal :

**Nom d'utilisateur :** *git config --global user.name "`Votre nom`"*  
**Adresse e-mail :** *git config --global user.email `mail@exemple.com`*  


### 1.2 Votre éditeur

Afin de définir un éditeur de texte il faut utiliser la commande :

**Editeur de texte :** *git config --global core.editor `Votre éditeur de texte`*  


### 1.3 Vérification des informations

Afin de vérifier si les informations renseignés sont corrects, on utilise :

*git config --list*  

Pour vérifier si le nom et l'e-mail rentrer est correct, il faut utiliser les commandes :

**Nom d'utilisateur :** *git config user.name*  
**Adresse e-mail :** *git config user.email*  



## 2. Création d'un dépôt git


Pour crée un dépôt git il faut faire la commande :  

*git init*  

Elle doit renvoyer :  

	Initialized empty Git repository in `Le chemin vers votre répertoire de travail`/.git/


### 2.1 La commande *git status*

La commande *git status* doit afficher : 

	On branch master
	
	Initial commit
	
	nothing to commit (create/copy files and use "git add" to track)



## 3. Création d'un fichier texte README.md


Un fichier README.md est un fichier au format markdown.


### 3.1 Gérer les différentes modifications du fichier README.md

Lorsque l'on fait la commande *git status* et que ceci s'affiche :

	On branch master
	
	Initial commit
	
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)
	
		README.md
	
	nothing added to commit but untracked files present (use "git add" to track)

S'il y a le message *Untracked files:* c'est qu'un fichier a été modifier ou crée mais il n'est pas 
encore dans le dépôt git.

Pour sélection un fichier le fichier on fait :

*git add `Le nom de votre fichier`*.

Si on refait la commande *git status* cela nous affiche :

	On branch master
	
	Initial commit
	
	Changes to be committed:
	  (use "git rm --cached <file>..." to unstage)
	
		new file:   README.md

Nous voyons que le fichier README.md est sélectionner, pour valider l'inclusion on fait :

*git commit -m "`Un message décrivant le commite`"*

Ce qui affiche :

	[master (root-commit) 23782d5] `Message décrivant le commite`
	 1 file changed, 0 insertions(+), 0 deletions(-)
	 create mode 100644 README.md

Si on refait un *git status* on obtient :

	On branch master
	nothing to commit, working directory clean

Pour voir l'historique des différentes versions il faut faire la commande *git log*.


### 3.2 Différencier 3 états / 3 zones / 3 actions

Dans un dépôt git il y a 3 états :

- Modifié (modified) : Il y a eu des modifications sur le fichier.
- Sélectionné (staged) : Le fichier est sélectionné.
- Validé (commited) : Le fichier est synchroniser avec le dépôt.

Ces états correspondent à 3 zones dans GIT :

- La copie de travail (directory).
- La zone de sélection (staging area).
- Le dépôt où les modifications sont enregistrées sous forme de validations (commits).


Le passage entre ses 3 états se fait par 3 actions :

- Sélection (stage) : Sélectionne le fichier *git add*.
- Validation (commit) : Crée le commit et l'envoie vers le dépôt avec *git commit*.
- Récupération (checkout) : Récupère un instantané (snapchot) du le dépôt vers la copie de travail.



## 4. Gestion de version d'un programme Java


Pour crée un fichier java vide on utilise la commande :

**Sur Linux :** *touch `Nom du programme`.java*

**Sur Windows :** *New-Item -Path `Nom du programme`.java -ItemType File*

On édite le fichier avec du code.

Ensuite on fait un *git add src\Cryptomonnaie.java* afin de sélectionner le fichier.
Après on fait la commande *git commit -m "Première version du fichier Cyptomonnaie.java"*.

La commande *git log* affiche ensuite :

	commit b3220b1690a4aa24187b038261dc445d5ce0e32a (HEAD -> master)
	Author: Liam GF <tiger76760@gmail.com>
	Date:   Thu Apr 17 16:31:40 2025 +0200

		Première version du fichier Cyptomonnaie.java

	commit 2ed6106dd9c398dc05958f20bb22819c88d0faad
	Author: Liam GF <tiger76760@gmail.com>
	Date:   Thu Apr 17 16:02:16 2025 +0200

		Ajout du compte rendu des 3 premières étapes du cour

	commit fe7d253bbe6242f8709268d386ba05dbccdeb64d
	Author: Liam GF <tiger76760@gmail.com>
	Date:   Wed Apr 16 21:23:03 2025 +0200

		Ajoute du fichier README.md


### 4.1 Creation du fichier .gitignore

Lorsqu'on compile un fichier .java cela crée un .class. Il est afficher quand on fait *git status* :

	On branch master
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)
		    Cryptomonnaie.class
	
	nothing added to commit but untracked files present (use "git add" to track)

Les fichiers .class ne sont pas à enregistrées dans le dépôt git. L'apparition de fichiers .class 
lorsqu'on fait la commande *git status* est ennuyeuse. Il va donc falloir les ignorer grâce à un 
fichier nommé *.gitignore*. Pour crée ce fichier on fait la commande :

**Sur Linux :** *touch .gitignore*

**Sur Windows :** *New-Item -Path .gitignore -ItemType File*

Dans ce fichier on met : 

**.class*

On ajoute ce fichier au dépôt git : 

*git add .gitignore*
*git commit -m ".gitignore ajouté"*

Maintenant lorsqu'on fait *git status* on ne voit plus le fichier .class.
Les fichiers .class ont été ignorer lors du *git status*.

On peut compléter le fichier *gitignore* avec ceci :

	# Compiled class file
	*.class
	
	# Package Files 
	*.jar
	*.war
	*.nar
	*.ear
	*.zip
	*.tar.gz
	*.rar

On sélectionne et commit ce fichier : 

*git add .gitignore*
*git commit -m ".gitignore ajouté"*

Ces ajouts permettent de ne pas afficher les fichiers qui ont ces extensions.
