# Terre du Pacifique — Prototype de ferme-gestion 3D

Jeu de gestion type *farming sim* en 3D, jouable directement dans le navigateur,
situé dans un territoire fictif inspiré de la Nouvelle-Calédonie.

Ce dépôt est **open source** : toutes les contributions, suggestions et
retours sont les bienvenus pour améliorer le jeu !

## 🎮 Jouer

Le jeu est un fichier HTML unique et autonome, sans installation requise.

1. Télécharge ou clone ce dépôt.
2. Ouvre [`index.html`](index.html) dans un navigateur récent (Chrome, Firefox, Edge).
   - Si le navigateur bloque les modules JS en local (`file://`), sers le
     dossier avec un petit serveur local, par exemple :
     ```
     npx http-server .
     ```
     puis ouvre l'URL affichée.

## 🗺️ Contenu actuel

**Module 1 — fondations**
- Scène 3D complète (terrain avec relief, ciel dynamique, eau, éclairage
  tropical chaud).
- Trois types de zones : **village** (commerces), **tribus** (habitations),
  **plantations** (cultures).
- Personnage jouable : déplacement clavier (WASD / flèches), caméra
  orbitale suiveuse.
- Architecture de données extensible (`MondeData`) prête à accueillir les
  modules suivants : cultures, économie, population/PNJ, dialogues et
  événements.

**Module 2 — ambiance culturelle, vue aérienne et personnalisation**
- Cycle jour/nuit (ciel, lumière, étoiles).
- Foyers à allumer la nuit à côté des cases (touche **E** à proximité).
- Aire de rassemblement au village : sonner la conque (**E**) déclenche un
  rassemblement communautaire neutre (affaires courantes, conflits de
  voisinage — aucun sujet politique réel n'est traité).
- Aire de coutume dans chaque tribu : lieu scénique statique réservé aux
  futurs événements de vie (mariage, naissance, deuil).
- Vue aérienne basculable (touche **V**) pour observer l'étendue des
  plantations et des tribus près du littoral.
- Personnalisation du personnage (bouton **👕 Tenue** / touche **I**) :
  genre, plusieurs tenues (robes à volants / chemises), teinte de peau —
  silhouettes humanoïdes génériques, sans visage détaillé.
- Musique d'ambiance "vibes Pacifique Sud" **entièrement synthétisée** en
  direct par la Web Audio API (bouton **🎵 Musique**) : aucun fichier audio
  externe, donc aucun risque de droits d'auteur.

Voir l'en-tête du fichier [`index.html`](index.html) pour le détail de
l'architecture et les points d'extension prévus.

## 🤝 Contribuer

Les retours, issues et pull requests sont ouverts à tous. Quelques principes
à respecter pour toute contribution :

- **Aucune personne réelle identifiable** ne doit être représentée (pas de
  reproduction de visages réels).
- Représentation **respectueuse et non caricaturale** des communautés du
  Pacifique (kanak, wallisienne, futunienne, tahitienne, javanaise, etc.),
  sans stéréotypes visuels appuyés.
- Pas d'assets 3D protégés par des droits d'auteur : géométries, matériaux
  et textures doivent être originaux ou libres de droits.
- Le jeu ne traite pas la gravité des conflits réels, les issues dramatiques
  ou des sujets politiques sensibles ; les tensions de gameplay restent
  volontairement légères (ex. conflits de voisinage résolus par le dialogue).

## 📜 Licence

Ce projet est publié sous licence [MIT](LICENSE), afin de permettre la
contribution la plus large possible.
