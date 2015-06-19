Backbone full StackJS
=====================

Dans ce tutoriel nous allons montrer comment développer une application BackboneJS en utilisant exclusivement les outils proposés par la communauté Javascript.

Pour nous allons devoir installer quelques outils.

Installation des prérequis
--------------------------
### Installer Node

Si vous avez déjà node

	brew update
	brew upgrade node
	
sinon

	brew install node
	
### Créer le squelette de l'application

	mkdir bbtuto
	cd bbtuto
	npm init

Installer Backbone et Jquery

	npm install backbone --save
	npm install jquery --save

Création des répertoires principaux de l'application

	mkdir app
	mkdir static

Créer à la racine de l'application, le fichier `index.html` et y ajouter un squelette de page HTML comme celui-ci :
	
	<!DOCTYPE html>	<html lang="en">	<head>		<meta charset="utf-8"/>		<title>PAGE TITLE</title>		<!-- scripts -->	</head>	<body>	</body>	</html>Le répertoire de l'application devrait ressembler à ça : 
	├── app
	├── index.html
	├── node_modules
	│   ├── backbone
	│   └── jquery
	├── package.json
	└── static	Créer le fichier du module principal de l'application `app/main.js` et y ajouter les lignes suivantes : 
	var Backbone = require('backbone');	module.exports = function() { return Backbone };Installer browserify	npm install -g browserify	browserify -r ./app/main:app > static/bundle.js	
Remplacer le commentaire dans index.html par :

	<script src="static/bundle.js"></script>Ouvrir le fichier index.html dans le navigateur et exécuter la commande suivante dans la console Javascript
	require("app")()
Le résultat devrait ressembler à ça :
![consolejs](http://puu.sh/itCQk/349b153e1b.png =600x)
On créé les répertoires qui vont contenir les vues et les modèles/collections
	mkdir app/views	mkdir app/collections	
On créé également le répertoire qui va permettre d'importer les vues et les modèles comme des modules Node	
	mkdir app/node_modules
	cd app/node_modules
	ln -sf ../views
	ln -sf ../collections	
Cette astuce va nous permettre d'appeler nos modules de la manière suivante :

	require('views/movie');	