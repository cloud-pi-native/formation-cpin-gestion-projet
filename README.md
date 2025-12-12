# Gestion des projets CPiN

## Connexion à CPiN

Ouvrir la console sur l'URL de [formation](https://console.formation.cpin.numerique-interieur.com/) 

![login](./img/console-not-connected.png)

En haut à droite cliquer sur se connecter et saisir ses identifiants.

Une fois connecté le menu gauche suivant apparait :

![login](./img/menu-connected.png)

Le menu permet :
 - D'accéder à ses informaitons de profil en cliquant sur son nom
 - D'accéder à ses projets CPiN
 - De voir le status des services CPiN de l'environnement
 - D'accéder à la documentation publique.

Le status des services affiche une page du type météo des services :
![status des services](./img/status-services.png) 


## Création d'un projet


Depuis le menu ```Mes projets``` cliquez sur ```+ Créer un noueau projet```

Commencez par donner un nom au projet, pour la formation nommez le projet par votre nom ou première lettre du prenom et 3 première lettre du nom de famille exemple pdup pour Pierre Dupont

et donnez une description

![Creation projet](./img/create-project1.png) 

Ensuite donnez les ressources maximales pour les environnements de production et hors production.

Pour les besoins de la formation :
 - 4 CPU
 - 8 Go de RAM
 - 0 GPU

Lors d'un déploiement réel sur l'offre CPiN au MI ces informations doivent correspondre à la demande d'hébergement et correspondent aux quotas global de ressources pour le projet sur les clusters (prod et hors prod)

Terminez la saisie par le bouton ```Commander mon espace projet```

Une fois le projet créé, le menu suivant apparait qui permet de gérer les différents éléments d'un projet :

![menu projet](./img/menu-project.png)

 - Ressources : Permet de gérer les environnements et les dépots de code source
 - Services externes : permet d'accéder à son espace projet sur les différents outils de CPiN : ArgoCD, Gitlab, Grafana, Harbor, etc.
 - Equipe : permet de gérer l'équipe qui peut accéder au projet
 - Role : permet de définir des rôles aux membres de l'équipe projet
 - Journaux : permet de voir les logs de la console sur les opérations de son projet
 - Configuration : permet d'accéder aux informations de ressources CPU/RAM/GPU du projet

 ## Gestion équipe

Aller dans le menu ```Equipe``` puis ajouter une personne (par binome, demandez à votre voisin de table). L'ajout sefait par adresse mail :
![ajout membre](./img/add-member.png)

puis cliquez sur Ajouter

Le bouton transférer le projet en fin de page permet de changer le propriétaire du projet à quelqu'un d'autre (tous les droits)

La modification des des membres d'un projet nécessite de reprovisionner le projet et un message s'affiche pour l'indiquer :
![repro](./img/repro-msg.png)

Pour cela cliquez sur le bouton ```Reprovionner le projet```

![repro](./img/repro-menu.png)

Le reprovisonnement permet à la console de ré-appliquer à l'ensemble des configuration du projets sur la console et les outils tiers (Gitlab, ArgoCD, etc.). Ces opérations sont idempotents et peuvent donc être repassé sans impact. A noter que la console déclenche periodiquement cette action.

## Gestion des rôles

Aller sur le menu ```Rôle``` du projet et créer un rôle permettant uniquement de voir les dépots et de voir et gérer les environnements et nommez le role ```read-repo-manage-env```  et cliquez sur enregistrer.

![gestion role](./img/gestion-role.png)

Dans l'onglet Membres, ajouter le voisin que vous avez ajouté à l'étape précédente.

Une fois que c'est fait par les 2 voisins, retournez dans la liste de vos projets et allez consulter le projet de votre voisin et vérifiez que vous avez bien les droits correspondants.

## Gestion des ressources

L'onglet ```Ressources``` permet de gérer :

 - Des environnements : permet de créer un environnement applicatif, associé à un cluster et un quota d'utilisation de ressources. 
 - Des dépots de codes : les dépots de code correspondent à des repos git externe à CPiN et contenant : 
   - Soit du code applicatif dont le but est de construire et déposer une image Docker sur le repo d'artefact Harbor
   - Soit du code d'infrastructure et contenant des manifest, charts Helm ou Kustomize permettant de déployer des applications.

![ressources](./img/resources.png)

Cette partie sera détaillée dans la suite de la formation.