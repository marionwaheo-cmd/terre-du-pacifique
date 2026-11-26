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

**Module 3 — cultures & économie**
- Planter une culture sur une parcelle vide (**E**, puis choisir dans le
  panneau : igname, pastèque, tomate, taro, manioc, café).
- Croissance datée sur l'horloge de jeu, avec un visuel qui évolue
  (pousse → croissance → maturité).
- Récolter (**E** sur une parcelle mûre) : alimente l'inventaire.
- Vendre la récolte à la coopérative agricole du village (**E**).
- Acheter de l'engrais à l'épicerie (**E**) pour accélérer la croissance
  d'une parcelle en cours.
- Argent, engrais et inventaire affichés dans le HUD.

**Module 3bis — semis par peinture**
- Barre de graines en bas à gauche : on sélectionne une graine puis on
  clique/glisse directement sur les parcelles affichées à l'écran pour
  semer en série (façon jeux de gestion mobiles), sans repasser par un
  menu à chaque parcelle.

**Module 4 — population**
- Les emplacements d'habitants sont maintenant de vrais PNJ (silhouette
  humanoïde) qui errent doucement autour de leur case.
- Vendre sa récolte alimente le revenu des tribus, qui fait grandir leur
  population chaque jour de jeu.
- Une fois la population totale suffisante, l'école du village devient
  constructible (**E**, en pièces).
- Chaque habitant peut être salué (**E**) — texte neutre, sans dialogue.

**Module 5 — dialogues & conflits de voisinage**
- De temps en temps, un petit différend anodin survient entre deux
  habitants d'une même tribu (clôture, animaux égarés…), signalé par une
  icône ❗ flottante.
- S'en approcher et appuyer sur **E** ouvre un dialogue à choix : le
  régler soi-même, ou faire intervenir le chef de tribu, le maire ou la
  police.
- Chaque résolution est **toujours amicale** : aucune gravité, aucune
  issue dramatique, aucun sujet politique — conformément au cahier des
  charges du projet.
- Un différend qui traîne plus de 45 secondes (icône ❗→⚠️) coûte un peu de
  revenu communautaire à la tribu (perte de main-d'œuvre pendant la
  médiation) — choisi à la place d'une mise en scène policière
  (arrestation, emprisonnement), jugée trop dramatique et sensible.
- La conque a une forme plus réaliste (corps spiralé, aile évasée, canal
  pointu). La sonner déclenche une vraie séquence : le joueur se fige, la
  porte à sa bouche, un son synthétisé imite le souffle, puis l'annonce
  donne un bilan (ventes, différends réglés) et une prochaine demande.

**Module 6 — sauvegarde**
- Progression sauvegardée automatiquement dans le navigateur
  (`localStorage`, rien n'est envoyé où que ce soit) : argent, inventaire,
  engrais, cultures en cours, population/revenu des tribus, école
  construite, position et apparence du personnage, horloge de jeu.
- Sauvegarde toutes les 20 secondes, à chaque action clé, et à la
  fermeture de l'onglet. Rechargée automatiquement à l'ouverture.
- Bouton 🗑️ (en haut à droite) pour effacer la sauvegarde et recommencer
  une nouvelle partie.

**Module 7 — écran d'accueil & effets sonores**
- Écran d'accueil au lancement : "Continuer l'aventure" (si une
  sauvegarde existe) ou "Nouvelle partie", avec un rappel des contrôles.
- Petits retours sonores synthétisés (jamais de fichier audio, donc
  aucun droit d'auteur) pour planter, récolter, encaisser et signaler
  une erreur.

**Module 8 — contrôles tactiles (mobile/tablette)**
- Sur appareil tactile : un joystick virtuel (bas gauche) pour se
  déplacer, et un bouton rond "E" (bas droite) pour interagir.
- La caméra reste pilotable au tactile nativement (un doigt = orbite,
  deux doigts = zoom), sans conflit avec le joystick.

**Module 9 — faune sauvage & chasse de subsistance**
- Des sangliers rôdent la nuit autour des tribus, puis se dispersent à
  l'aube.
- Une armurerie au village vend un fusil de chasse (achat unique).
- La nuit, s'approcher d'un sanglier permet de le chasser (**E**) si on
  est armé.
- La viande crue obtenue doit être grillée sur un foyer allumé (**E**),
  puis offerte à une tribu (**E**, près d'un habitant) pour renforcer son
  revenu communautaire.
- Le sanglier est une espèce commune en Nouvelle-Calédonie, chassée
  légalement toute l'année car elle endommage les cultures : aucune
  dramatisation, simple activité de subsistance.

**Module 10 — multijoueur pair-à-pair**
- Bouton **👥 Multi** : créer un salon (code généré automatiquement, ex.
  `TARO-5996`) ou rejoindre celui d'un proche.
- Connexion directe entre navigateurs via WebRTC ([Trystero](https://github.com/dmotz/trystero)),
  sans aucun serveur à héberger ni compte à créer — juste un code à partager.
- Chaque joueur voit l'autre se déplacer en temps réel (même silhouette que
  le personnage, avec son apparence).
- Actions partagées : planter, récolter, vendre une récolte et construire
  l'école sont répercutées chez l'autre joueur.
- Pensé pour un tout petit groupe (ex. soi-même et son/sa partenaire) ; la
  faune, les différends de voisinage et la progression des tribus restent
  simulés localement par chaque client pour l'instant.

**Module 11 — décor enrichi**
- Végétation très dense (arbres, bananiers, cocotiers, fougères arborescentes,
  buissons, arbres fruitiers, framboisiers et pieds d'hibiscus fleuris en
  couleurs), pour un paysage quasiment sans terrain vide — seuls les chemins
  restent dégagés.
- Petites mares d'eau douce près de chaque tribu, avec une berge herbeuse.
- Une quinzaine de chevaux en liberté, dispersés sur toute la carte, qui
  errent paisiblement de jour comme de nuit (décoratif, non chassable).
- Des torches s'allument et s'éteignent automatiquement autour des
  habitations avec le cycle jour/nuit, sans action du joueur.

**Module 12 — chasse saisonnière réglementée**
- Basé sur une recherche réelle de la réglementation néo-calédonienne (voir
  sources ci-dessous) : le **cerf rusa** est une espèce régulée, chassable
  toute l'année ; le **notou** et la **roussette** sont des espèces
  **protégées**, légalement chassables seulement durant de courtes périodes
  (les week-ends d'avril, selon les provinces).
- Dans le jeu, cette « saison » revient périodiquement dans le calendrier
  accéléré : hors saison, l'interaction de chasse est simplement
  indisponible pour le notou et la roussette (aucune mise en scène
  répressive). Le cerf, lui, reste chassable en tout temps.
- ⚠️ Les dates exactes varient selon les provinces et les années — ce qui
  est implémenté est une approximation stylisée à but ludique, pas un
  conseil juridique. Sources consultées : [guide de chasse, Province Sud](https://www.province-sud.nc/sites/default/files/guidechasse-psud-2022_web.pdf),
  [communiqué chasse roussettes/notous, Province Nord](https://province-nord.nc/sites/default/files/communique-ouverte-chasse-roussettes-inter-province-nouvelle-caledonie-2025.pdf),
  [Les Nouvelles Calédoniennes](https://www.lnc.nc/article/roussettes-et-notous-la-chasse-est-ouverte-jusqu-au-26-avril).

**Module 13 — pêche et quai**
- Une canne à pêche s'achète à l'épicerie du village.
- De petits pontons de pêche sont installés au bord de chaque mare, et un
  quai en mer (avec un bateau décoratif amarré, immatriculé « NC ») permet de
  pêcher en mer pour de meilleures prises.
- La canne apparaît en main pendant la courte animation de pêche.
- Le bateau n'est pour l'instant pas pilotable : premier pas visuel avant un
  futur module de navigation.

**Module 14 — objectifs du village ("scénarios")**
- Deux objectifs actifs en permanence, tirés d'un éventail varié : **vendre**
  une quantité d'une culture précise, **chasser** des cerfs, **pêcher**, ou
  **régler un différend** de voisinage.
- Récompense immédiate dès qu'un objectif est rempli (pas besoin d'attendre
  la conque) : message, pièces, et incrément de **renommée**.
- Tous les 5 objectifs réussis, un bonus supplémentaire tombe — la renommée
  est sauvegardée d'une session à l'autre, pour donner un vrai cap à long
  terme en plus de la récompense immédiate de chaque objectif.
- La conque fait toujours le bilan (objectifs réussis depuis le dernier
  appel) et tire deux nouveaux objectifs.
- Les objectifs "vendre" ne portent que sur des cultures réellement
  achetées par la coopérative (corrige un bug où la demande du village
  pouvait porter sur une culture invendable).

**Module 15/16 — sécurité du monde (eau)**
- Ni les animaux (chevaux, sangliers, cerfs, notous, roussettes) ni les
  arbres/torches ne peuvent plus apparaître dans une mare ou en mer : l'eau
  reste de l'eau. Le joueur peut s'approcher du bord (et se tenir sur un
  ponton de pêche) mais ne peut plus marcher dans l'eau elle-même.

**Optimisation (module 17)**
- Les géométries des fougères, cocotiers et hibiscus ont été fortement
  simplifiées (bien moins d'objets 3D par plante, même silhouette) et la
  densité globale légèrement réduite, pour que le décor enrichi reste fluide
  sur mobile et sur des machines modestes.

## 📱 Mobile
Le jeu reste jouable au doigt (joystick virtuel + bouton E, module 8) ; la
barre de boutons du haut (Multi/Musique/Tenue/réinitialiser) est désormais
en disposition flexible et se réduit sur petit écran pour ne jamais déborder.

## 🔧 Améliorations récentes

- **Déplacement relatif à la caméra** : avancer (W) déplace désormais le
  personnage dans la direction où regarde la caméra, comme dans la plupart
  des jeux à caméra orbitale (corrige la prise en main).
- **Cultures accélérées** : la croissance se compte maintenant en minutes
  réelles (1,5 à 7 min selon la culture) plutôt qu'en jours de jeu, pour
  rester satisfaisante à jouer.
- **Germes dispersés** : chaque parcelle plantée affiche 10 à 14 petits
  plants répartis sur toute sa surface, plutôt qu'une seule plante au
  centre.
- **Sanglier redessiné** : silhouette plus ronde et stylisée (inspirée
  d'un style "dessin", formes originales).
- **Personnages plus ronds et expressifs** : tête agrandie, visage simple
  (yeux, sourire) et coiffure (style + couleur libres). Chaque habitant
  varie ces traits individuellement pour représenter la diversité réelle
  du Pacifique, sans visage-type assigné à une communauté précise.
- **Silhouettes distinctes par culture** : igname (tuteurs + feuilles
  grimpantes), taro (grandes feuilles basses) et café (buisson + baies
  rouges à maturité) ont chacun leur propre apparence, inspirée de photos
  de référence. Les autres cultures gardent le visuel générique.

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
