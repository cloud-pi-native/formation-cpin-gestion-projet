# Gestion des projets Cloud Pi Native

Vous en êtes à l'étape 1 de la formation CPiN :
1. ➡️ [Gestion des projets CPiN](https://github.com/cloud-pi-native/formation-cpin-gestion-projet)
2. [Application d'exemple pour déploiement sur CPiN](https://github.com/cloud-pi-native/formation-cpin-repo-applicatif/tree/tuto)
3. [Gestion des artefacts sur CPiN](https://github.com/cloud-pi-native/formation-cpin-harbor-trivy)
4. [Chart Helm de démonstration sur CPiN](https://github.com/cloud-pi-native/formation-cpin-deploiement)
5. [Gestion des secrets sur CPiN](https://github.com/cloud-pi-native/formation-cpin-gestion-secret)
6. [Observabilité sur CPiN](https://github.com/cloud-pi-native/formation-cpin-observabilite)

## Connexion à CPiN

▶️ Ouvrez la [console de formation](https://console.dso.formation.numerique-interieur.fr/)

![déconnecté](./img/console-not-connected.png)

▶️ En haut à droite, cliquez sur `Se connecter` et saisissez vos identifiants.

Une fois connecté le menu de gauche suivant apparait :

![connecté](./img/menu-connected.png)

Le menu permet :
 - D'accéder à ses informations de profil en cliquant sur son nom
 - D'accéder à ses projets CPiN
 - De voir le statut des services CPiN de l'environnement
 - D'accéder à la documentation publique.

Le statut des services affiche une page du type météo des services :

![statut des services](./img/status-services.png)

## Création d'un projet

▶️ Depuis le menu `Mes projets`, cliquez sur `+ Créer un nouveau projet`.

![Creation projet](./img/create-project1.png)

▶️ Créez un projet avec les paramètres suivants :
- `Nom du projet` : votre nom ou première lettre du prénom et 3 premières lettres du nom de famille (pdup pour Pierre
Dupont)
- `Description` : Formation CPiN
- `Ressources Prod du projet` et `Ressources Hors Prod du projet` :
  - 8 Go de RAM
  - 4 CPU
  - 0 GPU

▶️ Pour valider la création, cliquez sur le bouton `Commander mon espace projet`.

> [!IMPORTANT]
> Lors d'un déploiement réel sur l'offre CPiN au MI, ces informations doivent correspondre à la demande d'hébergement
> que vous aurez faite, et correspondent aux quotas globaux de ressources de votre projet sur les clusters
> (*prod* et *hors prod*)

Une fois le projet créé (environ 1 minute), le menu suivant apparait. Il permet de gérer les différents éléments d'un
projet :

![menu projet](./img/menu-project.png)

 - **Ressources** : Permet de gérer les environnements et les dépôts de code source.
 - **Services externes** : permet d'accéder à son espace projet sur les différents outils de CPiN : ArgoCD, GitLab,
Grafana, Harbor, etc.
 - **Équipe** : permet de gérer l'équipe qui peut accéder au projet.
 - **Rôles** : permet de définir des rôles aux membres de l'équipe projet.
 - **Journaux** : permet de voir les logs de la console sur les opérations de son projet.
 - **Clusters** : informations sur les clusters disponibles, le DNS et les secrets.
 - **Configuration** : permet d'accéder aux informations de ressources CPU/RAM/GPU du projet.

## Gestion d'équipe

▶️ Allez dans le menu `Équipe` puis ajoutez une personne via son email (travaillez par binôme, demandez à votre voisin
de table).

![ajout membre](./img/add-member.png)

Le bouton `transférer le projet` en fin de page permet de changer le propriétaire du projet et lui transférer tous les
droits.

La modification des membres d'un projet nécessite de reprovisionner le projet. Un message s'affiche pour l'indiquer :

![reprovisionnement nécessaire](./img/repro-msg.png)

▶️ Cliquez sur le bouton `Reprovisionner le projet`

![bouton reprovisionner](./img/repro-menu.png)

Le reprovisionnement permet à la console de ré-appliquer l'ensemble des configurations de votre projet sur la console
et les outils tiers (GitLab, ArgoCD, etc.). Ces opérations sont idempotentes et peuvent donc être rejouées sans impact.

> [!TIP]
> À noter que la console déclenche cette action périodiquement de manière automatique.

## Gestion des rôles

> [!IMPORTANT]
> La console définit 5 rôles génériques : Administrateur, DevOps, Développeur, Sécurité et lecture seule. Ces rôles
> permettent d'attribuer des permissions par défaut dans la console et dans les services externes. La création de rôles
> custom est par contre limitée uniquement à la console et non aux services externes.

![roles prédéfinis](./img/roles-predefinis.png)

Vous pouvez retrouver dans la documentation CPiN le [détail des correspondances RBAC](https://cloud-pi-native.fr/guide/rbac/console-cpin) entre ces rôles et les
services externes.

▶️ Allez sur le menu `Rôles` du projet et retrouvez le rôle permettant d'attribuer les permissions suivantes :
- *Voir les environnements*
- *Gérer les dépôts*
- *Voir les dépôts*

▶️ Dans l'onglet `Membres`, attribuez ce rôle à l'utilisateur que vous avez ajouté à l'étape précédente.

▶️ Cliquez sur le bouton `Reprovisionner le projet`

▶️ Une fois que c'est fait par les 2 voisins, retournez dans la liste de vos projets et consultez le projet de votre
voisin. Vérifiez que vous avez bien les droits correspondants.

## Gestion des ressources

L'onglet `Ressources` permet de gérer :
- les `Environnements` : permet de créer un environnement applicatif, associé à un cluster et un quota d'utilisation de
ressources.
- les `Dépôts` : les dépôts de code correspondent à des dépôts Git externe à CPiN et contenant :
  - Soit du code applicatif dont le but est de construire et déposer une image Docker sur le dépôt d'artefact *Harbor*
  - Soit du code d'infrastructure contenant des manifest et des charts Helm ou Kustomize, permettant de déployer des
applications.
- les `Déploiements` : Permet d'associer un environnement à un ou plusieurs dépôts.

![ressources](./img/ressources.png)

Cette partie sera détaillée dans la suite de la formation.

Bravo, vous avez terminé le premier chapitre de la formation CPiN.

Vous pouvez passer à l'étape 2 : [Application d'exemple pour déploiement sur CPiN](https://github.com/cloud-pi-native/formation-cpin-repo-applicatif/tree/tuto)
