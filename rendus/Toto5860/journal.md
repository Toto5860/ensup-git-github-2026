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



\### Enquête 1 — Le fichier disparu du diff



Je pensais que git diff afficherait le nouveau fichier acces.md.

Mais il n’affichait rien, car le fichier était encore non suivi.

git status --short affichait ?? acces.md.



Après git add acces.md, git diff --cached affichait son contenu.



git log --oneline -- acces.md m’a permis de retrouver le commit 901edc3.

git show 901edc3 affichait l’ajout des indications d’accès.



\### TP 2 — Une branche pour une évolution



J’ai créé feature/programme avec git switch -c feature/programme.

J’y ai ajouté programme.md dans le commit 29a628f.



Avant la fusion, programme.md était absent sur main.

Pour intégrer cette évolution, je me suis placé sur main,

puis j’ai lancé git merge feature/programme.



La fusion était un fast-forward : main n’avait pas avancé

depuis la création de la branche. Aucun commit de fusion n’a été créé.



Avant : main pointait vers 44d741d et feature/programme vers 29a628f.

Après : les deux branches pointent vers 29a628f.



ls confirme la présence de programme.md.

git status confirme que le dépôt est propre.

