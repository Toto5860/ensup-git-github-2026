\# Carnet de bord



Identifiant GitHub : Toto5860



\## Mes preuves



\### TP 1 — Historique et index



Enregistrer un fichier dans l’éditeur modifie sa version sur mon PC.

git add copie son contenu actuel dans l’index.

git commit enregistre le contenu de l’index dans l’historique local.



Après le premier git add, j’ai ajouté « Inscription sur place. ».

Cette phrase n’était pas préparée pour le commit.

git status --short affichait MM README.md.

J’ai refait git add pour inclure les deux phrases.



Mes trois commits :

\- b2e855e : présentation du forum.

\- c3fafda : conditions d’accès.

\- 37e2eff : ajout du .gitignore.



git check-ignore -v .env confirme que .env est ignoré

grâce à la première ligne de mon .gitignore.

