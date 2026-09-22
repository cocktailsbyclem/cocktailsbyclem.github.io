# Cocktails by Clem — site vitrine

Site statique d'une seule page pour **Cocktails by Clem**, barman privé et cocktails
événementiels à Clermont-Ferrand. Aucune étape de build : les fichiers sont servis tels
quels.

```
Cocktail-by-clem/
├── index.html              page unique (toutes les sections)
├── styles.css              système de design complet
├── main.js                 comportements (menu, accordéon, formulaire, carte)
├── mentions-legales.html   ⚠️ champs légaux à compléter
├── confidentialite.html    ⚠️ responsable de traitement à compléter
├── favicon.svg  robots.txt  .nojekyll
├── PRODUCT.md   DESIGN.md  vérité produit et système visuel
└── assets/
    ├── fonts.css + fonts/          Cormorant Garamond + DM Sans, auto-hébergées
    ├── leaves.svg                  ombres de feuillage (motif signature)
    ├── og-image.jpg                image de partage 1200×630
    ├── cocktail-margarita.jpg      photo — hero, prestations, galerie
    ├── clem.jpg                    portrait — section « Qui est Clem ? » et galerie
    ├── evenement-vin-honneur.jpg   photo — prestation « Mariages », tête de galerie
    ├── buffet-evenement.jpg        photo — prestation « Anniversaires », galerie
    ├── buffet-canapes.jpg          photo — prestation « Événements pro », galerie
    ├── pisco-sour-service.jpg      photo — prestation « Atelier cocktail », galerie
    ├── dosage-alcool.jpg           photo — prestation « Barman privé », galerie
    ├── dosage-citron.jpg           photo — prestation « Sur mesure », galerie
    ├── barman-prepare.jpg          photo — section expérience et galerie
    ├── insta-*.jpg                 3 publications, aperçu du feed
    └── cocktails/*.jpg             7 illustrations extraites de votre carte
```

## Mise en ligne

Le site est du statique pur : aucune étape de build, aucun workflow. GitHub Pages le
sert directement depuis la racine de `main`, avec `.nojekyll` pour écarter le
traitement Jekyll.

Réglage, une fois pour toutes : **Settings → Pages → Deploy from a branch →
`main` → `/ (root)`**.

### Déménager vers cocktailsbyclem.github.io

Le sous-domaine d'une adresse `*.github.io` **est le nom du compte GitHub** : il ne se
règle pas. Pour obtenir `cocktailsbyclem.github.io`, il faut donc un compte nommé
`cocktailsbyclem`, et un dépôt nommé exactement `cocktailsbyclem.github.io`.

Le plus sûr est de **transférer** ce dépôt plutôt que de recopier les fichiers :

1. Créer le compte `cocktailsbyclem` sur GitHub. **Il faut une adresse email
   différente** de celle du compte `barriolatino` : GitHub refuse deux comptes sur le
   même email.
2. Depuis ce dépôt : **Settings → Danger Zone → Transfer ownership** vers
   `cocktailsbyclem`.
3. Sur le nouveau compte, renommer le dépôt en **`cocktailsbyclem.github.io`**
   (Settings → Repository name). C'est ce nom précis qui fait du dépôt un « user site »
   servi à la racine.
4. **Settings → Pages → Deploy from a branch → `main` → `/ (root)`**.
5. Fusionner la branche **`adresse-definitive`**, qui remet les URL absolues que
   l'absence d'adresse connue avait obligé à retirer : balise canonique, `og:url`,
   `og:image`, `url` des données structurées, `sitemap.xml` et la ligne `Sitemap` de
   `robots.txt`. Sans elle le site fonctionne, mais le partage sur les réseaux
   n'affiche pas l'image et les moteurs indexent moins bien.

Le site répond alors sur **<https://cocktailsbyclem.github.io/>**, à la racine.

Les chemins internes du site sont tous relatifs : ils fonctionnent aussi bien dans un
sous-dossier qu'à la racine, il n'y a donc rien d'autre à changer.

### Plus tard : un vrai domaine

Un domaine comme `cocktailsbyclem.fr` coûte 10 à 15 € par an et reste le vôtre même en
quittant GitHub. Ajoutez un fichier `CNAME` contenant le domaine à la racine du dépôt,
pointez-le vers GitHub Pages chez votre registrar, puis remplacez
`cocktailsbyclem.github.io` par votre domaine dans les six endroits listés à l'étape 5.

### Modifier le site

```bash
git clone https://github.com/<compte>/<depot>.git
cd <depot>
# … éditez index.html, main.js, styles.css, assets/ …
git add -A && git commit -m "Votre modification" && git push
```

Pages republie tout seul à chaque push.

## Ce qui est renseigné

Toutes les informations du site sont désormais réelles : aucun emplacement
« À COMPLÉTER » ne subsiste. `grep -rn "À COMPLÉTER" .` ne renvoie rien.

Rien n'a été inventé en chemin. Les tarifs (5 € et 6 € par cocktail, 30 € par personne
pour l'atelier) viennent de vos publications et de vos messages ; le Mara Sour et la
Caïpirinha ont été retirés à votre demande plutôt que complétés au jugé ; et les champs
sans objet — statut juridique, SIRET, TVA — ont été supprimés des mentions légales
plutôt que laissés vides.

Deux points restent optionnels, non bloquants :

- **Un nom de domaine.** Le site fonctionne sans, mais certains réseaux sociaux exigent
  une URL absolue pour afficher l'image de partage (voir *Mettre en ligne* ci-dessus).
- **Une fiche Google Business**, si vous voulez afficher des avis un jour
  (voir *Ajouter des avis plus tard*).

## Ajouter vos photos

Les **sept prestations montrent désormais une vraie photo** ; plus aucune illustration ne
tient lieu de visuel d'événement. La galerie compte 9 photos et 2 illustrations, chacune
portant son nom en cartel sous l'image — les cocktails ouvrent la série.

Pour en ajouter : déposez le fichier dans `assets/`, puis ajoutez une entrée au bloc
`.gal` de `index.html`, ou changez un chemin dans `main.js`, tableau `SERVICES`. Format
conseillé : JPEG, 1000 px de large, qualité 80.

**La grille de la galerie se remplit par multiples de trois.** La 1ʳᵉ entrée occupe
2×2 cases et la 2ᵉ 1×2, soit 6 cases ; chaque entrée suivante en occupe une. Avec
11 entrées on tombe juste sur 5 rangées pleines. Pour garder une grille sans trou,
ajoutez ou retirez les photos **trois par trois**.

### Droit à l'image

Deux photos d'événement montrent des invités reconnaissables. Le propriétaire a confirmé
disposer des accords nécessaires à leur publication. Pour toute nouvelle photo
d'événement, la même vérification s'impose avant mise en ligne.

Format conseillé : JPEG, 1200 px de large maximum, qualité 80. Une photo absente
n'affiche jamais d'icône cassée : `main.js` la remplace par un emplacement nommé.

## Ajouter des avis plus tard

La section « Ils ont vécu l'expérience » a été retirée : sans fiche Google Business, elle
n'affichait qu'un emplacement vide et un bouton qui ne menait nulle part. Le jour où des
avis existent, deux chemins :

- **Le plus simple** — créer la fiche **Google Business Profile** (catégorie « Service de
  bar » ou « Traiteur »), puis remettre une section avec un bouton vers sa page d'avis.
- **Les afficher dans la page** — il faut la *Places API* : un projet Google Cloud, la
  « Places API » activée, une clé restreinte au domaine, puis un appel `place/details`
  avec le `place_id` et le champ `reviews`. Google n'en renvoie que cinq et impose
  d'afficher l'attribution et la photo de l'auteur.

La section supprimée existe encore dans l'historique du dépôt où le site a été
développé : `barriolatino/Barrio-latino`, branche `claude/cocktails-clem-website-gyk6cm`,
commit `0a715f8`, fichier `cocktails-by-clem/index.html`.

## Brancher le formulaire

Aujourd'hui le formulaire **n'envoie rien à un serveur** : il valide les champs, compose
un message et l'ouvre dans WhatsApp, où vous gardez la main avant d'envoyer. C'est le
canal que vous utilisez déjà, et cela évite tout stockage de données personnelles.

Pour recevoir en plus une copie par email, sans serveur :

- **Formspree** (gratuit jusqu'à 50 envois/mois) — créez un formulaire, puis dans
  `main.js`, avant l'ouverture de WhatsApp :
  ```js
  fetch('https://formspree.io/f/VOTRE_ID', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json', Accept: 'application/json' },
    body: JSON.stringify(Object.fromEntries(new FormData(form))),
  }).catch(() => {});
  ```
- **Netlify Forms** si vous hébergez sur Netlify plutôt que GitHub Pages : ajoutez
  `netlify` et `name="devis"` sur la balise `<form>`, rien d'autre.

Dans les deux cas, mettez à jour `confidentialite.html` : les données transiteront alors
par un tiers, ce que la page affirme aujourd'hui ne pas être le cas.

## Choix techniques

- **Pas de framework.** Une page vitrine dont le trafic vient du lien en bio Instagram :
  le poids prime. Chargement initial ≈ 340 Ko, dont 167 Ko de polices mises en cache dès
  la deuxième visite.
- **Polices auto-hébergées.** Aucune requête vers Google Fonts, donc aucune adresse IP
  transmise à un tiers et un rendu qui ne dépend pas d'un domaine externe.
- **Carte Google chargée sur clic.** Tant que le visiteur ne la demande pas, Google ne
  reçoit rien et aucun cookie n'est déposé.
- **Illustrations réutilisées.** Les sept verres aquarellés viennent de votre propre
  publication du 25 mars, découpés un par un. Aucune image n'a été générée.
- **Tarifs.** 6 € (signatures) et 5 € (incontournables), à partir de 30 unités, repris de
  votre publication « Mes services ». La page précise qu'ils sont à confirmer au devis.

## Accessibilité et qualité

Vérifié au navigateur en 390, 768, 1280 et 1440 px :

- contraste WCAG AA respecté sur toute la page ;
- aucun texte fonctionnel sous 11 px, aucune cible tactile sous 40 px ;
- aucun débordement horizontal ;
- navigation complète au clavier, focus visible, `Échap` ferme le menu ;
- `prefers-reduced-motion` désactive animations et parallaxe ;
- la page reste entièrement lisible sans JavaScript (seuls l'accordéon, le menu mobile
  et l'envoi du formulaire en dépendent).

## Modifier les contenus

Les listes vivent dans `main.js`, en haut du fichier : `SERVICES`, `SIGNATURES`,
`CLASSIQUES`, `EVENEMENTS`. Ajouter un cocktail = ajouter une ligne au tableau et déposer
l'image correspondante dans `assets/cocktails/`.

Les couleurs et les tailles sont regroupées dans les jetons en tête de `styles.css`
(`:root`). Voir `DESIGN.md` pour le système complet.
