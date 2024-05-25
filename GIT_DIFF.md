# git diff

Des fichiers ont été ajoutés à la branche locale
Le titre principal du readme de la branche locale est "Utilisation de git"
Le titre principal du readme de la branche distante est "Utilisation personnelle de git"

Dans la commande diff, la première branche mentionnée subira les modifications de la branche suivante pour les zones qu'elles ont en commun. 
## application des modifications de la branche locale sur la branche distante
```
git diff origin/main main
```
```
exemple: 
diff --git a/GIT_ADD.md b/GIT_ADD.md
new file mode 100644
index 0000000..0b68f10
--- /dev/null
+++ b/GIT_ADD.md
@@ -0,0 +1 @@
+# git add
diff --git a/GIT_BRANCH.md b/GIT_BRANCH.md
new file mode 100644
index 0000000..1c3f0e7
--- /dev/null
+++ b/GIT_BRANCH.md
@@ -0,0 +1 @@
+# git branch
diff --git a/GIT_CLONE.md b/GIT_CLONE.md
new file mode 100644
index 0000000..ee1de71
--- /dev/null
+++ b/GIT_CLONE.md
@@ -0,0 +1 @@
+# git clone
diff --git a/GIT_COMMIT.md b/GIT_COMMIT.md
new file mode 100644
index 0000000..bbbce0e
--- /dev/null
+++ b/GIT_COMMIT.md
@@ -0,0 +1 @@
+# git commit
diff --git a/GIT_FETCH.md b/GIT_FETCH.md
new file mode 100644
index 0000000..ee1de71
--- /dev/null
+++ b/GIT_FETCH.md
@@ -0,0 +1 @@
+# git clone
diff --git a/GIT_PULL.md b/GIT_PULL.md
new file mode 100644
index 0000000..3c6cb09
--- /dev/null
+++ b/GIT_PULL.md
@@ -0,0 +1,59 @@
+# git pull
+
+Message proposé par git quand divergence
+
+``` 
+astuce: Vous avez des branches divergentes et vous devez spécifier comment
+astuce: les réconcilier. Vous pouvez le faire en lançant une des
+astuce: commandes suivantes avant votre prochain tirage :
+astuce: 
+astuce:   git config pull.rebase false  # fusion
+astuce:   git config pull.rebase true   # rebasage
+astuce:   git config pull.ff only       # avance rapide seulement
+astuce: 
+astuce: Vous pouvez remplacer "git config" par "git config --global" pour que
+astuce: ce soit l'option par défaut pour tous les dépôts. Vous pouvez aussi
+astuce: passer --rebase, --no-rebase ou --ff-only sur la ligne de commande pour
+astuce: remplacer à l'invocation la valeur par défaut configurée.
+``` 
+
+## configuration 
+
+### fusion
+
+```
+git config pull.rebase false
+```
+exemple: 
+
+| commits locaux| commits distants |
+|:--------------|------------------|
+| c45e51fe / Sat May 25 17:34:51 2024|c45e51fe / Sat May 25 17:34:51 2024|
+| b43b0e50  / Sat May 25 18:13:12 2024|e588608d / Sat May 25 18:01:25 2024|
+
+
+resultat: un message d'erreur
+
+erreur : Vos modifications locales aux fichiers suivants seraient écrasées par la fusion : README.md. Veuillez valider ou remiser vos modifications avant la fusion. Abandon. La fusion avec la stratégie ort a échoué.                                  |
+
+
+### rebasage
+
+```
+git config pull.rebase true
+```
+exemple: 
+
+| commits locaux| commits distants |
+|:--------------|------------------|
+| c45e51fe / Sat May 25 17:34:51 2024|c45e51fe / Sat May 25 17:34:51 2024|
+| b43b0e50  / Sat May 25 18:13:12 2024|e588608d / Sat May 25 18:01:25 2024|
+|:--------------|------------------|
+|resultat:     |
+
+
+### avance rapide seulement
+
+```
+git config pull.ff only
+```
\ No newline at end of file
diff --git a/README.md b/README.md
index 086a519..73e1823 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,21 @@
-# Utilisation personnelle de git
+# Utilisation de git
+
+Ce repo correspond à mon terrain d'expérimentation de git. 
+Si vous constatez des erreurs d'usage ou de description faites moi signe!
+
+## Concept
+
+
+
+## Methodologie
+
+### [Git clone](GIT_CLONE.md)
+### [Git fetch](GIT_FETCH.md)
+### [Git pull](GIT_PULL.md)
+### [Git branch](GIT_BRANCH.md)
+### [Git add](GIT_ADD.md)
+### [Git commit](GIT_COMMIT.md)
+### [Git push](GIT_PUSH.md)
+
+### [Git status](GIT_STATUS.md)
+### [Git log](GIT_LOG.md)
\ No newline at end of file

```
## application des modifications de la branche distante sur la branche local
```
git diff main origin/main
```
```
diff --git a/GIT_ADD.md b/GIT_ADD.md
deleted file mode 100644
index 0b68f10..0000000
--- a/GIT_ADD.md
+++ /dev/null
@@ -1 +0,0 @@
-# git add
diff --git a/GIT_BRANCH.md b/GIT_BRANCH.md
deleted file mode 100644
index 1c3f0e7..0000000
--- a/GIT_BRANCH.md
+++ /dev/null
@@ -1 +0,0 @@
-# git branch
diff --git a/GIT_CLONE.md b/GIT_CLONE.md
deleted file mode 100644
index ee1de71..0000000
--- a/GIT_CLONE.md
+++ /dev/null
@@ -1 +0,0 @@
-# git clone
diff --git a/GIT_COMMIT.md b/GIT_COMMIT.md
deleted file mode 100644
index bbbce0e..0000000
--- a/GIT_COMMIT.md
+++ /dev/null
@@ -1 +0,0 @@
-# git commit
diff --git a/GIT_FETCH.md b/GIT_FETCH.md
deleted file mode 100644
index ee1de71..0000000
--- a/GIT_FETCH.md
+++ /dev/null
@@ -1 +0,0 @@
-# git clone
diff --git a/GIT_PULL.md b/GIT_PULL.md
deleted file mode 100644
index 61c0427..0000000
--- a/GIT_PULL.md
+++ /dev/null
@@ -1 +0,0 @@
-# git pull
diff --git a/README.md b/README.md
index c18daae..086a519 100644
--- a/README.md
+++ b/README.md
@@ -1,17 +1 @@
-# Utilisation de git
-
-Ce repo correspond à mon terrain d'expérimentation de git. 
-Si vous constatez des erreurs d'usage ou de description faites moi signe!
-
-## Concept
-
-
-
-## Methodologie
-
-### [Git clone](GIT_CLONE.md)
-### [Git fetch](GIT_FETCH.md)
-### [Git pull](GIT_PULL.md)
-### [Git branch](GIT_BRANCH.md)
-### [Git add](GIT_ADD.md)
-### [Git commit](GIT_COMMIT.md)
\ No newline at end of file
+# Utilisation personnelle de git
```

