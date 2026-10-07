<!--
  Ce fichier est ÉCRIT PAR LA CI du dépôt privé où vit Race HUD
  (tools/race-hud/depot-public/README.md), à chaque release. Une modification
  faite ici, dans le dépôt public, est écrasée à la release suivante : c'est
  là-bas qu'il se corrige.
-->

# Race HUD

Un outil pour **commenter une course Le Mans Ultimate** : le classement en direct,
qui se bat avec qui, le journal de ce qui vient de se passer (dépassements,
accrochages, tête-à-queue, sorties de piste), la caméra du jeu mise sur une
voiture d'un clic, un moment revu puis le retour au direct. Il sert aussi
l'**habillage d'antenne à OBS** (le classement, le tour du circuit en 3D) et une
**régie** à mettre en dock, et se pilote depuis un **Stream Deck** avec son
plugin.

Il tourne **sur la machine qui fait tourner le jeu**, ne parle qu'au jeu, à OBS,
au navigateur et au Stream Deck de cette machine, et **n'envoie rien nulle
part** — sauf une question anonyme à ce dépôt-ci : au lancement puis toutes les
six heures, il demande à GitHub quelle est la dernière release, pour afficher un
bandeau quand une version plus récente existe. Rien de ta machine n'y est joint ;
l'option `--no-update-check` la coupe.

## Télécharger

**[Page des releases → la dernière](https://github.com/terry-afk/vincecosa-race-hud/releases/latest)**,
sans compte GitHub :

- `race-hud-x.y.z.exe` — l'application, un seul fichier, pour Windows 64 bits ;
- `race-hud-streamdeck-x.y.z.streamDeckPlugin` — seulement si tu as un Stream Deck.

Ce dépôt ne contient **que les releases** et ce README : le dépôt où l'outil se
développe n'est pas public. Les archives « Source code » que GitHub attache
d'office à chaque release ne contiennent que ce dépôt-ci — ce README.

## Installer, une fois

1. **Range l'exe dans un dossier fixe** (par exemple `C:\RaceHUD\`) **et
   renomme-le `race-hud.exe`.** C'est à côté de lui que le HUD garde ta mise en
   page, tes logos corrigés et tes enregistrements ; lancé depuis un autre
   dossier — Téléchargements, par exemple —, il repart de la mise en page d'usine.
2. **Épingle le fichier, jamais la fenêtre ouverte** : clic droit sur
   `race-hud.exe` → épingler à la barre des tâches, ou un raccourci sur le bureau.
   L'exe se décompresse dans un dossier temporaire au lancement, et une épingle
   prise sur la fenêtre risque de viser ce dossier-là.
3. **Premier lancement** : l'exe n'est pas signé, donc Windows affiche « Windows a
   protégé votre ordinateur » → _Informations complémentaires_ → _Exécuter quand
   même_. À chaque nouvel exe téléchargé, c'est soit ça au premier lancement, soit
   avant : clic droit sur le fichier → _Propriétés_ → cocher _Débloquer_ → _OK_.
   Le démarrage peut prendre quelques secondes sans rien montrer : attends la
   fenêtre, ne double-clique pas une seconde fois.
4. **Dans Le Mans Ultimate** : _Paramètres → Gameplay → Enable Plugins → ON_, puis
   **redémarre le jeu complètement**. Sans ça le HUD ne trouve pas le jeu, et
   aucun accrochage n'arrive au journal.

## Avant chaque course

Lance le jeu, charge la séance, puis `race-hud.exe`. En haut à droite, le HUD dit
**« jeu connecté »**. **Fermer la fenêtre arrête tout**, sources OBS comprises : à
la fin de la course seulement.

Les adresses se copient depuis le pied de page du HUD, port compris — ne les
tape pas :

- **habillage** : OBS, source _Navigateur web_ 1920 × 1080, au-dessus de la
  capture du jeu ; décoche « Désactiver la source quand elle n'est pas visible » ;
- **tour 3D** : OBS, _Navigateur web_ 1920 × 1080, dans sa propre scène, avec
  **« Contrôler l'audio via OBS »** coché — sans ça, sa musique part au stream
  par l'audio du bureau dès que la source est visible quelque part, aperçu
  compris ;
- **régie** : OBS, _Docks → Docks Internet personnalisés…_ ;
- **mise en page** : un navigateur ordinaire, jamais OBS.

## Le Stream Deck

Il faut le logiciel Stream Deck **7.1 ou plus récent** (au premier lancement du
plugin, laisse-lui Internet : il peut avoir à télécharger ce dont le plugin a
besoin). **Double-clic** sur le `.streamDeckPlugin` : une catégorie **« Race HUD »**
apparaît dans la liste des actions — **aucune touche ne se pose toute seule**.
Glisse « Revoir le départ » et « Arrêter la série » sur deux touches, et
« Commande du HUD » pour le reste (une colonne du classement, l'écran de
classement, l'anneau des pédales). **Garde l'icône par défaut** : une icône
choisie dans le logiciel Stream Deck cache l'état du HUD sur la touche.

## Mettre à jour

Quand une version plus récente est publiée, **un bandeau vert le dit** sous
l'en-tête du HUD ; « Voir la release » ouvre sa page dans ton navigateur,
« Plus tard » le cache jusqu'au prochain lancement. Sinon, la
[page des releases](https://github.com/terry-afk/vincecosa-race-hud/releases).
Le HUD n'installe rien lui-même : ferme le HUD, télécharge le nouvel exe, renomme-le `race-hud.exe` et **remplace**
l'ancien dans ton dossier : ton épingle, ta mise en page et tes logos suivent. Le
plugin Stream Deck ne se réinstalle pas à chaque version ; si une touche dit
« plugin périmé », double-clic sur celui de la dernière release.

## Marques et licences

- Race HUD est un outil de communauté, **ni édité ni approuvé** par les éditeurs
  de Le Mans Ultimate.
- Les logos de constructeurs sont des **fichiers du jeu, embarqués dans l'exe** ;
  les marques appartiennent à leurs titulaires et ne servent ici qu'à
  **identifier le constructeur d'une voiture**, exactement comme le jeu le fait.
- La musique du tour 3D est rendue avec la banque de sons **MuseScore General**
  (licence MIT, certaines parties CC0 ou domaine public) ; sa notice de licence est
  livrée dans l'exe, à côté de la musique.
- La police d'affichage est **Saira Condensed** (Copyright 2016 The Saira Project
  Authors, SIL Open Font License 1.1) ; sa notice est dans les pages du HUD.
- L'application est construite sur **Electron** (licence MIT) et embarque
  **Chromium** ; leurs licences (`LICENSE.electron.txt`, `LICENSES.chromium.html`)
  sont dans `%TEMP%\race-hud`, le dossier où l'exe se décompresse — présent tant
  que le HUD tourne, effacé à sa fermeture.
