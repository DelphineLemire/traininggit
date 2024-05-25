# git pull

## sommaire
- [git config pull.rebase false](#git-config-pull.rebase-false)
- [git config pull.rebase true](#git-config-pull.rebase-true)
- [git config pull.ff only](#git-config-pull.ff-only)

## Message proposé par git quand divergence

``` 
astuce: Vous avez des branches divergentes et vous devez spécifier comment
astuce: les réconcilier. Vous pouvez le faire en lançant une des
astuce: commandes suivantes avant votre prochain tirage :
astuce: 
astuce:   git config pull.rebase false  # fusion
astuce:   git config pull.rebase true   # rebasage
astuce:   git config pull.ff only       # avance rapide seulement
astuce: 
astuce: Vous pouvez remplacer "git config" par "git config --global" pour que
astuce: ce soit l'option par défaut pour tous les dépôts. Vous pouvez aussi
astuce: passer --rebase, --no-rebase ou --ff-only sur la ligne de commande pour
astuce: remplacer à l'invocation la valeur par défaut configurée.
``` 

le git pull tente de merger le contenu distant dans la branche locale

## configuration 

### fusion

```
git config pull.rebase false
```
exemple: 

| commits locaux| commits distants |
|:--------------|------------------|
| c45e51fe / Sat May 25 17:34:51 2024|c45e51fe / Sat May 25 17:34:51 2024|
| b43b0e50  / Sat May 25 18:13:12 2024|e588608d / Sat May 25 18:01:25 2024|

resultat: un message d'erreur quand il existe des modifications non indexées. 

```
erreur : Vos modifications locales aux fichiers suivants seraient écrasées par la fusion : README.md. Veuillez valider ou remiser vos modifications avant la fusion. Abandon. La fusion avec la stratégie ort a échoué.                                  |
```
### rebasage

```
git config pull.rebase true
```
exemple: 

| commits locaux| commits distants |
|:--------------|------------------|
| c45e51fe / Sat May 25 17:34:51 2024|c45e51fe / Sat May 25 17:34:51 2024|
| b43b0e50  / Sat May 25 18:13:12 2024|e588608d / Sat May 25 18:01:25 2024|

résultat: resultat: un message d'erreur quand il existe des modifications non indexées. 
erreur : impossible de tirer avec un rebasage : vous avez des modifications non indexées.
erreur : veuillez les valider ou les remiser.

Après Commit de toutes mes modifs en locale, j'ai toujours un message d'erreur à cause du readme
Fusion automatique de README.md
```
CONFLIT (contenu) : Conflit de fusion dans README.md
erreur : impossible d'appliquer b43b0e5... Mise à jour du readme avec différentes commandes
astuce: Resolve all conflicts manually, mark them as resolved with
astuce: "git add/rm <conflicted_files>", then run "git rebase --continue".
astuce: You can instead skip this commit: run "git rebase --skip".
astuce: To abort and get back to the state before "git rebase", run "git rebase --abort".
Impossible d'appliquer b43b0e5... Mise à jour du readme avec différentes commandes
```



git pull --rebase m'a ouvert le fichier readme en conflit avec des zones délimitants les écarts 
j'ai fait évoluer le fichier en le modifiant tel que je le voudrais

le retour de la commande git status est le suivant
``` 
rebasage interactif en cours ; sur e588608
Dernière commande effectuée (1 commande effectuée) :
   pick b43b0e5 Mise à jour du readme avec différentes commandes
Prochaines commandes à effectuer (4 commandes restantes) :
   pick 9120d70 mise à jour de  git pull et ajout de diff
   pick f8486e3 maj de git pull
  (utilisez "git rebase --edit-todo" pour voir et éditer)
Vous êtes en train de rebaser la branche 'main' sur 'e588608'.
  (réglez les conflits puis lancez "git rebase --continue")
  (utilisez "git rebase --skip" pour sauter ce patch)
  (utilisez "git rebase --abort" pour extraire la branche d'origine)

Modifications qui seront validées :
  (utilisez "git restore --staged <fichier>..." pour désindexer)
        nouveau fichier : GIT_ADD.md
        nouveau fichier : GIT_BRANCH.md
        nouveau fichier : GIT_CLONE.md
        nouveau fichier : GIT_COMMIT.md
        nouveau fichier : GIT_FETCH.md
        nouveau fichier : GIT_PULL.md

Chemins non fusionnés :
  (utilisez "git restore --staged <fichier>..." pour désindexer)
  (utilisez "git add <fichier>..." pour marquer comme résolu)
        modifié des deux côtés :  README.md
        
``` 

Après avoir réaliser les commandes requises

git status me dit

```
rebasage interactif en cours ; sur e588608
Dernière commande effectuée (1 commande effectuée) :
   pick b43b0e5 Mise à jour du readme avec différentes commandes
Prochaines commandes à effectuer (4 commandes restantes) :
   pick 9120d70 mise à jour de  git pull et ajout de diff
   pick f8486e3 maj de git pull
  (utilisez "git rebase --edit-todo" pour voir et éditer)
Vous êtes actuellement en train d'éditer un commit pendant un rebasage de la branche 'main' sur 'e588608'.
  (utilisez "git commit --amend" pour corriger le commit actuel)
  (utilisez "git rebase --continue" quand vous avez effectué toutes vos modifications)

rien à valider, la copie de travail est propre

apres plusieurs git rebase --continue + modif des fichiers au fil de l'eau
j'ai le message suivant

```
Sur la branche main
Votre branche est en avance sur 'origin/main' de 5 commits.
  (utilisez "git push" pour publier vos commits locaux)

rien à valider, la copie de travail est propre

```

### avance rapide seulement

```
git config pull.ff only
```
résultat: resultat: un message d'erreur quand il existe des modifications non indexées. 
erreur : impossible de tirer avec un rebasage : vous avez des modifications non indexées.
erreur : veuillez les valider ou les remiser.