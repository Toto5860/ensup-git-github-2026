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



\### Enquête 2 — Divergence sans conflit



Depuis le commit commun 8ed603a, les deux branches ont avancé :

\- main : f836476, modification de README.md.

\- feature/accessibilite : b7abb34, ajout de accessibilite.md.



La fusion a réussi sans conflit car les fichiers modifiés étaient différents.



Le commit de fusion 096feca possède deux parents :

f836476 et b7abb34.



Contrairement au fast-forward du TP 2, cette fusion crée

un nouveau commit qui relie les deux histoires.



git status confirme que le dépôt est propre.



\### TP 3 — Publication et collecte



PR de collecte :

https://github.com/AbidHamza/ensup-git-github-2026/pull/10



Un fork est ma copie du dépôt sur GitHub.

Un clone est la copie du dépôt sur mon ordinateur.

Une branche représente une ligne de développement dans un dépôt.



git push envoie mes commits locaux vers mon fork sur GitHub.

La PR propose mes modifications au professeur pour relecture.



\### TP 3 — Vérification d’un autre rendu



PR consultée :

https://github.com/AbidHamza/ensup-git-github-2026/pull/7



\- Auteur : yassminnee.

\- Dossier : rendus/yassminnee/.

\- Dernier commit observé : 88e452f.

\- Message : merge: ajouter les indications d accessibilite.



\### Enquête 3 — Diagnostiquer les erreurs



1\. Permission denied

Le compte utilisé n’a pas les droits nécessaires.

Je vérifie que origin pointe vers mon fork avec git remote -v,

puis je vérifie le compte utilisé pour la connexion.



2\. non-fast-forward

Le dépôt distant contient des commits absents de ma branche locale.

git fetch origin récupère les commits sans les fusionner.

Je compare ensuite les histoires avec :

git log --graph --oneline --all



3\. nothing to commit

Je vérifie que le fichier est enregistré, dans le bon dossier,

non ignoré et que la modification n’est pas déjà commitée.

Commande de contrôle : git status.



\### TP 5 — Laboratoire des erreurs



git restore --staged brouillon.txt a retiré le fichier de l’index

sans le supprimer du dossier.



Le commit 7dda2b8 ajoutait le brouillon.

Le revert 820bdbe a annulé cet ajout avec un nouveau commit.

Le commit d’origine reste dans l’historique.



Un conflit est apparu dans horaire.txt :

\- main proposait 09h30, dans le commit 3d3e8ad.

\- feature/horaire proposait 10h00, dans le commit 0edc20c.



Git ne pouvait pas choisir seul l’horaire souhaité.

HEAD désignait main, la branche sur laquelle je lançais la fusion.

Le commanditaire a retenu 09h45.



J’ai remplacé le contenu par « Accueil : 09h45 »,

puis terminé la fusion avec :

git add horaire.txt

git commit -m "fix: convenir de 09h45"



Le commit de fusion 41603b3 a deux parents : 3d3e8ad et 0edc20c.

Le dépôt est propre après la résolution.



Pendant une fusion en cours, git merge --abort permet

d’abandonner la tentative de fusion.



\### Incident distant — Programme modifié en ligne



J’ai modifié programme.md directement sur GitHub :

commit b689e5c, ajout de la visite libre à 12h00.



Sur mon PC, j’ai modifié README.md :

commit 48630df, conseil d’arrivée anticipée.



Le push a été refusé avec le message « fetch first »,

car le dépôt distant contenait un commit absent de ma branche locale.



git fetch origin a récupéré les commits distants et actualisé origin/main.

Cette commande seule ne modifie pas mes fichiers locaux.



J’ai ensuite intégré origin/main avec git merge.

La fusion 6e11903 a réussi sans conflit,

car les modifications concernaient des fichiers différents.



Après git push origin main, j’ai vérifié sur GitHub

que les deux changements étaient présents.

