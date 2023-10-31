## Fusionner les branches (merge/rebase)

Lorsque j'ai fini de travailler sur ma branche, je voudrais souvent appliquer mon travail à la branche principale(main);
Cette étape est possible grâce à la **fusion de branches**. Mais il existe plusieurs types de fusion possible:

## Le `merge` : 

le merge crée un nouveau commit de fusion *(merge commit)* qui combine les modifications de la branchce source dans la branche de destination.
Ce commit de fusion à deux parents:  
Un pour la branche source et un pour la branche de destination.

Le merge préserve l'historique des commits de manière linéaire et montre clairement quand et d'où proviennent les modifications.

Il est recommandé pour les colaborations ou plusieurs contributeurs travaillent sur la même branche, car il préserve l'histoire des contributions individuelles.

**Pour réaliser un merge je me place dans ma branche de destination et j'utilise la commande `git merge`**

```bash
# Par exemple, si je veux fusionner ma branche "feature1" avec ma branche "main"

#je me place dans ma branche main qui va recevoir les changements
 git switch main

 # Je fusionne ma branche feature1
 git merge feature1
```

Le merge peut rencontrer deux cas de figure: Avec ou sans fast-forward.

- **Le fast forward (avance rapide):**
Il s'agit d'une méthode de fusion particulière lorsque git veut intégrer les modifications d'une branche dans une autre sans créer de commit de fusion supplémentraire.  
Le fast forward est possible lorsque les conditions suivantes sont remplies.
    - Vous avez une branche de destination et une branche source.
    - La branche source contient des commits que la branche de destination n'a pas encore incorporé.  
    - Les commits de la branche source sont linéaire par rapport à la branche de destination, c'est à dire qu'ils s'ajoutent les uns après les autres dans l'ordre chronologique.

Cela donne l'apparence d'une fusion propre et liénaire dans l'historique des commits. 
Le FF est douvent préféré lorsque cest possible, car il maintient la clarté sans créer de commits de merges supplémentaires . Cependant, il n'est pas toujours applicable, en particulier lorsque des divergences importantes existent entre les branches à fusionner.  
Je peux forcer la non-utilisation d'un FF (par exemple si je veux volontairement un merge commit) en ajoutant l'option `--no-ff`(`git merge nom_branche --no-ff`)

- **Sans fast-forward** 
Lorsque des divergences existent entre les deux branches, je ne peux pas simplement "coller" ma branche source à ma branche de destination. Un commit de fusion *(merge commit)* est donc créé.Ce commit de fusion héritier des deux branches et n'existera qu'au sein de la branche de destination.
C'est dans cette configuration qu'un **conflit** peut apparaitre.
En effet, si une même ligne est modifié dans les deux parents, Git devra faire un choix dans ce qu'il récupère,c'est donc à l'utilisateur de reprendre la main pour faire ce choix et **résoudre** le conflit.

VSCode utilise un outil graphique pour réparer les conflits mais vous pouvez utiliser le `git mergetool` pour régler les conflits en CLI.
Si ces conflits ne sont pas voulus, **je peux annuler mon merge** grâce à l'option `--abort`  
```bash
git merge --abort
```

