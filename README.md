# Anaxago test

Appli dispo en test sur: <a href="https://anaxago-app.vercel.app/">https://anaxago-app.vercel.app/</a>

> Utilisation volontaire de Vue cli dans une version 2 de vue.

> Rien empêchait l'utilisation de Vue 3 mais comme le projet est en V2 je suis volontairement parti sur cette version.

> De même pour babel, eslint, webpack, je ne m'attarde pas sur la conf de ce projet (ajout d'alias également).

> Utilisation de la lib. Vuetify pour coller au plus à l'app actuelle.

> Style en scss.

> Avec plus de temps j'aurai ajouté des tests via cypress ou encore une partie storybook pour le testing de composant génériques (dossier shared) , ajouté typescript pour le typage des données et VueX pour la gestion des datas des forms également

> Au niveau des convention comme c'est très variable d'un projet à l'autre, j'ai utilisé celle mise en place sur mon dernier projet.

> Pas de gros travail fait pour le côté responsive, l'interface s'adapte aux tailles standard tablette, un peu plus de travail aurait été nécessaire pour aller jusqu'aux petites résolutions.

> Le modèle des données n'est pas top, j'ai fait un semblant de mock, pour le reste j'ai mis des chaines dans le code. Dans l'idéal il aurait fallu ajouter pour chacun un couple id / value pour éviter des tests sur des libellés.

Questions :

<ul><li>Contraintes navigteurs particulières ? </li><li> Gestion des langues ?</li>

## Mise en route du projet

```bash
# Récupérer le repository
git clone https://github.com/Dooxe77/anaxago-app.git

# Placez vous dans le dossier anaxago-test
cd anaxago/

# Installation des dépendences
npm i

# Lancement avec le hot reloading (mode dév)
npm run serve

#Lien de test: http://localhost:8080/

```
