# le blog du labx

Le blog du labx est généré avec [hugo](http://gohugo.io/)  générateur de site statique ecrit en [GO](https://golang.org/)

#Prise en main de hugo 

## architecture

Un projet hugo est composé de différent fichier et répertoire

### config.toml

contient la configuration globale du site [plus d'info](http://gohugo.io/overview/configuration/)

### data/

peut contenir des fichier au format JSON pour et génerer des pages en fonction de ces données [plus d'info](http://gohugo.io/extras/datafiles/)

### layout/

contient le théme hugo, permet la mise en page du site 

###static/

contient les CSS et les js

###content/

contient les articles du site ecrit en markdown 

#### détail d'un article 

un article est composé d'une entête:
* d'un titre
* auteur
* date
* catégorie, qui permet de classer les articles dans un menu

puis du corps de l'article en mardown 


## Mise à jour du blog mode 1
envoyer sur la mailling list la page rédiger en markdown

## Mise à jour du blog mode 2

### installation de hugo

hugo ne s'installe pas, il suffit de copier un binaire pour pouvoir l'utiliser, [télécharger hugo](https://github.com/spf13/hugo/releases)

### instance local du blog labx 

pour mettre à jour le blog, il faut une instance local

 git clone https://github.com/Labx/blog.git

### Ajout d'un article 

pour ajouter un article créer un fichier .md dans content/post
ne pas oublier la catégorie!!

rédiger le coprs de l'article en markdown

### Test du site 

Hugo fournit un server web de test, pour le lancer faire 

hugo server --watch

hugo server lance le serveur web, l'option watch permet le rafraichissement automatique de la page à chaque modification de la page

### Mise à jour du blog 

* commiter en local les modifications
** git commit -m"ajout de mon article"

* pousser sur le github
** git push 

* si vous avez les droit sudoer du serveur du labx, mettre à jour le depot local 
** cd /var/www/labx_blog/files/blog
** /var/www/labx_blog/files/blog# git pull
* mettre à jour le site 
** /var/www/labx_blog/files/blog# hugo

et voila le site est à jour 
