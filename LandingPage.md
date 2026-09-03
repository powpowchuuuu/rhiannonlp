# Landing page — ce qu'il faut montrer

Notes pour la page de `rhiannonlp`. Écrit depuis l'app, pas depuis l'idée qu'on
s'en fait : chaque point ci-dessous existe et se voit à l'écran.

---

## Les captures livrées

Dans `src/assets/shots/`, servies par `astro:assets`. Prises au simulateur sur
le compte **arestotle** — 1 132 843 écoutes. Données réelles de bout en bout :
pochettes, compteurs personnels, classements, notices, étiquettes.

| Fichier | Appareil | Morceau | Pour |
|---|---|---|---|
| `detail-iphone.png` | iPhone, 1260 × 2736 | *stupid song* — Olivia Rodrigo, **44 écoutes** | le héros |
| `detail-ipad.png` | iPad, 1640 × 2360 | *stupid song* — Olivia Rodrigo, **44 écoutes** | le héros, version large |
| `detail-sabrina-iphone.png` | iPhone | *Espresso* — Sabrina Carpenter, 16 écoutes | seconde section |
| `detail-taylor-iphone.png` | iPhone | *I Knew It, I Knew You* — Taylor Swift | seconde section |
| `journal-iphone.png` | iPhone | **1 132 843 écoutes**, éventail visible | « A journal, not a feed. » |
| `tops-iphone.png` | iPhone | le top de l'année, neuf rangs | le nuage de mots |
| `artist-iphone.png` | iPhone | Fleetwood Mac, 596 écoutes | « A page behind every track. » |

Le composant `Shot.astro` attend `src` ; il rend un bloc vide tant qu'on ne le
lui donne pas. `phone` pour les captures d'iPhone, sans lui pour l'iPad.

### Ce qui cloche encore sur ces captures

**Quatre lignes du journal n'ont pas de pochette.** Les écoutes les plus
récentes du compte sont un remix de Charli xcx, une reprise et deux titres de
Кино : ni Last.fm ni Apple ni Deezer n'en ont de couverture. Ce n'est pas un
défaut de l'app — elle cherche partout et affiche son aplat quand personne n'a
l'image — mais c'est le haut de la capture. Une prise faite après avoir écouté
deux ou trois albums bien pourvus serait plus vendeuse.

**La barre d'état** porte l'heure du simulateur et pas de réseau cellulaire. À
recadrer, ou à reprendre sur un appareil.

**Les thèmes diffèrent d'une capture à l'autre.** La fiche prend la teinte de
sa pochette : *stupid song* est claire, donc sa fiche l'est. Ce n'est pas une
incohérence, c'est une fonctionnalité — mais il faut le savoir avant de
composer la page.

**Le Top est pris sur l'année.** Sur sept jours, ce compte n'a que deux
morceaux, et l'écran affichait « Rien à classer ». L'année donne neuf rangs, et
le sous-titre le dit — « cette année ».

---

## Les captures qui manquent

Demandées par la page, dans l'ordre où elle en a besoin.

### Indispensables — chacune a déjà sa place

1. ~~**`journal-iphone.png`**~~ — **livrée**, avec son éventail : trois écoutes
   d'affilée du même remix de Charli xcx, groupées sous une seule pochette.
   Voir plus haut la réserve sur les couvertures manquantes.

2. **`review-iphone.png`** — la salle d'attente, deux ou trois écoutes en
   attente d'approbation. Pour « Uncertain listens wait for your approval. »
   C'est l'argument que personne d'autre ne tient : il mérite une image.

3. ~~**`tops-iphone.png`**~~ — **livrée.** Neuf rangs avec leurs pochettes, sur
   l'année.

### Reprise du héros

4. ~~**`detail-iphone.png`** et **`detail-ipad.png`**~~ — **reprises.** *stupid
   song* affiche maintenant **44 écoutes** au lieu de zéro, et la page peut dire
   ce qu'elle voulait dire.

### Bienvenues, sans place réservée encore

5. **`widget-iphone.png`** — l'écran d'accueil avec le widget et sa pochette.
   Pour une petite section « Widget », à côté de ListenBrainz.

6. **`listenbrainz-iphone.png`** — les réglages avec ListenBrainz activé, pour
   la même section.

7. ~~**`artist-iphone.png`**~~ — **livrée.** Fleetwood Mac : la photo en
   bandeau, les écoutes personnelles et mondiales, la biographie, les titres
   phares.

### Ce que la capture au simulateur peut rendre, et ce qu'elle ne peut pas

**Faisables sur un compte Last.fm public** — il suffit d'un pseudo, aucune
connexion : le journal, le Top, une page album, une page artiste. Ces écrans ne
lisent que des données publiques.

**Impossibles sans l'appareil de Dereje** :

- La **salle d'attente** n'a de contenu que si le moteur a vraiment relevé des
  écoutes douteuses. On ne peut pas en fabriquer sans mentir sur ce que l'app
  fait. **C'est la seule capture indispensable qui manque encore**, et c'est
  celle qui porte l'argument que personne d'autre ne tient.
- Le **widget** vit sur l'écran d'accueil, et un simulateur ne pose pas de
  widget tout seul.
- Les **réglages avec ListenBrainz activé** demandent un compte ListenBrainz
  connecté.

---

## Les fonctionnalités à mettre en avant

Rangées par force d'argument, pas par ordre d'apparition dans l'app.

### 1. Elle relève ce qui passe dans Musique, toute seule

C'est la raison d'être. Rien à lancer, rien à coller : l'app lit les compteurs
de lecture d'Apple Music et envoie sur Last.fm.

> Déjà écrit sur la page — *« Rhiannon scrobbles what you play in Apple Music
> to Last.fm and ListenBrainz. »* Ne pas y toucher.

### 2. Elle rattrape ce qui s'est écouté app fermée

**C'est l'argument que personne d'autre ne tient.** iOS suspend les apps ; un
scrobbler naïf perd tout ce qui joue pendant ce temps. Rhiannon relève au
réveil, par trois voies distinctes — le compteur de lecture, le suivi en
direct, l'historique du catalogue.

La section `#background` existe déjà. C'est elle qui mérite le plus de place.

### 3. Elle demande avant d'envoyer ce dont elle n'est pas sûre

Une écoute reconstituée dont la date est incertaine ne part pas seule : elle
attend un accord. **Aucun concurrent ne fait ça**, et c'est ce qui distingue un
outil sérieux d'un outil qui remplit un profil de bruit.

À dire en une phrase, sans jargon : *« Uncertain listens wait for your
approval. Nothing goes out that you didn't agree to. »*

### 4. Un journal, pas un flux

Les écoutes rangées par jour, avec les pochettes, dans l'ordre entendu. Les
suites d'un même artiste se regroupent sous un éventail de pochettes.

La section `#journal` le dit déjà bien.

### 5. Une fiche derrière chaque titre

C'est ce que montrent les captures livrées : la pochette pleine largeur, la
page qui prend ses couleurs, les caractéristiques, les compteurs Last.fm, les
étiquettes, la notice, les paroles.

**C'est la plus belle chose de l'app.** Elle mérite le héros, et c'est pour ça
que les captures sont des fiches.

### 6. Gratuite, sans compte à créer, sans rien à débloquer

Pas de version Pro, pas d'abonnement, pas de publicité, pas de pistage. Il faut
seulement un compte Last.fm, qui est gratuit lui aussi.

La section `#free` existe. Elle gagnerait à nommer ce que les autres font
payer.

### 7. ListenBrainz en parallèle

Une case à cocher, et les écoutes partent aux deux. Petit public, mais il
reconnaît immédiatement une app qui le respecte.

### 8. Un widget sur l'écran d'accueil

La dernière écoute envoyée, avec sa pochette. On le touche, la fiche s'ouvre.

---

## Ce qu'il ne faut pas promettre

- **Pas de Spotify.** Rhiannon lit Apple Music, et rien d'autre.
- **Pas de suppression.** L'API de Last.fm n'a pas de méthode pour retirer une
  écoute. C'est d'ailleurs pourquoi la relecture existe.
- **Pas de Mac pour l'instant.** Une version est envisagée, elle n'existe pas.
- **Pas de chiffre d'utilisateurs.** L'app n'est pas sortie.

---

## Deux notes de fond

**L'app est en français, la page en anglais.** Les captures montrent donc une
interface française sur une page anglaise. Soit on assume, soit il faut refaire
les prises avec l'appareil en anglais — l'app suit la langue du système.

**Le crédit AudioScrobbler est obligatoire.** La clause 2.7 de l'accord Last.fm
l'impose à l'app ; la page qui la présente a intérêt à le porter aussi, dans le
pied. `AppSignature` le fait déjà côté app.
