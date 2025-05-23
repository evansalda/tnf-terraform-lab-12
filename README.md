# CREATION DE L'ENVIRONNEMENT DE PRODUCTION

Vous allez à présent utiliser des workspaces pour gérer les environnements de votre application.

- Supprimez vos environnements de **développement** et de **recette**

- Supprimez (si présents) tout fichier contenant la configuration partielle de votre backend

- Dans le fichier **backend.tf**, configurez votre backend à l'aide des paramètres *bucket*, *key*, *region*, *profile* et **workspace_key_prefix** :

    - La valeur du paramètre **key** sera **terraform.tfstate**
    - La valeur du paramètre **workspace_key_prefix** sera votre digit (exemple : "01")
    - les valeurs des 3 autres paramètres seront les mêmes que depuis le début de ce lab

- La configuration du backend ayant changé, exécutez la commande **terraform init**.

- Créez les 3 workspaces suivants :

    - developpement
    - recette
    - production

- Créez les environnements de **developpement** et **recette** en utilisant les workspaces précédemment créés pour y stocker leur tftate

- Crééz le fichier production.tfvars, en sachant que :

    - Le serveur web est de type t2.large
    - La variable **environnement** a pour valeur **prd**

- Créez l'environnement de **production** en utilisant le workspace du même nom pour stocker le tfstate.

Connectez-vous à la [console AWS](https://645860290752.signin.aws.amazon.com/console), ouvrez le bucket S3 **nuumfactory-backend** et confirmez que terraform a stocké vos tfstates de la manière suivante :

```
<digit>
|
developpement
    |_ terraform.tfstate
recette
    |_ terraform.tfstate
production
    |_ terraform.tfstate
```
