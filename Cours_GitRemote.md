## Utiliser Git en remote

Pour connecter un référentiel Git Local à Github, vous devez suivre ces quelques étapes:

1. **Créer un compte Github.** Si vous n'avez pas déjà de compte Github, rendez-vous sur  
https://github.com et créez-en un.

2. **Installer Git** Si GIt n'est pas déjà installé sur votre ordinateur, télécharger-le et installer-le  
à partir du site officiel: htpps://git-scm.com

3. **Configurer Git:** Avant de pouvoir utiliser Git avec GitHub, vous devez configurer votre nom d'utilisateur et votre mail de façon locale. Vous pouvez le faire en exécutant ces commandes sur votre terminal:
 
```bash
git config --global user.name "Votre nom"
git config --global user.email "votre@email.com"
```

4. **Créer un nouveau référant sur Github:** Connectez-vous à votre compte Github, cliquez sur le bouton  
"+" en haut de l'écran pour créer un nouveau référentiel (repository).
Suivez les étapes pour le configurer selon vos besoins.

5. **Clonez le référentiel Github en local:** Pour clonez le reférentiel Github sur votre ordinateur,
utiliser la commande `git clone` en spécifiant l'url du référentiel distant:
```bash
git clone URL_du_referentiel
```

6. **Travaillez sur votre projet localement:** Vous pouvez maintenant travailler sur projet localement 
en ajoutant, modifiant et supprimant des fichiers dan le répertoire cloné.

7. **Validez et publiez vos modifications:** Une fois que vous avez effectué des modifications que vous souhaitez envoyer sur GitHub, vous devez ajouter ces modifications (add), valider les changements (commit) et le pousser vers le repo distant (push), en l'occurence GitHub. Par exemple:
 
```bash
git add .
git commit -m "Description"
git push origin main
```
 
Assurez-vous de remplacer `main` par la branche que vous souhaitez pousser si vous travaillez sur une branche différente.

8. **Consultez votre référentiel sur Github:**
Après avoir poussé vos modifications, vous pouvez vous rendre sur votre référentel Github pour voir les changements en ligne.  
Votre référentiel Git local est maintenant connécté à Github, et vous pouvez continuer à travailler sur votre projet tout en collaborant avec d'autres personnes via Github.

## Envoyer son projet sur Github sans Git Clone 
Pour rattacher un référentiel distant à un dossier lacal sans utiliser `git clone`,
vous pouvez utiliser la commande `git remote` pour ajouter un dépôt distant et `git fetch` pour récupérer **les références** du dépot distant:

1. **Créer un référentiel distant  sur github** 

2.**Dans votre dossier local, initialiser un repo Git**

3.**Ajouter le réferentiel distant en utilisant ``git remote add`:**

```bash
git remote add nom_perso_distant url_du_referentiel
```

remplacez `nom_perso_distant` par le nom que vous  souhaitez (par ex ,origin) et vous récupérer l'url sur Github.

Si vous avez fait une erreur et que vous souhaitez un remote , utiliser la commande `git remote remove nom_du_remote`

4. **Vérifiez que la référentiel distant a été ajouter avec succès**

```bash
git remote -v
```

Cela affichera les URL des référentiels distants que vous avez configurés.

5. **Récupérez les références du dépôt distant `git fetch` :**

```bash
git fetch nom_distant
```

Cela récupérera les informations sur les branches et les tafs du référentiel distant, mais ne fusionnera pas automatiquement les modifications dans votre branche locale.

6. **Ensuite, pour travailler avec les modifications de référentiel distant, vous pouvez créer une branche locale qui suit une branche distante avec `git checkout`**

```bash
git checkout -b nom_de_votre_branche_locale origin/nom_de_la_branche_distante
```

Vous avez maintenant connécté un référentiel distant à votre dossier local sans utiliser `git clone`.

## Le Git Pull 

```bash
git pull branche_distante branche_locale
#Exemple
git pull origin main
```
lors de l'execution d'un `git pull` ces étapes se succède :

1. Git commence par executer une opération ``git fetch` pour récupérer toutes les modifications depuis la branche distante spécifiée. Cela met à jour les références distantes dans votre dépôt local pour refléter l'état actuel du dépôt distant, mais à ce moment là, on ne modifie pas encore sa branche locale.

2. Fusion automatique: Après avoir récupéré les info distantes il s'executent automatiquement une opération de fusion (ou de rebase, si vous lui spécifiez) pour intégrer les modificationsrécupéreez votre branche locale. Si Git détecte des conflits entre les modifications distantes et locales, il vous demandera de les résoudre manuellment avant de terminer la fusion.

3. Finalisation: Une fois que la fusion (ou le rebase) est réussie, votre branche locale est mise à jour avec les dernières modifications de la branche distante.
Votre arborescence de travail reflète désormais l'état actuel de la branche distante.

