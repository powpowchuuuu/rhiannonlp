# Landing page — ce qu'il faut montrer

Notes pour la page de `rhiannonlp`. Écrit depuis l'app, pas depuis l'idée qu'on
s'en fait : chaque point ci-dessous existe et se voit à l'écran.

---

## Les captures livrées

Dans `public/shots/`. Prises au simulateur sur un vrai compte Last.fm, données
réelles — pochettes, compteurs d'auditeurs, notices, étiquettes.

| Fichier | Appareil | Morceau | Pour |
|---|---|---|---|
| `detail-iphone.png` | iPhone, 1260 × 2736 | *stupid song* — Olivia Rodrigo | le héros |
| `detail-ipad.png` | iPad, 1640 × 2360 | *stupid song* — Olivia Rodrigo | le héros, version large |
| `detail-taylor-iphone.png` | iPhone | *I Knew It, I Knew You* — Taylor Swift | seconde section |
| `detail-sabrina-iphone.png` | iPhone | *House Tour* — Sabrina Carpenter | seconde section |
| `journal-iphone.png` | iPhone | — | « A journal, not a feed. » |
| `tops-iphone.png` | iPhone | — | le nuage de mots |
| `artist-iphone.png` | iPhone | Fleetwood Mac | « A page behind every track. » |

Le composant `Shot.astro` attend `src` ; il rend un bloc vide tant qu'on ne le
lui donne pas. `phone` pour les captures d'iPhone, sans lui pour l'iPad.

### Ce qui cloche encore sur ces captures

**« JAMAIS ÉCOUTÉ · 0 ».** Le compte qui a servi aux prises n'a jamais joué ces
morceaux. Sur un héros, c'est le pire chiffre possible — la page vante un
journal d'écoutes et montre un compteur à zéro. À refaire depuis un compte qui
a réellement écouté le morceau choisi.

**La barre d'état** porte l'heure du simulateur et pas de réseau cellulaire. À
recadrer, ou à reprendre sur un appareil.

**L'iPad est en thème clair**, l'iPhone en sombre : la fiche prend la teinte de
sa pochette, et celle d'Olivia Rodrigo est claire. Ce n'est pas un défaut —
c'est une fonctionnalité de l'app — mais il faut le savoir avant de composer la
page, sous peine de croire à une incohérence.

---

## Les captures qui manquent

Demandées par la page, dans l'ordre où elle en a besoin.

### Indispensables — chacune a déjà sa place

1. ~~**`journal-iphone.png`**~~ — **livrée.** Une journée bien remplie, des
   pochettes variées, les en-têtes de journée. **Il y manque l'éventail** : le
   compte de test n'a pas de suite d'un même artiste dans ses écoutes récentes,
   et on ne peut pas en fabriquer une. À reprendre depuis un compte qui a
   enchaîné trois titres du même artiste.

2. **`review-iphone.png`** — la salle d'attente, deux ou trois écoutes en
   attente d'approbation. Pour « Uncertain listens wait for your approval. »
   C'est l'argument que personne d'autre ne tient : il mérite une image.

3. ~~**`tops-iphone.png`**~~ — **livrée.** Neuf rangs avec leurs pochettes.
   Sur « depuis toujours » et non sur la semaine : le compte de test n'a rien
   écouté ces sept derniers jours, et la page s'affichait « Rien à classer ».

### Reprise du héros

4. **`detail-iphone.png`** et **`detail-ipad.png`** — les mêmes fiches, mais
   depuis un compte qui a réellement écouté le morceau, pour que le compteur ne
   soit pas à zéro. **Un titre beaucoup écouté, avec un chiffre qui parle, vaut
   mieux que la plus belle des pochettes.**

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
  fait.
- Le **widget** vit sur l'écran d'accueil, et un simulateur ne pose pas de
  widget tout seul.
- Le **compteur d'écoutes** d'une fiche est celui du compte connecté. Un compte
  de test rendra toujours zéro.

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
